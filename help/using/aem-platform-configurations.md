---
title: Configurations de plateformes AEM
seo-title: Configurations de plateformes AEM
description: La page décrit les configurations de plateformes AEM
seo-description: La page décrit les configurations de plateformes AEM
translation-type: tm+mt
source-git-commit: 5c83a2b59769dfd3736a830f7d7d3cc35137c182

---

# Configurations de plateformes AEM {#platform-configurations}

>[!NOTE]
>
>L’intervenant typique de cette activité est un implémenteur AEM.

Suivez les sections ci-dessous pour configurer les configurations de plateformes AEM afin de commencer à utiliser les écrans AEM.

## Server Configurations {#server-configurations}

Pour configurer des configurations de serveur, reportez-vous à la section Configurations [de](https://helpx.adobe.com/experience-manager/6-5/screens/using/configuring-screens-introduction.html#ServerConfiguration)serveur.

## Auteur-Publication {#author-publish}

Pour configurer la fonction de création-publication, reportez-vous à la section [Configuration de l’auteur et de la publication dans les écrans AEM](https://helpx.adobe.com/experience-manager/6-5/screens/using/author-and-publish.html)

>[!NOTE]
>
> S’il n’existe qu’un seul auteur et qu’une seule publication, vous devez suivre les étapes de la section **Configuration des agents de réplication sur l’auteur** dans [Configuration de l’auteur et de la publication dans les écrans](https://helpx.adobe.com/experience-manager/6-5/screens/using/author-and-publish.html) AEM.

## Configurations du dispatcher{#dispatcher-configurations}.

Dispatcher est l’outil de mise en cache et/ou d’équilibrage de charge d’Adobe Experience Manager. L’utilisation de Dispatcher AEM contribue également à protéger le serveur AEM contre les attaques. Par conséquent, vous pouvez augmenter la sécurité de l’instance AEM en utilisant Dispatcher conjointement à un serveur web de niveau élevé.

Reportez-vous à la section Configurations du **[répartiteur pour AEM Screens](https://helpx.adobe.com/experience-manager/6-5/screens/using/dispatcher-configurations-aem-screens.html)** qui décrit les instructions de configuration du répartiteur pour un projet AEM Screens.

## Installation de FFMpeg et de rendus vidéo {#installing-ffmpeg}

Installez FFMpeg en suivant les étapes du système d'exploitation approprié (généralement RHEL) :

1. Si vous effectuez l’installation en activant EPEL et RPMFusion, vous pouvez installer tous les codecs gstreaming pour étendre la prise en charge des conversions FFmpeg.
1. Si le codec AAC est marqué comme expérimental, les conversions ffmpeg échouent. Pour éviter cette opération, ajoutez -strict -2 aux profils vidéo (/etc/dam/video dans AEM 6.3 et passez à /libs/settings/dam/video dans AEM 6.4)
   >[!NOTE]
   >
   > Veuillez noter que -strict -2 doit être le dernier paramètre de la liste des paramètres. De plus, dans AEM 6.4, vous devez copier les noeuds sous */libs/settings/dam/video* dans */conf/global/settings/dam/video* , comme indiqué dans Rendus [vidéo](https://helpx.adobe.com/experience-manager/6-5/screens/using/generating-renditions.html).
1. Vérifiez que des conversions vidéo sont en cours et que des rendus sont créés.

## Restrictions de mot de passe {#password-restrictions}

La stratégie de mot de passe d’AEM doit être désactivée sur l’instance AMS. Vous pouvez également le configurer dans la console Web à l’aide du service de périphérique Screens *com.adobe.cq.screens.device.impl.DeviceService* Reportez-vous à la section Restrictions **de** mot de passe[dans Configuration de l’auteur et de la publication dans AEM Screens.](https://helpx.adobe.com/experience-manager/6-5/screens/using/author-and-publish.html)

## Setting up the Environments {#setting-up-environments}

Installez et exécutez les versions les plus récentes des packages suivants pour votre version d’Adobe Experience Manager (AEM) :

* AEM  Service Pack 
* Capture d'écran
* AEM  Cumulative Fix Pack

Outre ce qui précède, identifiez les packages de développement (par exemple, les composants WCM) ou les kits d’outils tiers (par exemple, SAP Hybris) qui sont requis.
Installez les mêmes packs logiciels sur vos environnements de développement local. Demandez à votre client d’adopter la même configuration sur tous ses serveurs d’assurance qualité, d’évaluation et de production. Des configurations de serveur incohérentes créeront des problèmes lors du déploiement et du test.

>[!NOTE]
> Pour installer la dernière version du Pack de fonctionnalités pour les écrans AEM, reportez-vous aux Notes [de](https://helpx.adobe.com/experience-manager/6-5/screens/user-guide.html?topic=/experience-manager/6-5/screens/morehelp/release-notes.ug.js)mise à jour.

## Configuration des listes de contrôle d’accès {#setting-up-acls}

La configuration des listes de contrôle d’accès explique comment séparer les projets afin que chaque individu ou équipe gère son propre projet.

Consultez [Configuration des listes de contrôle d’accès](https://helpx.adobe.com/experience-manager/6-5/screens/using/setting-up-acls.html) pour plus d’informations.
