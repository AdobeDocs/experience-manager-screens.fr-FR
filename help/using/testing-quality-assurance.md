---
title: Tests et assurance qualité
seo-title: Tests et assurance qualité pour AEM Screens
description: Cette page décrit les procédures de test et d’assurance qualité dans le cadre du guide des bonnes pratiques d’AEM Screens
seo-description: Cette page décrit les procédures de test et d’assurance qualité dans le cadre du guide des bonnes pratiques d’AEM Screens
translation-type: tm+mt
source-git-commit: 2301922de9638ffb5586202d1631d0fa4754aecc

---


# Tests et assurance qualité {#testing-quality}

>[!NOTE]
>
>Cette activité est généralement réalisée par un intégrateur A/V.

À mesure que la date du déploiement du réseau de signalétique digitale se rapproche, nous devons créer un plan de test et d’assurance qualité qui porte sur chaque élément du réseau, notamment l’ensemble des composants matériels, logiciels et réseau.
Au cours de cette phase, des systèmes de test complets doivent être mis au point et soumis à des tests exhaustifs.

Il convient de créer une liste de contrôle qui identifie tous les IPC définis précédemment et qui mesure le livrable par rapport à ces indicateurs.

>[!NOTE]
> Cette phase doit également servir d’outil pour la création d’un guide d’installation et d’utilisation qui pourra être livré avec l’équipement et conservé sur site pour consultation future.

Les éléments suivants doivent être pris en compte :

## 1. Considérations mécaniques {#mechanical-considerations}

Les considérations mécaniques suivantes sont recommandées :

* Montage des écrans
* Montage du lecteur
* Ventilation
* Accessoires périphériques
* Gestion des câbles
* Mise en réseau des appareils

## 2. Considérations relatives aux logiciels {#software-considerations}

Il est recommandé de prendre en compte les éléments suivants :

* Enregistrement d’appareil
* Publication de médias
* Lecture
* Dépendances de base de données (définies précédemment)


## 3. Remarques sur la gestion des périphériques {#device-management-considerations}


AEM Screens inclut un module Device Control Center qui permet la gestion des points de fin d’application du lecteur d’écrans.

Il s’agit de tout périphérique *du lecteur* sur lequel l’application du lecteur d’écrans est installée et enregistré sur une instance d’AEM.
Ce module vous permet d’effectuer les opérations suivantes :

1. Surveillance des journaux d’erreurs de l’application
1. Gestion des captures d’écran distantes
1. Gestion des téléchargements de contenu
1. Gestion des problèmes de redémarrage de l’application

Pour en savoir plus sur ***Device Control Center***, reportez-vous à la section [Dépannage de Device Control Center](https://helpx.adobe.com/experience-manager/6-5/screens/using/monitoring-screens.html) du Guide **de l’utilisateur d’** AEM Screens.

>[!CAUTION]
> Vous ne devez pas utiliser Device Control Center pour :
>
> 1. Installer de nouvelles versions de l’application du lecteur
> 1. Surveiller les ressources au niveau du système
> 1. Configuration au niveau du système
> 1. Permet une intervention sur le bureau distant.



>[!NOTE]
> Adobe recommande d’utiliser des plateformes tierces dédiées de gestion des périphériques pour tous les déploiements.

La plateforme choisie dépend de plusieurs facteurs, dont le système ***d'exploitation*** cible, les exigences ***du*** projet et le ***nombre de points*** de fin.

Quelques exemples :

* Gestion des périphériques Google Chrome
* TeamViewer
* AirWatch42
* Engrenages
* Soti