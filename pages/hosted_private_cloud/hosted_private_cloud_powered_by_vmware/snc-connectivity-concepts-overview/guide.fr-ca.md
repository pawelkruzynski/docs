---
title: Présentation des concepts
excerpt: 'Présentation des concepts de SecNumCloud Connectivity'
updated: 2021-11-18
---

## Présentation de SecNumCloud Connectivity

Les produits OVHcloud SecNumCloud nécessitent une connexion sécurisée pour répondre aux exigences de conformité. Une telle connexion est sécurisée par le protocole IPsec du vRack pour une connectivité externe et par un lien sécurisé entre zones SecNumCloud.

## Avantages de la solution SecNumCloud Connectivity

### Extension réseau

À partir du vRack, les tunnels IPsec peuvent être étendus avec n'importe quel produit OVHcloud dans le vRack, y compris, et de manière non limitée, OVHcloud Connect pour les points de terminaison IPsec distants.

### Performances

OVHcloud utilise des applications matérielles dédiées pour obtenir les meilleures performances et fournir une connexion à haut débit, depuis l'extérieur et entre les zones SecNumCloud.

### Haute disponibilité

La connexion IPsec se fait via deux périphériques (par zone SecNumCloud). BGP dans les tunnels IPsec permet une résilience maximale.

## Composants de la solution SecNumCloud Connectivity

![SNC Network Global Overview](images/SNC-Global-Network.svg){.thumbnail}

### Sous-réseau

* Un sous-réseau est composé d’un préfixe IPv4. Taille maximale prise en charge : /24
* Les produits SecNumCloud sont attachés aux sous-réseaux.
* Un sous-réseau est disponible dans une seule zone SecNumCloud, il ne peut pas être étendu entre des datacenters ou entre des zones SecNumCloud et non-SecNumCloud.

### SPN

SPN signifie Secure Private Network. Il s'agit de l'instance de routage contenant les sous-réseaux.

### Connecteur SPN

Le but est d'acheminer le trafic entre les SPN. Par défaut, un SPN Connector est local sur une zone SecNumCloud et peut être upgradé en global sur plusieurs zones SecNumCloud.

### VPN-SPN

Le VPN-SPN gère la connectivité réseau externe via le protocole IPsec.

## Aller plus loin

Si vous avez besoin d'une formation ou d'une assistance technique pour la mise en oeuvre de nos solutions, contactez votre commercial ou cliquez sur [ce lien](/links/professional-services) pour obtenir un devis et demander une analyse personnalisée de votre projet à nos experts de l’équipe Professional Services. 

Échangez avec notre [communauté d'utilisateurs](/links/community).
