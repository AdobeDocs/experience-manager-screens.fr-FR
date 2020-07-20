---
title: Tests et assurance qualité
seo-title: Tests et assurance qualité pour AEM Screens
description: Cette page décrit les procédures de test et d’assurance qualité dans le cadre du guide des bonnes pratiques d’AEM Screens
seo-description: Cette page décrit les procédures de test et d’assurance qualité dans le cadre du guide des bonnes pratiques d’AEM Screens
translation-type: ht
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: ht
source-wordcount: '361'
ht-degree: 100%

---


# Tests et assurance qualité {#testing-quality}

>[!NOTE]
>
>Cette activité est généralement réalisée par un intégrateur A/V.

À mesure que la date du déploiement du réseau de signalétique digitale se rapproche, nous devons créer un plan de test et d’assurance qualité qui porte sur chaque élément du réseau, notamment l’ensemble des composants matériels, logiciels et réseau.
Au cours de cette phase, des systèmes de test complets doivent être mis au point et soumis à des tests exhaustifs.

Il convient de créer une liste de contrôle qui identifie tous les IPC définis précédemment et qui mesure le livrable par rapport à ces indicateurs.

>[!NOTE]
>
>Cette phase doit également servir d’outil pour la création d’un guide d’installation et d’utilisation qui pourra être livré avec l’équipement et conservé sur site pour consultation future.

Les éléments suivants doivent être pris en compte :

## 1. Facteurs mécaniques {#mechanical-considerations}

Il est recommandé de tenir compte des facteurs mécaniques suivants :

* Montage des écrans
* Montage du lecteur
* Ventilation
* Accessoires périphériques
* Gestion des câbles
* Mise en réseau des périphériques

## 2. Facteurs logiciels {#software-considerations}

Il est recommandé de tenir compte des facteurs logiciels suivants :

* Enregistrement de périphériques
* Publication de médias
* Lecture
* Dépendances de base de données (définies précédemment)


## 3. Facteurs de gestion des périphériques {#device-management-considerations}


AEM Screens dispose d’un module de centre de contrôle des périphériques qui permet de gérer les points d’extrémité de l’application du lecteur Screens.

Cela fait référence à tout périphérique matériel de *lecture* sur lequel cette application est installée ; il est également enregistré sur une instance AEM.
Ce module permet d’effectuer les opérations suivantes :

1. Surveiller les journaux d’erreurs de l’application du lecteur
1. Gérer les captures d’écran distantes
1. Gérer les téléchargements de contenus
1. Gérer les problèmes de redémarrage de l’application

Pour en savoir plus sur le ***Centre de contrôle des périphériques***, reportez-vous à la section [Dépannage du Centre de contrôle des périphériques](https://helpx.adobe.com/fr/experience-manager/6-5/screens/using/monitoring-screens.html) du **Guide de l’utilisateur d’AEM Screens**.

>[!CAUTION]
>
> Vous ne devez pas utiliser le Centre de contrôle des périphériques pour :
>
> 1. installer de nouvelles versions de l’application du lecteur ;
> 1. surveiller les ressources système ;
> 1. résoudre des erreurs au niveau du système ;
> 1. autoriser une intervention à distance sur le poste de travail.



>[!NOTE]
>
> Adobe recommande d’utiliser des plates-formes tierces dédiées de gestion de périphériques pour tous les déploiements.

La plate-forme spécifique choisie dépend de plusieurs facteurs, dont le ***système d&#39;exploitation cible******, les exigences du projet*** et le ***nombre de points d’extrémité***.

Exemples :

* Google Chrome Device Management
* TeamViewer
* AirWatch
* 42Gears
* Intergiciel propriétaire de l’intégrateur A/V
