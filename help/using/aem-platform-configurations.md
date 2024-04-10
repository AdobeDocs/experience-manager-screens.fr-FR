---
title: Configurations d’AEM Platform
description: Cette page décrit les configurations d’AEM Platform
exl-id: cfe1769b-4da2-430d-a7b1-10dbcaf9f51b
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 44%

---

# Configurations d’AEM Platform  {#platform-configurations}

>[!NOTE]
>
>Cette activité est généralement réalisée par l’implémentateur d’AEM.

Commencez à utiliser AEM Screens en suivant les sections ci-dessous pour configurer AEM configurations de plateforme.

## Configurations de serveur {#server-configurations}

Pour configurer les configurations de serveur, voir [Configurations de serveur](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/configuring-screens-introduction#ServerConfiguration).

## Auteur-Publication {#author-publish}

Voir [Configuration de l’auteur et de la publication dans AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish).

>[!NOTE]
>
>S’il n’y a qu’un seul auteur et qu’une seule publication, vous ne suivez que les étapes de la section **Configuration des agents de réplication sur l’auteur** in [Configuration de l’auteur et de la publication dans AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish) page.

## Configurations du Dispatcher {#dispatcher-configurations}

Dispatcher est l’outil de mise en cache et d’équilibrage de charge Adobe Experience Manager. L’utilisation du Dispatcher AEM contribue également à protéger le serveur AEM contre les attaques. Vous pouvez donc accroître la sécurité de l’instance AEM en utilisant le Dispatcher avec un serveur web de niveau entreprise.

Voir **[Configurations de Dispatcher pour AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/dispatcher-configurations-aem-screens)** qui met en évidence les instructions de configuration de Dispatcher pour un projet AEM Screens.

## Installation de FFMpeg et rendus vidéo {#installing-ffmpeg}

Installez FFMpeg en suivant les étapes relatives au système d’exploitation approprié (généralement RHEL) :

1. Si vous effectuez l’installation en activant EPEL et RPMFusion, vous pouvez installer tous les codecs gstreamer afin d’étendre la prise en charge aux conversions FFMpeg.
1. Si le codec AAC est marqué comme expérimental, les conversions FFMpeg échouent. Pour éviter cela, ajoutez `-strict -2` aux profils vidéo (/etc/dam/video dans AEM 6.3 et déplacé vers /libs/settings/dam/video dans AEM 6.4)

   >[!NOTE]
   >
   >La variable `-strict -2` doit être le dernier paramètre de la liste des paramètres. En outre, dans AEM 6.4, vous devez copier les noeuds sous */libs/settings/dam/video* to */conf/global/settings/dam/video* comme mentionné dans [Rendus vidéo](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/authoring/product-features/generating-renditions).
1. Vérifiez que les conversions vidéo sont en cours d’exécution et que la création des rendus est en cours.

## Restrictions de mot de passe {#password-restrictions}

La stratégie de mot de passe de l’AEM doit être désactivée sur l’instance AMS. Vous pouvez également le configurer dans la console web à l’aide du service de périphérique Screens. *com.adobe.cq.screens.device.impl.DeviceService*
Voir **Restrictions de mot de passe** dans[Configuration de l’auteur et de la publication dans AEM Screens](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/author-publish/author-and-publish)

## Configuration des environnements {#setting-up-environments}

Installez et exécutez les versions les plus récentes des packages suivants pour votre version d’Adobe Experience Manager (AEM) :

* AEM Service Pack
* Screens Feature Pack
* AEM Cumulative Fix Pack

Veuillez, en outre, identifier les packages de développement (les composants WCM Core, par exemple) ou les kits d’outils tiers (SAP Hybris, par exemple) qui sont éventuellement requis.
Installez les mêmes packages logiciels sur votre environnement de développement local. Demandez à votre client d’adopter la même configuration sur tous ses serveurs de contrôle de la qualité, de production et intermédiaires. Des configurations de serveur incohérentes créent des problèmes lors du déploiement et du test.

>[!NOTE]
>
>Pour installer le dernier Feature Pack pour AEM Screens, voir [Notes de mise à jour](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/aem-screens-introduction).

## Configuration des listes de contrôle d’accès {#setting-up-acls}

Cette section explique comment séparer les projets, de sorte que chaque personne ou équipe gère son propre projet.

Pour en savoir plus, voir [Configuration des listes de contrôle d’accès](https://experienceleague.adobe.com/en/docs/experience-manager-screens/user-guide/administering/setting-up-acls).
