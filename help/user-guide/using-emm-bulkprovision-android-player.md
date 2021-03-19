---
title: Utilisation d’une solution MDM ou EMM pour l’approvisionnement en bloc du lecteur Android
seo-title: Approvisionnement en bloc du lecteur Android à l’aide d’une solution EMM ou MDM
description: Rendez-vous sur cette page pour en savoir plus sur l’approvisionnement en bloc du lecteur Android à l’aide d’une solution EMM ou MDM
translation-type: ht
source-git-commit: 793507b266b99051544b377e4a7effb92dc6feb6
workflow-type: ht
source-wordcount: '334'
ht-degree: 100%

---


# Approvisionnement en bloc du lecteur Android à l’aide d’une solution Enterprise Mobility Management {#bulk-provisioning}

Lors du déploiement en bloc d’un lecteur Android, il devient fastidieux d’enregistrer manuellement chaque lecteur dans AEM. Nous vous recommandons vivement d’utiliser une solution EMM (Enterprise Mobility Management) telle que VMWare Airwatch, MobileIron ou Samsung Knox pour configurer et gérer votre déploiement à distance. Le lecteur Android AEM Screens prend en charge la norme EMM AppConfig pour permettre l’approvisionnement à distance.

## Mise en œuvre de l’approvisionnement en bloc du lecteur Android à l’aide d’une solution Enterprise Mobility Management {#implementation}

Suivez les étapes ci-dessous pour autoriser l’approvisionnement en bloc dans le lecteur Android Player :

1. Assurez-vous que votre périphérique Android prend en charge les services Google Play.
1. Enregistrez vos périphériques de lecteur Android dans votre solution EMM préférée prenant en charge AppConfig.
1. Connectez-vous à votre console EMM et extrayez l’application du lecteur AEM Screens de Google Play.
1. Sélectionnez Configuration gérée (ou l’option associée).
1. Vous devriez maintenant voir la liste des options du lecteur qui peuvent être configurées (par exemple, le code d’enregistrement en bloc et du serveur).
1. Configurez ces paramètres, enregistrez-les et déployez la stratégie sur les périphériques.

   >[!NOTE]
   >Les périphériques doivent recevoir l’application avec la configuration et pointer vers le serveur AEM approprié avec la configuration sélectionnée. Si vous choisissez de configurer le code d’enregistrement en bloc et que vous le conservez tel que configuré dans AEM, le lecteur doit être en mesure de s’enregistrer automatiquement. Si vous avez configuré un affichage par défaut, il peut également télécharger et afficher un certain contenu par défaut (qui peut être modifié ultérieurement selon vos besoins).

En outre, vous devez vérifier auprès de votre fournisseur de solution EMM si celle-ci prend AppConfig. Les plus populaires, parmi lesquels [VMWare Airwatch](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), [Mobile Iron](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm), [SOTI](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm), [Blackberry UEM](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm), [IBM Maas360](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm) et [Samsung Knox](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm), prennent en charge cette solution standard dans ce domaine.


