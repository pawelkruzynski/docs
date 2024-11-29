---
title: "Activation du chiffrement des machines virtuelles avec un KMS externe"
excerpt: "Découvrez comment mettre en oeuvre le chiffrement de vos machines virtuelles avec un KMS externe non OVHcloud au sein de votre environnement VMware vSphere on OVHcloud managé"
updated: 2024-10-21
---

## Objectif

**Découvrez comment mettre en oeuvre le chiffrement de vos machines virtuelles avec un KMS externe.**

## Prérequis

- Avoir souscrit à une offre [Hosted Private Cloud](/links/hosted-private-cloud/vmware).
- Disposer d'un serveur de clé (KMS) externe compatible **[KMIP](https://en.wikipedia.org/wiki/Key_Management_Interoperability_Protocol_(KMIP)) 1.1** et dans la [matrice de compatibilité](https://www.vmware.com/resources/compatibility/search.php?deviceCategory=kms&details=1&feature=293&page=1&display_interval=500&sortColumn=Partner&sortOrder=Asc) VMware.
- Avoir accès à l’interface de gestion vSphere.
- Posséder des machines virtuelles avec une version Hardware 13 (minimum).

## En pratique

Ce guide a pour objectif d'expliquer les détails de la mise en oeuvre du chiffrement de machines virtuells sur l'offre Hosted Private Cloud VMware on OVHcloud, en employant une stratégie de stockage utilisant un **Fournisseur de clé Standard** ou KMS externe.

### Récupérer l'empreinte du certificat du serveur de clé (KMS)

Suivant votre KMS, vous pouvez vous connecter au serveur à l'aide de votre navigateur. Cliquez ensuite sur `View Certificate`{.action}, puis sur `Thumbprint`{.action}.

![empreinte du certificat](images/certificate_thumbprints_01.png){.thumbnail}

![empreinte du certificat](images/certificate_thumbprints_02.png){.thumbnail}

Extrayez ensuite la valeur de ligne `SHA1 Fingerprint`.

Voici une autre méthode avec OpenSSL :

```shell
openssl s_client -connect 192.0.2.1:5696 < /dev/null 2>/dev/null | openssl x509 -fingerprint -noout -in /dev/stdin
```

Ici, il s'agit de la valeur à droite du signe égal :

```shell
> SHA1 Fingerprint=7B:D9:46:BE:0C:1E:B0:27:CE:33:B5:2E:22:0F:00:84:F9:18:C6:61
```

### Enregistrer votre serveur de clé (KMS)

#### Via l'espace client OVHcloud

Connectez-vous à votre [espace client](/links/manager) et assurez-vous de vous situer dans la section `Hosted Private Cloud`{.action}. 

Cliquez sur `VMware`{.action} dans la barre de services à gauche, puis sélectionnez le service VMware concerné.

Depuis la page principale du service, cliquez sur `Sécurité`{.action}.

![Manager Add Kms](/pages/assets/screens/control_panel/product-selection/hosted-private-cloud/vmware/security/add_kms.png){.thumbnail}

Plus bas dans la page se trouve la section « **Virtual Machine Encryption Key Management Servers** ». Cliquez sur le bouton `Ajouter un nouveau serveur KMS`{.action}.

![server KMS](images/vm-encrypt_manager_03.png){.thumbnail}

Dans la nouvelle fenêtre qui s'affiche, saisissez les informations suivantes :

* L'adresse IP du KMS ;
* Le SSLThumbprint du KMS Server précédemment récupéré.

Validez la prise en compte de cette documentation, puis validez en cliquant sur `Suivant`{.action}. 

![server KMS](images/vm-encrypt_manager_04.png){.thumbnail}

Une fenêtre affiche la progression de la tâche.

#### Avec l'API OVHcloud

