---
title: "Object Storage - Gestion de l'immuabilité des objets avec Object Lock (WORM)"
excerpt: "Object Lock est une fonctionnalité qui vous permet de stocker des objets en utilisant un modèle WORM (Write Once, Read Many)"
updated: 2023-08-09
---

## Objectif

Object Lock est une fonctionnalité qui vous permet de stocker des objets en utilisant un modèle WORM (**W**rite **O**nce, **R**ead **M**any) et peut être utilisé dans des scénarios où il est impératif que les données ne soient pas modifiées ou supprimées après avoir été écrites.

**Ce guide explique comment gérer l'Object Lock.**

## Concept

Object Lock fournit deux façons de gérer la rétention des objets. La première étant les périodes de rétention et la seconde le Legal hold.

### Comment fonctionne Object Lock ?

Pour comprendre le fonctionnement de Object Lock, nous devons d'abord comprendre comment la suppression d'objets et le *versioning* fonctionnent ensemble. Lorsqu'une opération de suppression d'objet est effectuée sur un objet dans un bucket sur lequel le *versioning* est activé, elle ne supprime pas l'objet de manière permanente, mais crée un marqueur de suppression sur l'objet. Ce marqueur de suppression devient la version la plus récente et la version actuelle de l'objet avec un nouvel ID de version.

Un marqueur de suppression possède les propriétés suivantes :

- Une clé et un ID de version comme tout autre objet.
- Il n'a pas de données associées, donc il ne récupère rien d'une requête GET (vous obtenez une erreur 404).
- Par défaut, il n'est plus affiché dans l'espace client.
- La seule opération que vous pouvez utiliser sur un marqueur de suppression est DELETE, et seul le propriétaire du bucket peut effectuer une telle demande.

Pour supprimer définitivement un objet, vous devez spécifier l'ID de version dans votre demande de suppression d'objet :

```bash
aws s3api delete-object --bucket my-bucket --key an-object --version-id 123456huijw0
```

La fonction Object Lock empêche les objets, pendant une durée fixe (mode de rétention) ou indéfiniment (conservation légale), d'être :

- supprimés même si vous spécifiez le *version id* (vous obtenez une erreur « Access Denied ») ;
- écrasés par le *versioning*.

> [!primary]
>
> Pour utiliser Object Lock, le *versioning* doit être activé.
>

### Périodes de rétention

Une période de rétention spécifie une période de temps fixe pendant laquelle un objet reste verrouillé. Pendant cette période, votre objet est protégé et ne peut pas être écrasé ou supprimé. Vous pouvez appliquer une période de rétention en nombre de jours ou en nombre d'années, avec un minimum d'un jour et aucune limite maximale.

Lorsque vous définissez une période de rétention pour vos objets ou vos buckets, vous pouvez choisir le mode de rétention que vous souhaitez appliquer à vos objets. Vous pouvez choisir soit le mode *Governance*, soit le mode *Compliance* pour vos objets.

#### Mode Governance

Vous devriez utiliser le mode *Governance* si vous souhaitez empêcher la suppression des objets par la plupart des utilisateurs au cours d'une période de rétention prédéfinie, tout en permettant à certains utilisateurs disposant d'autorisations spéciales de modifier les paramètres de rétention ou de supprimer les objets. Les utilisateurs disposant de l'autorisation `s3:BypassGovernanceRetention` peuvent remplacer ou supprimer les paramètres de rétention en mode *Governance*.

#### Mode Compliance

Vous devriez utiliser le mode *Compliance* si vous avez l'obligation de stocker des données conformes.
Lorsque ce mode est activé, la version d'un objet ne peut être écrasée ou supprimée par aucun utilisateur. Si ce mode est configuré pour un objet, son mode de rétention ne peut pas être modifié et sa période de rétention ne peut pas être raccourcie.

> [!primary]
>
> Vous ne devez utiliser le mode *Compliance* que si vous ne voulez jamais qu'un utilisateur, y compris l'utilisateur administrateur, puisse supprimer les objets pendant une période de rétention prédéfinie.
>

### Legal hold

La fonction Legal hold est conçue pour toutes les situations où vous n'êtes pas sûr de la durée pendant laquelle vous voulez que vos objets restent immuables. La fonction Legal hold est un interrupteur ON/OFF qui peut être appliqué à chaque objet, indépendamment de la configuration du verrou, de la rétention de l'objet ou de l'âge de l'objet. Elle peut être appliquée aux objets qui sont verrouillés.

La fonction Legal hold offre la même protection qu'une période de rétention, mais elle n'a pas de date d'expiration. Au lieu de cela, la fonction Legal hold reste en place jusqu'à ce que vous la supprimiez explicitement.

## Prérequis

- Connaître vos informations d'identification S3 (access_key et secret_access_key)
- Avoir installé et configuré aws cli

Consultez notre guide « [Débuter avec S3 Object Storage](/pages/storage_and_backup/object_storage/s3_getting_started_with_object_storage) » pour plus de détails.

## En pratique

> [!primary]
>
> Tous les exemples suivants utiliseront aws cli.
>
> Pour en savoir plus sur aws cli, suivez ce [guide](/pages/storage_and_backup/object_storage/s3_getting_started_with_object_storage).
>

### Permissions

