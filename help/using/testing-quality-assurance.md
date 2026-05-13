---
title: Tests et assurance qualité
description: Découvrez les tests et l’assurance qualité dans le cadre du guide des bonnes pratiques d’AEM Screens.
exl-id: cc3bfb88-1341-43f8-b247-6a41f1d1a963
TQID: https://experienceleague.adobe.com/So83gHv7n21zhdoCdWHVf0yswyQuSr1hLWmCA7uHSiE
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2: id: c1579802-ddd4-4214-8a91-97b2066abe11
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 346
ht-degree: 97%

---

# Tests et assurance qualité {#testing-quality}

>[!NOTE]
>Cette activité est généralement réalisée par une personne chargée de l’intégration Audio/Vidéo.

À mesure que la date du déploiement du réseau de signalétique digitale se rapproche, créez un plan de test et d’assurance qualité qui porte sur chaque élément du réseau, notamment l’ensemble des composants matériels, logiciels et réseau.
Au cours de cette phase, des systèmes de test complets doivent être mis au point et soumis à des tests exhaustifs.

Il convient de créer une liste de contrôle qui identifie tous les KPI définis précédemment et qui mesure les éléments livrables par rapport à ces indicateurs.

>[!NOTE]
>
>Cette phase doit également être utilisée comme outil pour créer un guide d’installation et d’utilisation. Les deux peuvent ensuite être livrés avec l’équipement et conservés sur site à des fins de référence ultérieure.

Les éléments suivants doivent être pris en compte :

## &#x200B;1. Considérations mécaniques {#mechanical-considerations}

Il est recommandé de tenir compte des facteurs mécaniques suivants :

* Montage des écrans
* Montage du lecteur
* Ventilation
* Accessoires périphériques
* Gestion des câbles
* Mise en réseau des appareils

## &#x200B;2. Considérations relatives aux logiciels {#software-considerations}

Il est recommandé de tenir compte des facteurs logiciels suivants :

* Enregistrement d’appareils
* Publication de médias
* Lecture
* Dépendances de base de données (définies précédemment)


## &#x200B;3. Considérations relatives à la gestion des appareils {#device-management-considerations}

AEM Screens dispose d’un module de centre de contrôle des appareils qui permet de gérer les points d’entrée de l’application du lecteur Screens.

Cela fait référence à tout appareil matériel de *lecture* sur lequel cette application est installée ; il est également enregistré sur une instance AEM.
Ce module vous permet d’effectuer les opérations suivantes :

1. Surveiller les journaux d’erreurs de l’application du lecteur
1. Gérer les captures d’écran distantes
1. Gérer les téléchargements de contenus
1. Gérer les problèmes de redémarrage de l’application

Pour en savoir plus sur le ***Centre de contrôle des appareils***, voir [Dépannage du Centre de contrôle des appareils](https://experienceleague.adobe.com/fr/docs/experience-manager-screens/user-guide/troubleshooting/monitoring-screens) dans le **Guide d’utilisation d’AEM Screens**.

>[!CAUTION]
>
>N’utilisez pas le Centre de contrôle des appareils pour effectuer ce qui suit :
>
>* installer de nouvelles versions de l’application du lecteur ;
>* surveiller les ressources système ;
>* résoudre des erreurs au niveau du système ;
>* autoriser une intervention à distance sur le poste de travail.


>[!NOTE]
>
> Adobe recommande d’utiliser des plateformes tierces dédiées de gestion des appareils pour tous les déploiements.

La plateforme spécifique choisie dépend de plusieurs facteurs, dont le ***système d&#39;exploitation cible***, les ***exigences du projet*** et le ***nombre de points d’entrée***.

Voici quelques exemples :

* Google Chrome Device Management
* TeamViewer
* AirWatch
* `42Gears`
* Middleware propriétaire de l’intégrateur ou intégratrice audiovisuel
