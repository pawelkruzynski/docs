---
title: 'Load Balancer FAQ'
excerpt: 'FAQ Load Balancer'
updated: 2018-03-26
---

## Comment configurer mon Firewall pour accepter le trafic provenant du service Load Balancer OVHcloud ?

Lors de l'utilisation du Load-Balancer, vos clients ne se connectent pas directement à vos serveurs. Une bonne pratique est de mettre en place un Firewall (Pare-Feu) pour autoriser uniquement le trafic provenant du service Load Balancer OVHcloud.

- Pour déterminer les IPs à autoriser dans votre Firewall, vous pouvez utiliser la fonction API suivante :

> [!api]
>
> @api {v1} /ipLoadbalancing GET /ipLoadbalancing/{serviceName}/natIp
> 

## Comment connaître l'état de mon service ?

Parfois, il peut être utile de connaître l'état de votre service Load Balancer OVHcloud.

- Pour déterminer l'état de votre service, vous pouvez utiliser la fonction API suivante :

> [!api]
>
> @api {v1} /ipLoadbalancing GET /ipLoadbalancing/{serviceName}/instancesState
> 

L'état des différentes instances du Load Balancer OVHcloud peut être `running` (actif), `reload` (en cours de rafraîchissement), `unknown` (pas encore démarré) ou `dead` (inactif).

## Comment ajouter une Additional IP au service Load Balancer OVHcloud ?

L'Additional IP est une IP supplémentaire sur laquelle peut être joint votre service en plus de l'IP principale. L'Additional IP peut être basculée d'un service à un autre en quelques secondes.

- Pour ajouter une Additional IP à un service Load Balancer OVHcloud :

> [!api]
>
> @api {v1} /ip POST /ip/{ip}/move
> 

- Appliquer les modifications :

> [!api]
>
> @api {v1} /ipLoadbalancing POST /ipLoadbalancing/{serviceName}/refresh
> 

## Comment lister les Additional IP rattachées au service Load Balancer OVHcloud ?

Utilisez l'appel API suivant :

> [!api]
>
> @api {v1} /ipLoadbalancing GET /ipLoadbalancing/{serviceName}/failover
> 

## Comment commander un certificat SSL gratuit ?

Il est possible de commander un certificat SSL gratuit pour le Load Balancer OVHcloud.

- Pour commander un certificat gratuit, vous pouvez utiliser la fonction API suivante, en renseignant le champ `fqdn` :

> [!api]
>
> @api {v1} /ipLoadbalancing POST /ipLoadbalancing/{serviceName}/freeCertificate
> 

Il est possible de commander un certificat multi-domaine ; le champ `fqdn` prend comme paramètre un tableau de chaîne de caractères.

Pour que la commande se finalise, il faut obligatoirement que le nom de domaine choisi pointe vers votre Load Balancer OVHcloud.

## Comment lister les certificats SSL associés au Load Balancer OVHcloud ?

- Pour lister les certificats SSL associés au Load Balancer OVHcloud, vous pouvez utiliser la fonction API suivante :

> [!api]
>
> @api {v1} /ipLoadbalancing GET /ipLoadbalancing/{serviceName}/ssl
>

Les certificats commandés (gratuit ou non) sont de type `built`. Ceux ajoutés par vous-même sont de type `custom`.

Un certificat de type `built_not_routed` est un certificat qui a été commandé et livré, mais dont le domaine n'a pas pu être validé. Généralement, c'est parce que le domaine ne pointe plus vers le Load Balancer OVHcloud.

- Pour obtenir les détails d'un certificat SSL, vous pouvez utiliser la fonction API suivante :

> [!api]
>
> @api {v1} /ipLoadbalancing GET /ipLoadbalancing/{serviceName}/ssl/{id}
>

## Aller plus loin

Échangez avec notre [communauté d'utilisateurs](/links/community).
