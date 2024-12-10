---
title: Supprimer un datastore
excerpt: Découvrez comment supprimer un datastore de votre Private Cloud
updated: 2020-07-01
---

## Objectif

Dans certains cas, il peut être utile de supprimer un datastore de votre cluster, par exemple pour le remplacer ou le faire évoluer vers une taille supérieure.

**Ce guide vous explique comment retirer en toute sécurité un datastore de votre infrastructure.**

## Prérequis

* Posséder une offre [Hosted Private Cloud](https://www.ovhcloud.com/fr-ca/enterprise/products/hosted-private-cloud/){.external}.
* Accéder à l’interface de gestion vSphere.

## En pratique

> [!warning]
>
> Pour des raisons de sécurité, la demande de suppression échouera si vous avez des machines virtuelles (VM) présentes sur le datastore concerné (vous trouverez la liste dans la fenêtre de validation).
> 

Pour supprimer un datastore, la première étape consiste à effectuer un clic droit sur la ressource concernée. Sélectionnez `OVHcloud`{.action}, puis `Retirer ce stockage`{.action}.

![Choix du datastore](images/removedatastore01.png){.thumbnail}

Une fenêtre de confirmation s'ouvre. Validez alors avec `Next`{.action}.

![Confirmation de la suppression](images/removedatastore02.png){.thumbnail}

La demande de suppression est dès lors prise en compte.

![Suppression validée](images/removedatastore03.png){.thumbnail}

Il est possible de surveiller la progression de la suppression du datastore via les tâches récentes.

![Tâche de suivi de la suppression](images/removedatastore04.png){.thumbnail}

## Aller plus loin

Échangez avec notre [communauté d'utilisateurs](/links/community).