| Nom | Description
|:--|:--|
| `s3:GetObjectRetention` | Permet à l'utilisateur de visualiser le mode et la période de rétention d'un objet.
| `s3:PutObjectRetention` | Permet à l'utilisateur de placer une configuration de rétention sur un objet |
| `s3:GetObjectLegalHold` | Permet à l'utilisateur de visualiser la configuration Legal hold d'un objet.
| `s3:PutObjectLegalHold` | Permet à un utilisateur de placer une configuration Legal hold sur un objet.
| `s3:GetBucketObjectLockConfiguration` | Permet à l'utilisateur de visualiser la configuration de rétention par défaut d'un bucket.
| `s3:PutBucketObjectLockConfiguration` | Permet à l'utilisateur de placer une configuration de rétention sur un bucket spécifique |
| `s3:BypassGovernanceRetention` | Permet à l'utilisateur de contourner le mode *Governance*. |

*Lisez ce [guide](/pages/storage_and_backup/object_storage/s3_identity_and_access_management) pour en savoir plus sur la gestion des identités et des accès.*

### Configuration d'Object Lock

Pour utiliser Object Lock, vous devez créer un bucket qui supporte la fonctionnalité avec le flag `--object-lock-enabled-for-bucket`. Si un bucket est créé sans ce flag, il ne pourra pas être ajouté ultérieurement.

> [!primary]
>
> La commande suivante n'applique pas l'Object Lock aux objets du bucket, elle active seulement la fonctionnalité.
>

```bash
aws s3api create-bucket \
  --bucket object-lock-bucket \
  --object-lock-enabled-for-bucket
```

> [!primary]
>
> Cette action active également le versioning du bucket.
>

### Configuration d'Object Lock sur un bucket

Object Lock vous permet de définir une période de rétention sur un bucket spécifique. Une fois définie, la règle spécifiée est appliquée par défaut à chaque nouvel objet placé dans le bucket spécifié.

```bash
aws s3api put-object-lock-configuration \
    --bucket object-lock-bucket \
    --object-lock-configuration '{ "ObjectLockEnabled" : "Enabled", "Rule" : { "DefaultRetention" : { "Mode" : "GOVERNANCE", "Days" : 60 }}}'
```

Pour afficher la configuration Object Lock d'un bucket, exécutez :

```bash
aws s3api get-object-lock-configuration \
   --bucket object-lock-bucket
```

Le résultat devrait ressembler à ceci :

```json
{
  "ObjectLockConfiguration" : {
    "ObjectLockEnabled" : "Enabled",
    "Rule" : {
      "DefaultRetention" : {
        "Mode" : "GOVERNANCE",
        "Days" : 60
      }
    }
  }
}
```

### Comment configurer une période de rétention sur un objet

Pour appliquer une configuration de rétention sur un objet :

```bash
aws s3api put-object-retention \
       --bucket object-lock-bucket \
       --key test.txt \
       --retention '{"Mode" : "COMPLIANCE", "RetainUntilDate" :
"2023-01-01T12:00:00.00Z" }'
```

> [!primary]
>
> Le format de la date est standard iso8601 : `Y-m-dTH:M:S.%3fZ`
>

Pour afficher la configuration de rétention d'un objet, exécutez :

```bash
aws s3api get-object-retention \
   --bucket object-lock-bucket \
   --key test.txt
```

Le résultat devrait ressembler à ceci :

```json
{
  "Rétention" : {
  "Mode" : "COMPLIANCE",
  "RetainUntilDate" : "2023-01-01T12:00:00Z"
  }
}
```

#### Contournement du mode Governance

> [!primary]
>
> Si vous avez la permission `s3:BypassGovernanceRetention`, vous pouvez effectuer des opérations sur des versions d'objet verrouillées en mode *Governance* comme si elles n'étaient pas protégées.
>

Pour contourner le mode *Governance*, vous devez indiquer explicitement dans votre requête que vous souhaitez contourner ce mode. Pour ce faire, incluez l'en-tête `--bypass-governance-retention` avec votre requête:

```bash
aws s3api delete-object \
  --bucket object-lock-bucket \
  --key test.txt \
  --bypass-governance-retention
```

### Comment configurer Object Lock Legal hold sur un objet

Pour appliquer une configuration Legal hold à l'objet spécifié :

```bash
aws s3api put-object-legal-hold \
  --bucket object-lock-bucket \
  --key test.txt \
  --legal-hold Status=ON
```

Pour afficher la configuration Legal hold d'un objet, exécutez :

```bash
aws s3api get-object-legal-hold \
  --bucket object-lock-bucket \
  --key test.txt
```

Le résultat devrait ressembler à ceci :

```json
{
  "LegalHold": {
    "Status": "ON"
  }
}
```

## Aller plus loin

Si vous avez besoin d'une formation ou d'une assistance technique pour la mise en oeuvre de nos solutions, contactez votre commercial ou cliquez sur [ce lien](/links/professional-services) pour obtenir un devis et demander une analyse personnalisée de votre projet à nos experts de l’équipe Professional Services.

Échangez avec notre [communauté d'utilisateurs](/links/community).

**\*** : S3 est une marque déposée appartenant à Amazon Technologies, Inc. Les services de OVHcloud ne sont pas sponsorisés, approuvés, ou affiliés de quelque manière que ce soit.
