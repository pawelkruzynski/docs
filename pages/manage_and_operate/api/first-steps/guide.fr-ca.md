---
title: 'Premiers pas avec les API OVHcloud'
excerpt: 'Découvrez comment utiliser les API OVHcloud'
updated: 2024-06-07
---

## Objectif

Les API disponibles sur [https://ca.api.ovh.com/](https://ca.api.ovh.com/){.external} vous permettent d'acheter, gérer, mettre à jour et configurer des produits OVHcloud sans utiliser une interface graphique comme l'espace client.

**Découvrez comment utiliser les API OVHcloud mais aussi comment les coupler avec vos applications**

## Prérequis

- Disposer d'un compte OVHcloud actif et connaître ses identifiants.
- Être sur la page web des [API OVHcloud](https://ca.api.ovh.com/){.external}.

## En pratique

> [!warning]
>
> OVHcloud met à votre disposition des services dont la configuration, la gestion et la responsabilité vous incombent. Il vous revient de ce fait d'en assurer le bon fonctionnement.
> 
> Nous mettons à votre disposition ce guide afin de vous accompagner au mieux sur des tâches courantes. Néanmoins, nous vous recommandons de faire appel à un [prestataire spécialisé](https://partner.ovhcloud.com/fr-ca/directory/) et/ou de contacter l'éditeur du service si vous éprouvez des difficultés. En effet, nous ne serons pas en mesure de vous fournir une assistance. Plus d'informations dans la section « [Aller plus loin ](#gofurther) » de ce guide.
> 

### Utilisation simple

#### Se connecter aux API OVHcloud

Sur la page des [API OVHcloud](https://ca.api.ovh.com/), cliquez sur `Explore the OVH API`{.action} pour afficher la liste des API. 

Pour utiliser les API sur vos produits, vous devez vous connecter sur ce site grâce à vos identifiants OVHcloud.

- Cliquez sur `Authentication`{.action} en haut à gauche.
- Cliquez ensuite sur `Login with OVHcloud SSO`{.action}.
- Saisissez vos identifiants OVHcloud.
- Cliquez sur le bouton `Authorize`{.action} pour autoriser les appels aux API depuis ce site.

![API](images/login.png){.thumbnail} 

> [!primary]
>
> Si votre compte OVHcloud est protégé par une [double authentification](/pages/account_and_service_management/account_information/secure-ovhcloud-account-with-2fa),  vous devrez également saisir le code généré par SMS ou application OTP ou clé U2F.
>

#### Explorer les produits disponibles sur les API

Vous retrouvez dans le menu de gauche la liste des produits OVHcloud qui peuvent être gérés via des API. Cette liste est classée par ordre alphabétique.

![API](images/api-list.png){.thumbnail} 

Pour afficher, par exemple, les API liées aux noms de domaine, cliquez sur **/domain** dans la liste.

Après avoir cliqué sur le produit, la liste des API de ce dernier s'affiche en dessous. 

![API](images/api-displayed.png){.thumbnail} 

Vous disposez également d'un sélecteur à gauche de la liste des produits qui permet de choisir entre les branches **/v1** et **/v2** de l'API. Si vous n'êtes pas familier avec le principe des branches d'API, vous pouvez consulter [la documentation suivante à propos de l'API v2](/pages/manage_and_operate/api/apiv2).

#### Exécuter une API

Il existe 4 types d'API disponibles qui emploient ce que l'on appelle des méthodes HTTP : 

**GET** 

La methode GET a pour but de récupérer les données d'une ressource.

Par exemple, pour récupérer la liste de vos noms de domaine, utilisez l'API suivante :

> [!api]
>
> @api {v1} /domain GET /domain
>

**POST**

La méthode POST est utilisée pour envoyer des données supplémentaires vers la ressource. 

Par exemple, pour ajouter un enregistrement à votre zone DNS, utilisez l'API suivante :

> [!api]
>
> @api {v1} /domain POST /domain/zone/{zoneName}/record
>

**PUT**

La méthode PUT sert à remplacer les données actuelles de la ressource par les données de la requête.

Par exemple, si vous vous êtes trompé dans un enregistrement de votre zone DNS, utilisez l'API suivante :

> [!api]
>
> @api {v1} /domain PUT /domain/zone/{zoneName}/record/{id}
>

**DELETE**

La méthode DELETE est utilisée pour supprimer la ressource appelée.

Par exemple, si vous ne souhaitez finalement pas conserver l'enregistrement DNS que vous avez ajouté à votre zone DNS, utilisez l'API suivante :

> [!api]
>
> @api {v1} /domain DELETE /domain/zone/{zoneName}/record/{id}
>

##### Paramètres de l'API

Après avoir cliqué sur l'API de votre choix, la section **Request** permet d'attribuer les variables relatives à son application.
 
Par exemple, pour l'ajout d'un enregistrement TXT dans votre zone DNS, vous obtiendrez les paramètres suivants :
 	
![API](images/parameters.png){.thumbnail} 
 
Une fois les paramètres définis, vous pouvez lancer l'API en cliquant sur `TRY`{.action}.

L'onglet `Response` alors affiché vous donnera le rapport d'éxécution de l'API.

![API](images/result.png){.thumbnail} 

Les onglets `PHP` et `Python` contiennent les éléments à ajouter dans votre script en fonction du language utilisé.

### Utilisation avancée : coupler les API OVHcloud avec une application

#### Créer les clés de votre application

Toute application souhaitant communiquer avec l'API OVHcloud doit être déclarée à l'avance.

Pour ce faire, cliquez sur le lien suivant : [https://ca.api.ovh.com/createToken/](https://ca.api.ovh.com/createToken/){.external}.

Renseignez votre identifiant client, votre mot de passe et le nom de votre application. Le nom sera utile plus tard si vous voulez autoriser d'autres personnes à l'utiliser.

Vous pouvez également ajouter une description de l'application ainsi qu'une temporalité. 

Le champ `Rights` vous permet de restreindre l'usage de l'application à certaines API. 
<br> Afin d'autoriser toutes les API OVHcloud pour une méthode HTTP, renseignez une étoile `*` dans le champ, comme dans l'exemple ci-dessous où la méthode GET est autorisée pour toutes les API :

![API keys](images/api-keys.png){.thumbnail} 

Après avoir cliqué sur `Create keys`{.action}, Vous obtiendrez trois clés :

- la clé d'application, appelée **AK**. Par exemple :

```console
7kbG7Bk7S9Nt7ZSV
```

- votre clé d'application secrète, à ne pas divulguer, appelée **AS**. Par exemple :

```console
EXEgWIz07P0HYwtQDs7cNIqCiQaWSuHF
```

- une « **consumer key** » secrète, à ne pas divulguer, appelée **CK**. Par exemple :

```console
MtSwSrPpNjqfVSmJhLbPyr2i45lSwPU1
```

Dans le cas présent, la clé **CK** est attachée à votre compte.

Le token **CK** peut être utilisé pour de la délégation de droits. Consultez le guide suivant pour en savoir plus : [Comment gérer le compte d'un client OVHcloud via les API](/pages/manage_and_operate/api/api_right_delegation) (guide en anglais).

#### Première utilisation de l'API

Une fois vos trois clés obtenues (**AK**, **AS**, **CK**), vous pouvez signer les demandes d'API. La signature est calculée ainsi :

```console
"$1$" + SHA1_HEX(AS+"+"+CK+"+"+METHOD+"+"+QUERY+"+"+BODY+"+"+TSTAMP)
```

Afin de simplifier le développement de vos applications, OVHcloud vous fournit des wrappers API dans plusieurs langages.
Les utiliser vous permettra de ne pas vous préoccuper du calcul de la signature et de vous concentrer sur le développement de votre application.

- *Go* : <https://github.com/ovh/go-ovh>
- *Perl* : <https://github.com/ovh/perl-ovh>
- *Python* : <https://github.com/ovh/python-ovh>
- *PHP* : <https://github.com/ovh/php-ovh>
- *Node.js* : <https://github.com/ovh/node-ovh>
- *C#* : <https://github.com/ovh/csharp-ovh>

Voici un exemple d'utilisation de la section `/me` qui permet de gérer votre compte OVHcloud :

```python
import ovh

# Instantiate. Visit https://ca.api.ovh.com/createToken/?GET=/me
# to get your credentials
client = ovh.Client(
    endpoint='ovh-eu',
    application_key='<application key>',
    application_secret='<application secret>',
    consumer_key='<consumer key>',
)

# Print nice welcome message
print("Welcome", client.get('/me')['firstname'])
```

#### Lister et révoquer vos clés

Il n'y a actuellement aucune option dans l'espace client pour lister et révoquer vos clés. Pour cela, il est possible d’utiliser le portail API :

- Listez les ID des clés avec l'appel suivant :

> [!api]
>
> @api {v1} /me GET /me/api/application
>

- Obtenez les détails d'une clé avec l'appel suivant :

> [!api]
>
> @api {v1} /me GET /me/api/application/{applicationId}
>

- Révoquez une clé avec l'appel suivant :

> [!api]
>
> @api {v1} /me DELETE /me/api/application/{applicationId}
>

## Aller plus loin <a name="gofurther"></a>

[Gestion d'un nom de domaine via les API OVHcloud](/pages/web_cloud/domains/api_domain_intro)

[Comment gérer le compte d'un client OVHcloud via les API](/pages/manage_and_operate/api/api_right_delegation) (guide en anglais)

Échangez avec notre [communauté d'utilisateurs](/links/community).
