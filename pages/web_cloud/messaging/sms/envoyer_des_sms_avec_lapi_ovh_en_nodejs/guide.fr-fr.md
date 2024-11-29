---
title: 'Envoyer des SMS avec l’API OVHcloud en Node.js'
excerpt: 'Comment envoyer des SMS avec l’API OVHcloud RESTful en Node.js'
updated: 2020-06-18
---

## Objectif

Les SMS sont largement utilisés pour diffuser des informations pratiques, suivre l'état d'une commande ou d'un processus transactionnel, être alerté d'un évènement inhabituel ou encore rappeler des rendez-vous. Ce guide détaille la méthode d'envoi d'un premier SMS avec l'API OVHcloud en Node.js.

**Apprenez comment envoyer des SMS avec l'API OVHcloud RESTful en Node.js**

## Prérequis

- Disposer d'un compte SMS OVHcloud avec des crédits SMS
- Disposer d’un serveur Node.js et de npm. Exemple sur Ubuntu :

```
$ sudo apt-get install nodejs npm
```

Plus d'informations sur [le projet GitHub](https://github.com/ovh/node-ovh).

## En pratique

Le moyen le plus rapide pour récupérer le Wrapper NodeJs pour l’Api OVHcloud est d’utiliser npm pour ajouter le module ovh :

```
$ npm install ovh
```

Vous devez récupérer un répertoire ./node_modules/ovh/...

### Étape 1 : Création des identifiants

Des identifiants sont nécessaires pour consommer l’API SMS. Ces identifiants sont créés une fois pour identifier l’application qui va envoyer des SMS. La durée de vie de ces identifiants est paramétrable.

Créez vos identifiants de Script (all keys at once) sur cette page :
[https://api.ovh.com/createToken](https://eu.api.ovh.com/createToken/index.cgi?GET=/sms&GET=/sms/*&GET=/sms/*/jobs&POST=/sms/*/jobs) (cette url vous permet d'avoir automatiquement les bons droits pour les étapes décrites dans ce guide).

![création des tokens](images/img_2462.jpg){.thumbnail}

Dans cet exemple simple, nous récupérons les droits pour avoir accès aux informations sur le compte, à la possibilité de voir les envois en attente et à la possibilité d’envoyer des SMS.

- GET /sms/
- GET/sms/\*/jobs/
- POST /sms/\*/jobs/

L’étoile (\*) active les appels à ces méthodes pour tous vos comptes SMS. Vous pouvez également restreindre les appels à un seul compte, si vous gérez plusieurs comptes SMS sur votre compte OVHcloud, en remplaçant « /sms » par « /sms/NOM-DU-COMPTE » et « /sms/\*/ » par «/sms/NOM-DU-COMPTE/».

Vous récupérez vos identifiants pour votre script :

- Application Key (identifie votre application)
- Application Secret (authentifie votre application)
- Consumer Key (autorise l'application à accéder aux méthodes choisies)

![récupération des tokens](images/img_2463.jpg){.thumbnail}

L'environnement est prêt, les identifiants sont créés, vous êtes prêt pour coder votre script Node.js.

### Étape 2 : Récupération du serviceName et envoi d'un premier SMS

Nous allons maintenant récupérer le nom du serviceName (compte SMS que vous possédez, nous supposons que vous n'avez qu'un seul compte SMS, sinon cette partie est à implémenter). Puis nous envoyons un SMS avec le compte récupéré par le premier appel WebService :

```
var ovh = require('ovh')({
  appKey: 'your_app_key',
  appSecret: 'your_app_secret',
  consumerKey: 'your_consumer_key'
});
 
 // Get the serviceName (name of your sms account)
ovh.request('GET', '/sms', function (err, serviceName) {
  if(err) {
    console.log(err, serviceName);
  }
  else {
    console.log("My account SMS is " + serviceName);
 
    // Send a simple SMS with a short number using your serviceName
    ovh.request('POST', '/sms/' + serviceName + '/jobs', {
      message: 'Hello World!',
      senderForResponse: true,
      receivers: ['0033600000000']
    }, function (errsend, result) {
      console.log(errsend, result);
    });
  }
});
```

Lancez votre script pour envoyer votre premier SMS.

```
$ nodejs sms.js
my account SMS sms-XXXXXXX-1
{ totalCreditsRemoved: 1,
  invalidReceivers: [],
  ids: [ 2700042‡ ],
  validReceivers: [ '+33600000000' ] }
```

On récupère bien le compte SMS (ServiceName), on obtient une réponse avec 1 crédit consommé pour un numéro valide.

#### Taille des SMS à caractère commercial

Un SMS à caractère commercial devra obligatoirement inclure la mention STOP. Celle-ci contient 11 caractères et est automatiquement déduite des 160 caractères de base du 1er SMS.
Le tableau ci-dessous indique donc le nombre maximum de caractères autorisés pour les SMS à caractère commercial. 

Exemple : en encodage 7bits, si votre message fait plus de 149 caractères, il sera envoyé en 2 SMS et coûtera donc 2 crédits.

| Encodage | 1er SMS | 2ème SMS et suivants  |
|---|---|---|
| 7bits (norme GSM 03.38) | 149 caractères | 153 caractères |
| Unicode | 59 caractères | 70 caractères  |

## Aller plus loin

La console d'API ([https://api.ovh.com/console/#/sms](https://api.ovh.com/console/#/sms)) vous permettra de découvrir d'autres méthodes pour faciliter l'intégration de services SMS tels que : SMS permettant la réponse (uniquement pour les comptes OVHcloud en France), envoi en masse avec fichier CSV, publipostage, suivi des accusés de réception...

Échangez avec notre [communauté d'utilisateurs](/links/community).

