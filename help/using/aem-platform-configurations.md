---
title: Configurations de plates-formes AEM
seo-title: Configurations de plates-formes AEM
description: Cette page décrit les configurations des plates-formes AEM
seo-description: Cette page décrit les configurations des plates-formes AEM
translation-type: ht
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: ht
source-wordcount: '522'
ht-degree: 100%

---

# Configurations de plates-formes AEM {#platform-configurations}

>[!NOTE]
>
>Cette activité est généralement réalisée par l’implémentateur d’AEM.

Suivez les instructions des sections ci-dessous pour configurer les plates-formes AEM afin de commencer à utiliser AEM Screens.

## Configurations serveur {#server-configurations}

Pour les configurations serveur, consultez la page [Configurations serveur](https://helpx.adobe.com/fr/experience-manager/6-5/screens/using/configuring-screens-introduction.html#ServerConfiguration).

## Création-Publication {#author-publish}

Pour configurer les serveurs de création et de publication, consultez la page [Configuration des instances de création et de publication dans AEM Screens](https://helpx.adobe.com/fr/experience-manager/6-5/screens/using/author-and-publish.html).

>[!NOTE]
>
>S’il n’existe qu’une seule instance de création et une seule instance de publication, vous devez suivre la procédure décrite à la section **Configuration des agents de réplication sur l’auteur** sur la page [Configuration des instances de création et de publication dans AEM Screens](https://helpx.adobe.com/fr/experience-manager/6-5/screens/using/author-and-publish.html).

## Configurations de Dispatcher {#dispatcher-configurations}

Le Dispatcher est l’outil de mise en cache et/ou d’équilibrage de charge d’Adobe Experience Manager. L’utilisation du Dispatcher AEM contribue également à protéger le serveur AEM contre les attaques. Vous pouvez donc accroître la sécurité de l’instance AEM en utilisant le Dispatcher conjointement à un serveur web de niveau élevé.

Rendez-vous sur la page **[Configurations du Dispatcher pour AEM Screens](https://helpx.adobe.com/fr/experience-manager/6-5/screens/using/dispatcher-configurations-aem-screens.html)**, où vous trouverez des instructions sur la configuration du Dispatcher pour un projet AEM Screens.

## Installation de FFMpeg et rendus vidéo {#installing-ffmpeg}

Installez FFMpeg en suivant les étapes relatives au système d’exploitation approprié (généralement RHEL) :

1. Si vous effectuez l’installation en activant EPEL et RPMFusion, vous pouvez installer tous les codecs gstreamer afin d’étendre la prise en charge aux conversions FFMpeg.
1. Si le codec AAC est marqué comme « expérimental », les conversions FFMpeg échoueront. Pour éviter cela, ajoutez -strict -2 aux profils vidéo (/etc/dam/video dans AEM 6.3 ; /libs/settings/dam/video dans AEM 6.4)
   >[!NOTE]
   >
   > Notez que -strict -2 doit être le dernier paramètre dans la liste des paramètres. Dans AEM 6.4, vous devez, en outre, copier les nœuds situés sous */libs/settings/dam/video* dans */conf/global/settings/dam/video*, comme indiqué sur la page [Rendus vidéo](https://helpx.adobe.com/fr/experience-manager/6-5/screens/using/generating-renditions.html).
1. Vérifiez que les conversions vidéo sont en cours d’exécution et que la création des rendus est en cours.

## Restrictions de mot de passe {#password-restrictions}

La stratégie de mot de passe d’AEM doit être désactivée sur l’instance AMS. Cela peut, par ailleurs, être configuré dans la console web à l’aide du service de périphérique de Screens *com.adobe.cq.screens.device.impl.DeviceService*.
Reportez-vous à la section **Restrictions relatives aux mots de passe** sur la page [Configuration des instances de création et de publication dans AEM Screens](https://helpx.adobe.com/fr/experience-manager/6-5/screens/using/author-and-publish.html).

## Configuration des environnements {#setting-up-environments}

Installez et exécutez les versions les plus récentes des packages suivants pour votre version d’Adobe Experience Manager (AEM) :

* AEM Service Pack
* Screens Feature Pack
* AEM Cumulative Fix Pack

Veuillez, en outre, identifier les packages de développement (les composants WCM Core, par exemple) ou les kits d’outils tiers (SAP Hybris, par exemple) qui sont éventuellement requis.
Installez les mêmes packages logiciels sur vos environnements de développement locaux. Demandez à votre client d’adopter la même configuration sur tous ses serveurs de contrôle de la qualité, de production et intermédiaires. Des configurations de serveur incohérentes entraîneront des problèmes lors des phases de déploiement et de test.

>[!NOTE]
>
>Pour installer la dernière version du Feature Pack pour AEM Screens, consultez les [Notes de mise à jour](https://helpx.adobe.com/fr/experience-manager/6-5/screens/user-guide.html?topic=/experience-manager/6-5/screens/morehelp/release-notes.ug.js).

## Configuration des listes de contrôle d’accès {#setting-up-acls}

Cette section explique comment séparer les projets, de sorte que chaque  personne ou équipe gère son propre projet.

Pour en savoir plus, voir [Configuration des listes de contrôle d’accès](https://helpx.adobe.com/fr/experience-manager/6-5/screens/using/setting-up-acls.html).
