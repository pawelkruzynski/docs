---
title: 'Préparer l’environnement pour utiliser l’API OpenStack'
excerpt: "Installez l'environnement OpenStack pour piloter vos instances via API"
updated: 2024-01-22
---

## Objectif

Il est possible d'administrer les services Public Cloud à l’aide des commandes issues de la console système, après le téléchargement et l’installation des outils OpenStack.

Grâce à l'API OpenStack, vous pouvez automatiser cette gestion en générant des scripts.

> [!primary]
>
> OpenStack requiert Python >=3.8.
> Ce guide décrit l'installation du paquet `python-openstackclient` qui regroupe la ligne de commande pour la majorité des projets OpenStack.
> Le projet Octavia (qui alimente le `Load Balancer Public Cloud`) n’est pas inclus. Vous devez donc exécuter `pip3 install python-octaviaclient` en plus des instructions d'installation ci-dessous.
> De la même manière, si vous utilisez le projet Barbican pour gérer des secrets, la commande `pip3 install python-barbicanclient` doit aussi être ajoutée à la procédure ci dessous.
>

**Découvrez comment installer ces outils OpenStack.**

## Prérequis

- Disposer d'un accès **root** à l'environnement que vous souhaitez configurer.

## En pratique

### Sous Debian

Ouvrez le terminal ou connectez-vous en SSH à l'environnement que vous souhaitez préparer.

Mettez à jour le cache des paquets, grâce à la commande `apt update`:

```sh
apt update
```

Utilisez la commande ci-dessous pour installer les clients OpenStack :

```sh
$ apt install python3-pip python3-venv -y
$ python3 -m venv env
$ source env/bin/activate
(env)$ pip3 install --upgrade pip
(env)$ pip3 install python-openstackclient
```

À l'issue de cette étape, nous vous recommandons de créer un utilisateur spécial pour ne pas vous servir de l’utilisateur root.

Pour accéder aux outils d'aide, exécutez la commande suivante :

```sh
openstack --help
```

> [!primary]
>
> La documentation relative à l’API OpenStack est disponible [sur cette page](https://docs.openstack.org/python-openstackclient/latest/){.external}.
>

### Sous CentOS

Ouvrez le terminal ou connectez-vous en SSH à l'environnement que vous souhaitez préparer.

Mettez à jour le cache des paquets grâce à la commande suivante :

```sh
yum update -y
```

Utilisez la commande ci-dessous pour installer les clients OpenStack :

```sh
yum install python3-pip -y
$ python3 -m venv env
$ source env/bin/activate
(env)$ pip3 install --upgrade pip
(env)$ pip3 install python-openstackclient
```

À l'issue de cette étape, nous vous recommandons de créer un utilisateur spécial pour ne pas vous servir de l’utilisateur root.

Pour accéder aux outils d'aide, exécutez la commande suivante :

```sh
openstack --help
```

> [!primary]
>
> La documentation relative à l’API OpenStack est disponible [sur cette page](https://docs.openstack.org/python-openstackclient/latest/){.external}.
>

### Sous Windows

Téléchargez et installez la version 3.12.0 de Python. Vous pouvez choisir d'ajouter automatiquement le langage de programmation Python à Path, en cochant cette option dans le configurateur d'installation :

![Installation automatique](images/1_preparation_openstack_environment_windows.png){.thumbnail}

Vous pouvez également effectuer l'installation par vous-même. Pour ce faire, suivez les actions décrites ci-dessous :

#### Étape 1 : éditer les variables d'environnement du système

Recherchez les paramètres des variables d'environnement du système et positionnez-vous sur « Éditer les variables environnement du système » :

![Paramètres des variables d’environnement ](images/2_preparation_openstack_environment_windows.png){.thumbnail}

#### Étape 2 : éditer les paramètres du système

Passez à l’onglet `Avancé`{.action} et cliquez sur `Variables environnement`{.action}, pour éditer les paramètres.

![Paramètres de performance](images/3_preparation_openstack_environment_windows.png){.thumbnail}

#### Étape 3 : configurer les variables d'environnement

Dans la section « Variables système », choisissez « Nouveau », attribuez le nom « PYTHON_HOME » et ajoutez le chemin jusqu'à Python.

![Ajout du chemin d'accès](images/4_edit_system_variables.png){.thumbnail}

#### Étape 4 : ajouter le chemin pour les variables

Après l’ajout de Python, éditez « Path » (chemin) dans les variables système et ajoutez à la fin du chemin :

`...;%PYTHON_HOME%\;%PYTHON_HOME%\Script`

#### Étape 5 : redémarrer Windows

Les modifications introduites seront prises en compte une fois le système redémarré.

#### Étape 6 : installer le client OpenStack

Connecté en tant qu'administrateur, ouvrez le programme en ligne de commande (CMD) et installez le client OpenStack en utilisant la commande suivante :

```sh
pip install python-openstackclient
```

Si l'opération s'est correctement déroulée, un résumé s'affiche :

![Installation automatique](images/5_preparation_openstack_environment_windows.png){.thumbnail}

Vous pouvez vérifier la version d'installation dans la fenêtre CMD (ligne de commande) nouvellement ouverte, en saisissant « python-V » depuis n'importe quel emplacement du système.

![Vérification](images/6_preparation_openstack_environment_windows.png){.thumbnail}

### Sous MacOS

Vous pouvez utiliser [HomeBrew](https://brew.sh), un gestionnaire de paquets pour MacOS.

Ouvrez le terminal et entrez la commande suivante :

```bash
brew install openstackclient
```

Pour accéder aux outils d'aide, exécutez la commande suivante :

```sh
openstack --help
```

## Aller plus loin

[Charger les variables d’environnement OpenStack](/pages/public_cloud/compute/loading_openstack_environment_variables).

Échangez avec notre [communauté d'utilisateurs](/links/community).
