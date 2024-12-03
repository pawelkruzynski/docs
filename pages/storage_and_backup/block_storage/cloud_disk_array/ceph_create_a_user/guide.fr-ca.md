---
title: Création d'utilisateurs
excerpt: Ce qui vous présente comment créer un nouvel utilisateur.
updated: 2018-03-26
---

## Utiliser l'interface web

> [!primary]
>
> L'utilisation d'une interface web est le moyen le plus simple de créer un utilisateur.
>

Tout d'abord, connectez-vous au [l’espace client](https://ca.ovh.com/manager/dedicated/#/configuration){.external} et dans la rubrique Plates-formes et services vous trouverez le service Ceph.

Dans l'onglet "Utilisateurs", vous trouverez la liste des **utilisateurs**. Aucun utilisateur n'est créé par défaut (sauf *admin* que vous ne pouvez pas utiliser et qui est caché).

![Ceph users](images/create_a_user_1.png){.thumbnail}

Entrez un nom d'utilisateur.

> [!warning]
>
> Votre nom d'utilisateur doit comporter au moins trois caractères.
>

![Ceph user creation](images/create_a_user_2.png){.thumbnail}

Après la création de l'utilisateur, vous revenez au gestionnaire. Vous pouvez voir que le statut du cluster a changé parce que l'utilisateur est en cours de création.

![Ceph user creation](images/create_a_user_3.png){.thumbnail}

## Utiliser l'API

> [!api]
>
> @api {v1} /dedicated/ceph POST /dedicated/ceph/{serviceName}/user
>
serviceName est le fsid de votre cluster.

Vous pouvez vérifier la création des utilisateurs en dressant une liste des utilisateurs.

```bash
GET /dedicated/ceph/98d166d8-7c88-47b7-9cb6-63acd5a59c15/user
[
  {
    mdsCaps: ""
    monCaps: "allow r"
    serviceName: "98d166d8-7c88-47b7-9cb6-63acd5a59c15"
    name: "myuser"
    osdCaps: "allow class-read object_prefix rbd_children"
    key: "AQA9KpdXoBrDNhAAFCM7m/XOtmWh3LMSNlHVqw=="
  }
]
```

## Aller plus loin

Rendez-vous sur notre chaîne Discord dédiée : <https://discord.gg/ovhcloud>. Posez des questions, fournissez des commentaires et interagissez directement avec l'équipe qui construit nos services de stockage et de sauvegarde.

Si vous avez besoin d'une formation ou d'une assistance technique pour la mise en oeuvre de nos solutions, contactez votre commercial ou cliquez sur [ce lien](https://www.ovhcloud.com/fr-ca/professional-services/) pour obtenir un devis et demander une analyse personnalisée de votre projet à nos experts de l’équipe Professional Services.

Échangez avec notre [communauté d'utilisateurs](/links/community).
