---
title: Hôte de spare
excerpt: Comprendre le mécanisme de remplacement d'hôte
updated: 2020-11-18
---

## Prérequis

- Disposer d'une offre [Managed Bare Metal](https://www.ovhcloud.com/fr-ca/managed-bare-metal/){.external}.

## Objectifs

OVHcloud garantit dans ses contrats le remplacement d'un hôte inaccessible.

**Ce guide explique le fonctionnement de ce remplacement.**

## Livraison d’un hôte de spare

Si l’un de vos hôtes est victime d’une panne, afin d’assurer la continuité de service, nous vous livrons automatiquement un hôte de remplacement gratuit dans votre infrastructure. 

Dès que cet hôte est livré, vous recevez un email vous indiquant toutes les informations concernant cet hôte ainsi que son adresse IP vous permettant de le retrouver facilement dans votre interface vSphere.

Par défaut, le service HA ([High Availability)](/pages/bare_metal_cloud/managed_bare_metal/vmware_ha_high_availability) de VMware est activé sur votre cluster. Si vous l’avez laissé activé, vos machines virtuelles vont redémarrer automatiquement. Si le service DRS (Distributed Ressources Scheduler) est activé et configuré en mode « Entièrement Automatisé », la répartition de charge sur les hôtes de votre cluster sera également effectuée automatiquement.

> [!warning]
> 
> Si un lecteur CD/DVD est encore monté ou connecté sur une VM, le service HA ne pourra pas la redémarrer sur l'hôte de spare. Il est recommandé de toujours avoir le lecteur CD/DVD en périphérique client.
>

## Que faire après avoir reçu le hôte de spare

Une fois que l'hôte original est de nouveau fonctionnel (une fois réparé), vous pouvez nous rendre l’un des deux hôtes (l'hôte de spare ou l'hôte original).

Nous vous recommandons de nous rendre l'hôte original afin que nous puissions lui faire subir une batterie de tests suite à cet incident (pour éviter d’éventuelles futures pannes). Vous pourrez alors conserver l'hôte de spare. Pour cela vous pouvez suivre le guide [suppression d’un hôte](/pages/bare_metal_cloud/managed_bare_metal/delete_host)

OVHcloud pourra récupérer automatiquement l'hôte original dès que celui-ci est retiré.

## Aller plus loin

Échangez avec notre [communauté d'utilisateurs](/links/community).
