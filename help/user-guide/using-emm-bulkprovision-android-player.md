---
title: Utilisation de MDM ou EMM pour la fourniture en masse d'Android Player
seo-title: Approvisionnement en bloc du lecteur Android à l'aide d'EMM ou de MDM
description: Suivez cette page pour en savoir plus sur l'approvisionnement en bloc d'Android Player à l'aide d'EMM ou de MDM
translation-type: tm+mt
source-git-commit: 5f8938bfd092197391aefcd2d730d47fa06c214d
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---


# Approvisionnement en bloc du lecteur Android à l&#39;aide de la gestion de la mobilité d&#39;entreprise {#bulk-provisioning}

Lors du déploiement en bloc du lecteur Android, il devient fastidieux d’enregistrer manuellement chaque lecteur avec AEM. Il est vivement recommandé d&#39;utiliser une solution EMM (Enterprise Mobility Management) telle que VMWare Airwatch, MobileIron ou Samsung Knox pour configurer et gérer votre déploiement à distance. Le lecteur Android AEM Screens prend en charge la configuration Appconfig standard EMM pour permettre la mise en service à distance.

## Mise en oeuvre de l&#39;approvisionnement en bloc du lecteur Android à l&#39;aide de la gestion de la mobilité d&#39;entreprise {#implementation}

Suivez les étapes ci-dessous pour autoriser la mise en service en masse dans le lecteur Android :

1. Assurez-vous que votre périphérique Android prend en charge les services Google Play.
1. Inscrivez vos périphériques du lecteur Android à votre solution EMM préférée qui prend en charge Appconfig.
1. Connectez-vous à votre console EMM et extrayez l’application AEM Screens Player de Google Play.
1. Sélectionnez la configuration gérée (ou l’option associée).
1. Vous devriez maintenant voir une liste des options du lecteur qui peuvent être configurées (par exemple, le code d&#39;enregistrement en masse et le serveur).
1. Configurez ces paramètres et enregistrez et déployez la stratégie sur les périphériques.

   >[!NOTE]
   >Les périphériques doivent recevoir l&#39;application avec la configuration et pointer vers le serveur AEM approprié avec la configuration sélectionnée. Si vous choisissez de configurer le code d’enregistrement en bloc et que vous le conservez comme configuré dans AEM, le lecteur doit être en mesure de s’enregistrer automatiquement. Si vous avez configuré un affichage par défaut, il peut également télécharger et afficher un certain contenu par défaut (qui peut être modifié ultérieurement selon vos besoins).

En outre, vous devez vérifier auprès de votre fournisseur EMM sur la prise en charge d’AppConfig. Les plus populaires tels que [VMWare Airwatch](https://docs.samsungknox.com/admin/uem/vm-configure-appconfig.htm), [Mobile Iron](https://docs.samsungknox.com/admin/uem/mobileiron2-configure-appconfig.htm), [SOTI](https://docs.samsungknox.com/admin/uem/soti-configure-appconfig.htm), [Blackberry UEM](https://docs.samsungknox.com/admin/uem/bb-configure-appconfig.htm), [IBM Maas360](https://docs.samsungknox.com/admin/uem/ibm-configure-appconfig.htm) et [Samsung Knox&lt;a 11/> prend en charge cette norme industrielle.](https://docs.samsungknox.com/admin/uem/km-configure-appconfig.htm)


