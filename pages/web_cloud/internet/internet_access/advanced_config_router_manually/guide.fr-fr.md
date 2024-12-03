---
title: 'Configurer un routeur manuellement'
excerpt: 'Découvrez comment configurer votre accès internet OVHcloud sur votre propre routeur'
updated: 2024-01-10
---

## Objectif

Si vous souhaitez utiliser votre équipement personnel pour gérer la connexion PPPoE sur votre offre xDSL/FTTH OVHcloud, vous devez récupérer les identifiants PPPoE associés à cet accès.<br>
Si vous ne les connaissez pas, vous pouvez les récupérer en suivant les étapes de notre guide « [Obtenir les identifiants PPPoE](/pages/web_cloud/internet/internet_access/obtenir_id_ppp) ».

**Découvrez comment configurer votre accès internet OVHcloud sur votre propre routeur**.

## Prérequis

- Disposer d'une [offre xDSL ou FTTH OVHcloud](https://www.ovhtelecom.fr/offre-internet/) active.
- Disposer d'un équipement (routeur, firewall) compatible PPPoE.
- Disposer des identifiants PPPoE de votre accès internet OVHcloud.

## En pratique

Les identifiants PPPoE vous sont envoyés par e-mail (à l'adresse e-mail de contact de votre compte OVHcloud) lors de la livraison de votre accès.<br>
Ces identifiants vous permettent de configurer votre modem OVHcloud (dans le cas d’une configuration manuelle en local du modem fourni par OVHcloud) ou de votre équipement personnel pour l’usage de votre accès à Internet.

Si votre offre a été fournie avec un modem OVHcloud, les identifiants PPPoE vous sont envoyés par e-mail systématiquement après chaque réinitialisation du modem.

Le *login* reste identique après chaque réinitialisation.<br>
Pour des raisons de sécurité, le *mot de passe* est systématiquement modifié après chaque réinitialisation de votre routeur OVHcloud.

Si vous utilisez votre propre modem/routeur, vous pouvez utiliser les API OVHcloud afin de [générer l'envoi de nouveaux identifiants PPPoE par e-mail](/pages/web_cloud/internet/internet_access/obtenir_id_ppp).

> [!warning]
>
> Chaque routeur à une méthode de configuration différente.
> Ce guide liste les paramètres indispensables pour faire fonctionner votre connexion mais nous vous invitons à lire le manuel utilisateur de votre modem/routeur pour vérifier comment les appliquer.
>

### Connaître le profil de son modem

Le profil de votre accès est disponible sur l'espace client. Pour le retrouver, connectez-vous à votre [espace client OVHcloud](https://www.ovh.com/auth?onsuccess=https%3A%2F%2Fwww.ovhtelecom.fr%2Fmanager&ovhSubsidiary=fr), partie `Telecom`{.action}.

Cliquez sur `Accès Internet`{.action} puis sélectionnez votre offre xDSL ou FTTH.

![serviceName dans espace client](images/servicename-2022.png){.thumbnail}

Par défaut, l'onglet affiché est `Mon accès`.

Vous retrouverez, dans les `Caractéristiques`, les informations sur le profil du modem dans la section `Connexion`.

![modem profil dans espace client](images/profil-2023.png){.thumbnail}

### Profil Standard

Ce profil s'applique aux typologies d'accès suivantes :

- Accès ADSL/VDSL (Cuivre) et FTTH (Fibre) Covage
- Accès ADSL/VDSL (Cuivre) et FTTH (Fibre) en collecte SFR
- Accès ADSL/VDSL (Cuivre) et FTTH (Fibre) en collecte AXIONE
- Accès ADSL (Cuivre) en collecte ORANGE

Les paramètres à configurer sont :

- **Mode de connexion**: PPPoE
- **Nom d'utilisateur PPPoE**: le login reçu par e-mail (exemple: `0320xxyyzz_1@ovh.kosc`)
- **Mot de passe PPPoE**: le mot de passe reçu par e-mail
- **MTU**: 1432 ou 1456 ou **1492** (recommandé)
- **VLAN**: aucun VLAN
- **IPv6**: IPv4/IPv6 DualStack, IPCPv6 activé
- **Pour l'ADSL**:
    - **Type**: ADSL over ATM
    - **VPI**: 8
    - **VCI**: 35
    - **Encapsulation**: LLC/SNAP-BRIDGING
    - **Service Category**: UBR without PCR
- **Pour le VDSL**:
    - **Type**: VDSL over PTM
- **Pour le FTTH**:
    - **Type**: Ethernet

### Profil Orange

> [!primary]
> La différence avec le profil Standard est l'activation du VLAN 835.
>

Ce profil s'applique aux typologies d'accès suivantes :

- Accès VDSL (Cuivre) et FTTH (Fibre) en collecte Orange

Les paramètres à configurer sont :

- **Mode de connexion**: PPPoE
- **Nom d'utilisateur PPPoE**: le login reçu par e-mail (exemple: `0320xxyyzz_1@adsl.ovh`)
- **Mot de passe PPPoE**: le mot de passe reçu par e-mail
- **MTU**: 1432 ou 1456 ou **1492** (recommandé)
- **VLAN**: 835 (802.1p : 0 , 802.1q: 835)
- **IPv6**: IPv4/IPv6 DualStack, IPCPv6 activé
- **Pour le VDSL**:
    - **Type**: VDSL over PTM
- **Pour le FTTH**:
    - **Type**: Ethernet

### Profil Bouygues

> [!primary]
> La différence avec le profil Standard est l'activation du VLAN 4001.
>

Ce profil s'applique aux typologies d'accès suivantes :

- Accès FTTH (Fibre) en collecte Bouygues

Les paramètres à configurer sont :

- **Mode de connexion**: PPPoE
- **Nom d'utilisateur PPPoE**: le login reçu par e-mail (exemple: `FP_1111xxyy_1@byt.ovhcloud`)
- **Mot de passe PPPoE**: le mot de passe reçu par e-mail
- **MTU**: 1432 ou 1456 ou **1492** (recommandé)
- **VLAN**: 4001 (802.1p : 0 , 802.1q: 4001)
- **IPv6**: IPv4/IPv6 DualStack, IPCPv6 activé
- **Pour le FTTH**:
    - **Type**: Ethernet

## Aller plus loin

Échangez avec notre [communauté d'utilisateurs](/links/community).
