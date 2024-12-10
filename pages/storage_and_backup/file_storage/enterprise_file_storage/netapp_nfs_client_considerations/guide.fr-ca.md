---
title: "Enterprise File Storage - Particularités concernant certains clients NFS"
excerpt: "Paramètres spécifiques à vérifier et/ou à mettre en oeuvre concernant l'offre Enterprise File Storage"
updated: 2024-11-08
---

## Objectif

**Découvrez comment permettre l'accès en lecture/écriture à votre Entreprise File Storage depuis certains clients NFS.**

## Prérequis

- Disposer d'une offre [Enterprise File Storage](/links/storage/enterprise-file-storage)

## En pratique

### Clients NFS Microsoft Windows

#### Assurez-vous que l'utilisateur Windows qui est utilisé pour accéder à votre Entreprise File Storage dispose de droits suffisants

En effet, le couple UID/GID doit être configuré à 0 (droit unix root).

Si ce n'est pas le cas, vous aurez des erreurs d'accès à votre Entreprise File Storage car, lorsque NFS est autorisé sur une machine Windows, un utilisateur UNIX est créé avec l'UID et le GID par défaut à -2 (ou 4294967294).

Comme solution de contournement, l'UID et le GID peuvent être forcés à 0 sur la machine Windows qui accède à votre Entreprise File Storage.

- Démarrez l'éditeur de registre sur la machine cliente.
- Localisez `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ClientForNFS\CurrentVersion\Default`.
- Créez deux valeurs DWORD, à savoir AnonymousUid et AnonymousGid.
- Définissez ces valeurs sur l'UID et le GID à 0.
- Redémarrez le service NFS sur la machine cliente.

> [!primary]
>
> **Documentations de référence :**
>
> - <https://techcommunity.microsoft.com/t5/running-sap-applications-on-the/installation-configuration-of-windows-nfs-client-to-enable/ba-p/367084>
> - <https://learn.microsoft.com/fr-fr/archive/blogs/msdn/sfu/can-i-set-up-user-name-mapping-in-windows-vista>
> - <https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753302(v=ws.10)?redirectedfrom=MSDN>
> - <https://kb.netapp.com/on-prem/ontap/da/NAS/NAS-KBs/Unable_to_perform_write_operations_on_an_export_mounted_on_a_Windows_machine>

#### Demandez l'activation de la fonctionnalité « showmount » au support OVHcloud

Pour des raisons de sécurité, l'option « showmount » permettant de lister les partages disponibles sur un serveur NFS est désactivée par défaut.
Cependant, si vous obtenez des erreurs de type « erreur périphérique invalide » lors de certaines opérations d'écritures ou si vous utilisez une application qui doit absolument utiliser cette fonctionnalité, ouvrez un [ticket auprès du support OVHcloud](https://help.ovhcloud.com/csm?id=csm_get_help) afin de demander qu'elle soit activée exceptionnellement.

> [!primary]
>
> **Documentation de référence :**
>
> - <https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/showmount>

## Aller plus loin

Si vous avez besoin d'une formation ou d'une assistance technique pour la mise en oeuvre de nos solutions, contactez votre commercial ou cliquez sur [ce lien](/links/professional-services) pour obtenir un devis et demander une analyse personnalisée de votre projet à nos experts de l’équipe Professional Services.

Échangez avec notre [communauté d'utilisateurs](/links/community).
