---
title: Configurations de plateforme AEM
description: Cette page décrit les configurations d’AEM Platform
exl-id: cfe1769b-4da2-430d-a7b1-10dbcaf9f51b
TQID: https://experienceleague.adobe.com/qsJ-vj45WoTXXdBU5zsNQYoB7g4HnNTLwwfFSBL-wwI
product_v2:
  - id: a27b4747-2f72-4fb7-9936-be5d11dd2c4a
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 0b0bfcd803c3da9298122200a0a1715fc2d5e49c
workflow-type: tm+mt
source-wordcount: 545
ht-degree: 87%

---

# Configurations de plateforme AEM {#platform-configurations}

>[!NOTE]
>
>Cette activité est généralement réalisée par la personne chargée de l’implémentation d’AEM.

Commencez à utiliser AEM Screens en lisant les sections ci-dessous pour configurer les configurations de plateforme AEM.

## Configurations serveur {#server-configurations}

Pour les configurations serveur, consultez [Configurations serveur](https://experienceleague.adobe.com/fr/docs/experience-manager-screens/user-guide/administering/configuring-screens-introduction#ServerConfiguration).

## Création-Publication {#author-publish}

Voir [Configuration des instances de création et de publication dans AEM Screens](https://experienceleague.adobe.com/fr/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish).

>[!NOTE]
>
>S’il n’existe qu’une seule instance de création et de publication, vous devez suivre la procédure décrite à la section **Configuration des agents de réplication sur l’instance de création** sur la page [Configuration des instances de création et de publication dans AEM Screens](https://experienceleague.adobe.com/fr/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish).

## Configurations de Dispatcher {#dispatcher-configurations}

Dispatcher est l’outil de mise en cache et/ou d’équilibrage de charge d’Adobe Experience Manager. L’utilisation du Dispatcher AEM contribue également à protéger le serveur AEM contre les attaques. Vous pouvez donc accroître la sécurité de l’instance AEM en utilisant le Dispatcher avec un serveur web de niveau entreprise.

Consultez **[Configurations de Dispatcher pour AEM Screens](https://experienceleague.adobe.com/fr/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens)**, où vous trouverez des instructions sur la configuration de Dispatcher pour un projet AEM Screens.

## Installation de FFMpeg et rendus vidéo {#installing-ffmpeg}

Installez FFMpeg en suivant les étapes relatives au système d’exploitation approprié (généralement RHEL) :

1. Si vous effectuez l’installation en activant EPEL et RPMFusion, vous pouvez installer tous les codecs gstreamer afin d’étendre la prise en charge aux conversions FFMpeg.
1. Si le codec AAC est marqué comme « expérimental », les conversions FFMpeg échouent. Pour éviter ce problème, ajoutez des `-strict -2` aux profils vidéo (`/etc/dam/video` dans AEM 6.3 et déplacés vers `/libs/settings/dam/video in AEM 6.4`)

   >[!NOTE]
   >
   >`-strict -2` doit être le dernier paramètre de la liste des paramètres. Dans AEM 6.4, vous devez, en outre, copier les nœuds situés sous */libs/settings/dam/video* dans */conf/global/settings/dam/video* , comme indiqué dans les [Rendus vidéo](https://experienceleague.adobe.com/fr/docs/experience-manager-screens/user-guide/authoring/product-features/generating-renditions).
1. Vérifiez que les conversions vidéo sont en cours d’exécution et que la création des rendus est en cours.

## Restrictions relatives aux mots de passe {#password-restrictions}

La politique de mot de passe d’AEM doit être désactivée sur l’instance AMS. Il peut également être configuré dans la console web à l’aide du service d’appareil Screens *com.adobe.cq.screens.device.impl.DeviceService*
Voir la section **Restrictions de mot de passe** dans [&#x200B; Configuration de l’auteur et de la publication dans AEM Screens](https://experienceleague.adobe.com/fr/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish)

## Configuration des environnements {#setting-up-environments}

Installez et exécutez les versions les plus récentes des packages suivants pour votre version d’Adobe Experience Manager (AEM) :

* AEM Service Pack
* Screens Feature Pack
* AEM Cumulative Fix Pack

En plus de ce qui précède, identifiez tous les packages de développement (par exemple, WCM Core
composants) ou de kits d’outils tiers (par exemple, SAP Hybris) qui sont requis.
Installez les mêmes packages logiciels sur votre environnement de développement local. Demandez à votre client ou cliente d’adopter la même configuration sur tous ses serveurs de contrôle de la qualité, de production et intermédiaires. Des configurations de serveur incohérentes entraîneront des problèmes lors des phases de déploiement et de test.

>[!NOTE]
>
>Pour installer la dernière version du pack de fonctionnalités pour AEM Screens, consultez les [Notes de mise à jour](https://experienceleague.adobe.com/fr/docs/experience-manager-screens/user-guide/aem-screens-introduction).

## Configuration des listes de contrôle d’accès {#setting-up-acls}

Cette section explique comment séparer les projets, de sorte que chaque personne ou équipe gère son propre projet.

Pour en savoir plus, voir [Configuration des listes de contrôle d’accès](https://experienceleague.adobe.com/fr/docs/experience-manager-screens/user-guide/administering/setting-up-acls).
