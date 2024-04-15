---
title: Tests et assurance qualité
description: Découvrez les tests et l’assurance qualité pour AEM Screens dans le guide des bonnes pratiques.
exl-id: cc3bfb88-1341-43f8-b247-6a41f1d1a963
source-git-commit: 3c4b37b3b9f268b500562fa4ce3782b7be1e7d74
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 51%

---

# Tests et assurance qualité {#testing-quality}

>[!NOTE]
>Cette activité est généralement réalisée par un intégrateur audio/vidéo.

À mesure que vous vous approchez du déploiement du réseau de signalétique digitale, créez un plan de test et d’assurance qualité qui s’adresse à chaque élément du réseau, y compris tous les composants matériels, logiciels et réseau.
Au cours de cette phase, des systèmes de test complets doivent être mis au point et soumis à des tests exhaustifs.

Il est nécessaire de créer une liste de contrôle qui identifie tous les IPC définis précédemment et qui mesure les livrables par rapport à ces indicateurs.

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
* Mise en réseau des appareils

## 2. Facteurs logiciels {#software-considerations}

Il est recommandé de tenir compte des facteurs logiciels suivants :

* Enregistrement d’appareils
* Publication de médias
* Lecture
* Dépendances de base de données (définies précédemment)


## 3. Facteurs de gestion des périphériques {#device-management-considerations}

AEM Screens dispose d’un module de centre de contrôle des appareils qui permet de gérer les points d’extrémité de l’application du lecteur Screens.

Cela fait référence à tout appareil matériel de *lecture* sur lequel cette application est installée ; il est également enregistré sur une instance AEM.
Ce module permet d’effectuer les opérations suivantes :

1. Surveiller les journaux d’erreurs de l’application du lecteur
1. Gestion des captures d’écran distantes
1. Gérer les téléchargements de contenus
1. Gérer les problèmes de redémarrage de l’application

Pour en savoir plus sur ***Centre de contrôle des périphériques***, voir [Dépannage du Centre de contrôle des périphériques](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/troubleshooting/monitoring-screens) in **Guide de l’utilisateur d’AEM Screens**.

>[!CAUTION]
>
>N’utilisez pas le Centre de contrôle des périphériques pour :
>
>* installer de nouvelles versions de l’application du lecteur ;
>* surveiller les ressources système ;
>* résoudre des erreurs au niveau du système ;
>* autoriser une intervention à distance sur le poste de travail.


>[!NOTE]
>
> Adobe recommande que des plateformes tierces dédiées de gestion des périphériques soient utilisées pour tous les déploiements.

La plateforme choisie dépend de plusieurs facteurs, dont : ***système d&#39;exploitation cible***, ***exigences du projet***, et ***nombre de points de fin***.

Voici quelques exemples :

* Google Chrome Device Management
* TeamViewer
* AirWatch
* `42Gears`
* Intergiciel propriétaire de l’intégrateur audio/vidéo
