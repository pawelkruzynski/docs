---
title: "Hébergement web - Activer l’hébergement gratuit 100M"
excerpt: "Découvrez comment activer votre hébergement gratuit 100M"
updated: 2024-12-05
---

## Objectif

Avec [l'hébergement gratuit 100M](/links/web/domains-free-hosting){.external}, OVHcloud vous offre un hébergement Web de 100 Mo et un compte e-mail disposant de 5 Go de stockage. 
Ce guide vous présente comment activer cette offre sur votre [nom de domaine](/links/web/domains){.external}.

> [!warning]
>
> Cet hébergement gratuit de 100 Mo convient pour une simple page Web de présentation, il **n'inclut pas de base de données**.
> Il convient également si vous n'avez pas besoin de plusieurs adresses e-mail de type "MX plan". 
> Si vous souhaitez mettre en place un site Web comprenant plusieurs pages et nécessitant une base de données, tel qu'un CMS (WordPress, Joomla!, PrestaShop, Drupal, etc.), nous vous invitons à commander directement l'une de [nos offres d'hébergement Web](/links/web/hosting) depuis notre site ou votre [espace client OVHcloud](/links/manager).
>

**Découvrez comment activer votre hébergement gratuit 100M**

## Prérequis

- Disposer d'un [nom de domaine](/links/web/domains) dans votre [espace client OVHcloud](/links/manager), détaché de tout hébergement Web et sans aucun [MX Plan](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/email_generalities) associé.
- Être connecté à votre [espace client OVHcloud](/links/manager).

## En pratique

Pour activer votre hébergement gratuit 100M, cliquez sur les onglets ci-dessous pour afficher successivement chacune des 5 étapes.

> [!tabs]
> **Etape 1**
>>
>> Connectez-vous à votre [espace client OVHcloud](/links/manager).
>>
>> ![enable 100m](/pages/assets/screens/control_panel/login.png){.thumbnail}
>>
> **Etape 2**
>>
>> Rendez-vous dans la partie `Web Cloud`{.action}.
>>
>> ![enable 100m](/pages/assets/screens/control_panel/product-selection/web-cloud.png){.thumbnail}
>>
> **Etape 3**
>>
>> Cliquez sur le menu déroulant `Noms de domaine`{.action}, puis choisissez le nom de domaine concerné.
>>
>> ![enable 100m](/pages/assets/screens/control_panel/product-selection/web-cloud/domain-names.png){.thumbnail}
>>
> **Etape 4**
>>
>> Dans le cadre **Informations générales** vous trouverez la mention **Hébergement Web et e-mail gratuit**. Cliquez sur le bouton `...`{.action} à droite puis sur `Activer`{.action}.
>>
>> ![enable 100m](/pages/assets/screens/control_panel/product-selection/web-cloud/domain-dns/general-information/enable-100m.png){.thumbnail}
>>
> **Etape 5**
>>
>> La fenêtre d'activation s'affiche. La section **1** vous rappelle l'offre et son tarif, cliquez sur `Suivant`{.action}.
>> Pour la section **2**, choisissez les modifications à apporter sur votre zone DNS :
>>
>> ![activate 100m](/pages/assets/screens/control_panel/product-selection/web-cloud/order/order-100m-step-2.png){.thumbnail}
>>
>> > [!warning]
>> >
>> > Si vous cochez l'une des deux cases `Entrée DNS A` et `Entrée DNS MX` ou les deux, cela écrasera la configuration initialement mise en place dans la zone DNS de votre nom de domaine.
>> >
>> > Si votre zone DNS n'est pas gérée dans votre [espace client OVHcloud](/links/manager), vous devrez effectuer les modifications manuellement dans votre zone DNS externe.
>> >
>> > Pour plus de détails, consultez notre guide sur [l'édition d'une zone DNS OVHcloud](/pages/web_cloud/domains/dns_zone_edit).
>>
>> | Choix                                       	| Description                                                                                                               							|
>> |--------------------------------------------	|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
>> | Entrée DNS A                         	| Le nom de domaine pointera vers l'adresse IP de l'hébergement gratuit 100M.                                               								|
>> | Entrée DNS MX 	| Les serveurs e-mail (`mx1.mail.ovh.net`, `mx2.mail.ovh.net`, `mx3.mail.ovh.net`, etc.) d'OVHcloud seront appliqués au nom de domaine. 	|
>>
>> La section **3** vous rappelle la tarification de l'offre. 
>>
>> Dans la section **4**, prennez connaissance des contrats, puis valider votre commande pour terminer la demande d'activation de votre hébergement gratuit 100M.

> [!primary]
>
> Si votre projet est amené à évoluer rapidement vers un hébergement disposant d'une base de données, d'un espace de stockage plus important ou davantage d'adresses e-mail, vous pourrez basculer directement et uniquement de l'hébergement gratuit 100M vers une offre d'hébergement **Perso** depuis votre [espace client OVHcloud](/links/manager).
>
> Une bascule vers l'offre **Pro** ou **Performance** nécessite de passer préalablement de l'offre d'hébergement gratuit 100M à l'offre **Perso**.
>
> Vous pouvez aussi choisir de supprimer l'offre gratuite en prenant soin de récupérer au préalable vos données d'hébergement et le contenu de votre adresse mail.
>
> Pour plus de détails, consultez nos [offres d'hébergement](/links/web/hosting).

Une fois votre commande validée, un e-mail vous sera transmis avec les informations de [connexion FTP](/pages/web_cloud/web_hosting/ftp_connection) à votre hébergement gratuit 100M.

Consultez le guide de [création d'un compte E-mail MX Plan](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/email_creation) pour profiter de l'adresse e-mail incluse avec votre hébergement gratuit 100M.

## Aller plus loin

[Se connecter à l’espace de stockage de son hébergement Web](/pages/web_cloud/web_hosting/ftp_connection)

[Créer une adresse e-mail avec son offre MX Plan](/pages/web_cloud/email_and_collaborative_solutions/mx_plan/email_creation)

[Gérer un certificat SSL sur son hébergement web](/pages/web_cloud/web_hosting/ssl_on_webhosting)

Pour des prestations spécialisées (référencement, développement, etc), contactez les [partenaires OVHcloud](/links/partner).

Si vous souhaitez bénéficier d'une assistance à l'usage et à la configuration de vos solutions OVHcloud, nous vous proposons de consulter nos différentes [offres de support](/links/support).

Échangez avec notre [communauté d'utilisateurs](/links/community)