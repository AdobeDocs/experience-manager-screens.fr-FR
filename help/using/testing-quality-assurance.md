---
title: Tests et assurance qualité
description: Découvrez les tests et l’assurance qualité pour AEM Screens dans le guide des bonnes pratiques.
exl-id: cc3bfb88-1341-43f8-b247-6a41f1d1a963
source-git-commit: ef74265eadf5972eae7451b7725946d8b014c198
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 28%

---

# Tests et assurance qualité {#testing-quality}

>[!NOTE]
>Une partie prenante standard de cette activité est un intégrateur audio/vidéo.

À mesure que vous vous approchez du déploiement du réseau de signalétique digitale, créez un plan de test et d’assurance qualité qui s’adresse à chaque élément du réseau, y compris tous les composants matériels, logiciels et réseau.
Au cours de cette phase, des systèmes de test complets doivent être mis au point et soumis à des tests exhaustifs.

Il est nécessaire de créer une liste de contrôle qui identifie tous les IPC définis précédemment et qui mesure les livrables par rapport à ces indicateurs.

>[!NOTE]
>
>Cette phase doit également être utilisée comme outil pour créer un guide d’installation et d’utilisation. Les deux peuvent ensuite être livrés avec l’équipement et conservés sur site à des fins de référence ultérieure.

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

AEM Screens comprend un module de centre de contrôle des périphériques qui permet de gérer les points de terminaison de l’application du lecteur Screens.

Il fait référence à tout *player* Périphérique matériel sur lequel l’application du lecteur Screens est installée et enregistré sur une instance d’AEM.
Ce module permet :

1. Surveiller les journaux d’erreurs de l’application du lecteur
1. Gestion des captures d’écran distantes
1. Gérer les téléchargements de contenus
1. Gérer les problèmes de redémarrage de l’application

Pour en savoir plus sur les ***Centre de contrôle des périphériques***, voir [Dépannage du Centre de contrôle des périphériques](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/troubleshooting/monitoring-screens) in **Guide de l’utilisateur d’AEM Screens**.

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