Les fonctions de chiffrement peuvent être activées grâce à [l'API OVHcloud](/pages/manage_and_operate/api/first-steps).

Pour récupérer votre « serviceName », utilisez l'appel API suivant :

> [!api]
>
> @api {v1} /dedicatedCloud GET /dedicatedCloud
>

Pour vérifier que le chiffrement n'est pas encore activé, effectuez cet appel API :

> [!api]
>
> @api {v1} /dedicatedCloud GET /dedicatedCloud/{serviceName}/vmEncryption
>

```shell
>     "state": "disabled"
```

Effectuez ensuite l'enregistrement du KMS :

> [!api]
>
> @api {v1} /dedicatedCloud POST /dedicatedCloud/{serviceName}/kms
>

Pour réaliser cette manipulation, munissez-vous des informations suivantes :

* Le « serviceName » récupéré précédemment ;
* L'adresse IP du KMS externe ;
* L'empreinte TLS du KMS externe précédemment récupéré.

### Ajouter votre serveur de clé (KMS) sur le vCenter

#### À propos de cette partie

**Le vCenter Server crée un cluster KMS lorsque vous ajoutez votre première instance KMS.** 

- Lorsque vous ajoutez le KMS, vous êtes invité à définir ce cluster par défaut. Vous pouvez le modifier ultérieurement. 
- Une fois que le vCenter a créé le premier cluster, vous pouvez lui ajouter de nouvelles instances KMS du même fournisseur. 
- Vous pouvez configurer le cluster avec au minimum une seule instance KMS.
- Si votre environnement prend en charge les solutions KMS de différents fournisseurs, vous pouvez ajouter plusieurs clusters KMS. 
- Si votre environnement comprend plusieurs clusters KMS et que vous supprimez le cluster par défaut, vous devez en définir un autre. Voir « Définir le cluster KMS par défaut ».

#### Procédure

Initiez la manipulation en vous connectant à votre Hosted Private Cloud avec le client web vSphere. 

Parcourez ensuite votre liste d'inventaire et sélectionnez le vCenter concerné. Positionnez-vous sur « Gérer », puis sur « Key Management Servers ». 

Cliquez sur `Ajouter > Ajouter un fournisseur de clés standard`{.action}.

![Add KMS](images/add_kms.png){.thumbnail}

Puis spécifiez les informations KMS dans l'assistant qui s'affiche :

![Add KMS](images/vm-encrypt_01.png){.thumbnail}

Validez le certificat en cliquant sur `Trust KMS`{.action}.

#### Import du certificat KMS

La plupart des fournisseurs de KMS ont besoin d'un certificat pour [établir une connexion sécurisée](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.security.doc/GUID-0212CEF2-7871-4E00-ADF2-0C71401D5E1A.html){.external} avec le vCenter.

Depuis le vCenter où vous avez ajouté le serveur KMS, sélectionnez celui-ci. Dans « Toutes les options », cliquez sur `Établir un lien de confiance avec KMS`{.action}.

> [!warning]
>
> Assurez-vous que le certificat n'est pas chiffré avec un mot de passe lorsque vous le téléchargez à partir du KMS. Par exemple, si vous créez un utilisateur, créez-en un sans mot de passe et téléchargez le certificat pour l'utilisateur KMS.
> 

![import certificat KMS](images/vm-encrypt_02.png){.thumbnail}

#### Vérifier que le KMS est configuré

Vérifiez que le « **Connection Status** » correspondant au KMS est en mode « Normal ».

![vérifier connection status](images/vm-encrypt_03.png){.thumbnail}

#### Modifier la politique de stockage de « VM Encryption Storage »

Créez une machine virtuelle. Une fois celle-ci créée, effectuez un clic droit sur celle-ci. Cliquez alors sur `VM Policies`{.action}, puis sur `Edit VM Storage Policies`{.action}.

![VM encryption storage](images/vm-encrypt_04.png){.thumbnail}

Sélectionnez les fichiers de la machine virtuelle et les autres disques durs qui doivent être chiffrés.

![VM encryption storage](images/vm-encrypt_05.png){.thumbnail}

Assurez-vous que les tâches se sont effectuées sans erreurs.

> [!primary]
>
> Si le KMS n'est pas configuré correctement et qu'il y a des dysfonctionnements avec l'échange de clés entre vCenter et KMS, il y aura une erreur « RuntimeFault » dans la tâche comportant le message d'erreur « Cannot generate key ».
>

#### vMotion chiffré

Concernant le vMotion, le chiffrement fonctionne au niveau de la machine virtuelle. Pour la synchronisation, des clés de cryptage de 256 bits sont utilisées.

Le chiffrement du trafic vMotion fonctionne au niveau du noyau de la machine virtuelle avec l'algorithme AES-GCM (Advanced Encryption Standard-Galois Counter Mode) largement utilisé.

Modifiez ensuite votre machine virtuelle et cliquez sur `VM Options`{.action}

Vous devez sélectionner les options si votre vMotion doit être chiffré. Il existe trois politiques pour du vMotion chiffré :

|     Statut      | Description                                                                                                                                  |
|:---------------:|:---------------------------------------------------------------------------------------------------------------------------------------------|
|    Disabled     | - Éteint.                                                                                                                                    |
|  Opportunistic  | - Chiffrement uniquement s'il est pris en charge par l'hôte source et l'hôte cible ESXi. Dans le cas contraire, vMotion ne sera pas chiffré. |
|    Required     | - Le chiffrement sera utilisé.                                                                                                               |

![vMotion chiffré](images/vm-encrypt_06.png){.thumbnail}

Le déplacement des machines entre les hôtes est effectué par l'échange de clés uniques, qui sont générées et servies par le serveur vCenter, plutôt que par KMS.

#### Vérifications de la configuration

Vérifiez qu'un petit cadenas est apparent, et que le disque est bien chiffré dans les informations de votre VM.

Vérifiez dans les paramètres de votre VM que votre politique de stockage est bien celle qui utilise le chiffrement `VM encryption Policy`. 

![vérification de la configuration](images/vm-encrypt_07.png){.thumbnail}

![vérification de la configuration](images/vm-encrypt_09.png){.thumbnail}

Pour terminer, vous pouvez regarder les tasks et events pour avoir la confirmation finale que la configuration a bien fonctionné.

## Aller plus loin

Si vous rencontrez des problèmes avec la configuration de votre KMS externe, nous vous invitons à contacter le [support](https://help.ovhcloud.com/csm?id=csm_get_help) ou à envisager d'utiliser un KMS OVHcloud (OKMS). 

Vous pouvez ainsi lire le guide suivant, qui détaille la procédure à suivre : [KMS for VMware on OVHcloud - Solution et cas d'usages pour chiffrer des VM](/pages/hosted_private_cloud/hosted_private_cloud_powered_by_vmware/vmware_overall_vm-encrypt).

Échangez avec notre [communauté d’utilisateurs](/links/community).
