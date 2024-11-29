---
title: "Commander un projet Public Cloud via l'API OVHcloud"
excerpt: "Découvrez comment commander votre projet Public Cloud avec l'API OVHcloud"
updated: 2020-12-09
---

## Objectif

La création d'un projet est la première étape du déploiement d'[instances Public Cloud](https://www.ovhcloud.com/fr-ca/public-cloud/).

**Ce guide explique comment commander un projet Public Cloud via l'APIv6 OVHcloud.**

## Prérequis

- Disposer d'identifiants OVHcloud valides
- Disposer d'un [mode de paiement](/pages/account_and_service_management/managing_billing_payments_and_services/manage-payment-methods) valide et enregistré dans votre compte OVHcloud
- Être familiarisé avec le [fonctionnement de l'APIv6 OVHcloud](/pages/manage_and_operate/api/first-steps).

## En pratique

Connectez-vous à l'[interface API OVHcloud](https://ca.api.ovh.com/) et suivez les étapes ci-dessous.

### Étape 1 : construire le panier

La première étape d'une commande consiste à créer un « panier » (cart). Vous pourrez ensuite y ajouter un projet Public cloud.

#### Créer le panier

Utilisez cet appel pour créer le panier :

> [!api]
>
> @api {v1} /order POST /order/cart
>

Veillez à bien choisir votre filiale d'API OVHcloud. Notez le numéro de panier (« cartId ») dans la réponse ; il sera nécessaire d'identifier ce panier.

Vous devez ensuite ajouter un projet Public Cloud en tant qu'article. Utilisez cet appel avec votre « cartId » pour vérifier la disponibilité du service :

> [!api]
>
> @api {v1} /order GET /order/cart/{cartId}/cloud
>

Dans la réponse, vous pouvez vérifier les paramètres relatifs à un projet Public Cloud :

>
>**code_plan** : « project.2018 »
>
>**productName** : « Projet Public Cloud »
>

#### Ajouter un projet au panier

Utilisez cet appel pour ajouter l'article à votre panier :

> [!api]
>
> @api {v1} /order POST /order/cart/{cartId}/cloud
>

Les informations suivantes, extraites au cours des étapes précédentes, doivent être fournies :

|Champ|Valeur|
|---|---|
|cartId|*ID de votre panier*|
|duration|P1M|
|planCode|project.2018|
|priceMode|default|
|quantity|1|

La réponse inclura un « itemId » qui peut être utilisé (avec le « cartId ») pour identifier l'article du panier :

> [!api]
>
> @api {v1} /order GET /order/cart/{cartId}/item/{itemId}
>

Vous pouvez vérifier la liste des paramètres de configuration disponibles pour cet article avec cet appel :

> [!api]
>
> @api {v1} /order GET /order/cart/{cartId}/item/{itemId}/requiredConfiguration
>

Utilisez le endpoint suivant pour nommer votre projet (`label: « description »`) :

> [!api]
>
> @api {v1} /order POST /order/cart/{cartId}/item/{itemId}/configuration
>

|Champ|Valeur|
|---|---|
|cartId|*ID de votre panier*|
|itemId|*ID de l'article*|
|label|description|
|value|*Nom de votre projet*|

Pour appliquer un bon d'achat, utilisez le même appel avec le label « voucher », etc.

Les réponses incluent un « configurationId » qui peut être utilisé (avec « cartId » et « itemId ») pour récupérer la configuration (GET) ou la supprimer, par exemple :

> [!api]
>
> @api {v1} /order DELETE /order/cart/{cartId}/item/{itemId}/configuration/{configurationId}
>

### Étape 2 : valider le panier

Vous pouvez vérifier le contenu de votre panier à l'aide de « cartId » :

> [!api]
>
> @api {v1} /order GET /order/cart/{cartId}/checkout
>

L'appel suivant vous permet de créer un lien vers votre commande. Il faut d'abord cocher la case correspondante afin de renoncer au droit de rétractation.

> [!api]
>
> @api {v1} /order POST /order/cart/{cartId}/checkout
>

## Aller plus loin

Échangez avec notre [communauté d'utilisateurs](/links/community).