---
title: Transition de ContentSync à SmartSync
description: Découvrez cette fonctionnalité SmartSync et comment migrer de ContentSync à SmartSync.
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
content-type: reference
docset: aem65
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: b8d0c089-af79-403e-870f-fb46b66fecd3
source-git-commit: 6b4fc934c31640168528fa3e72cf634773f4f8e6
workflow-type: ht
source-wordcount: '443'
ht-degree: 100%

---

# Transition de ContentSync à SmartSync {#transitioning-from-contentsync-to-smartsync}

Cette section présente la fonctionnalité SmartSync et explique comment elle minimise la charge/le stockage du serveur et le trafic réseau afin de réduire les coûts.

## Vue d’ensemble {#overview}

SmartSync est le tout dernier mécanisme utilisé par AEM Screens. Il remplace la méthode actuelle utilisée pour mettre en cache les canaux hors ligne et les diffuser au lecteur.

Il s’exécute à la fois côté serveur et côté client.

**Côté serveur**

* Le contenu des canaux, incluant les ressources, est mis en cache dans *`/var/contentsync`*.
* Le cache est exposé aux lecteurs via un manifeste qui décrit le contenu disponible pour un affichage.

**Côté client**

* Le lecteur met à jour son contenu en fonction du manifeste généré ci-dessus.

### Avantages de SmartSync {#benefits-of-using-smartsync}

La fonctionnalité SmartSync offre plusieurs avantages à votre projet AEM Screens, tels que :

* Une réduction considérable du trafic réseau et des besoins de stockage côté serveur.
* Le lecteur télécharge de manière intelligente les ressources uniquement si la ressource est manquante ou a été modifiée.
* Des optimisations du stockage côté serveur et côté client.

>[!NOTE]
>
>Adobe recommande vivement d’utiliser SmartSync pour les projets AEM Screens.

## Migration de ContentSync vers SmartSync {#migrating-from-contentsync-to-smartsync}

>[!NOTE]
>
>Si vous avez déjà installé AEM 6.3 Feature Pack 5 et AEM 6.4 Feature Pack 3, vous pouvez activer SmartSync pour les ressources afin d’améliorer l’utilisation de l’espace disque. Pour activer SmartSync, consultez la section ci-dessous pour passer de ContentSync à SmartSync et activer ainsi SmartSync.
>
>SmartSync est disponible pour le lecteur Screens avec les serveurs AEM 6.4.3 FP3 pris en charge.
>
>Reportez-vous à la section [Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/) pour télécharger le dernier lecteur. Le tableau suivant décrit la version minimale du lecteur requise pour chaque plateforme :

| **Plateforme** | **Version minimale du lecteur prise en charge** |
|---|---|
| Android™ | 3.3.72 |
| Chrome OS | 1.0.136 |
| Windows | 1.0.136 |

Pour passer de ContentSync à SmartSync, procédez comme suit :

1. La migration de ContentSync vers SmartSync nécessite de vider le cache ContentSync avant d’activer SmartSync.

   Accédez à la console ContentSync à partir de votre instance à l’aide du lien ***https://localhost:4502/libs/cq/contentsync/content/console.html*** et cliquez sur **Effacer le cache**, comme illustré ci-dessous :

   ![clear_contesync_cache](assets/clear_contesync_cache.png)

   >[!CAUTION]
   >
   >Tout le cache de contenu doit être effacé avant d’utiliser SmartSync pour la première fois.

1. Accédez à la **Configuration de la console web Adobe Experience Manager** via Instance AEM > icône en forme de marteau > **Opérations** > **Console web**.

   ![screen_shot_2019-02-11at15339pm](assets/screen_shot_2019-02-11at15339pm.png)

1. La **configuration de la console web d’Adobe Experience Manager** s’ouvre. Recherchez *offlinecontentservice*.

   Pour rechercher la propriété **Services de contenu hors ligne Screens**, appuyez sur **Commande+F** pour **Mac** et **Ctrl+F** pour **Windows**.

   ![screen_shot_2019-02-19at22643pm](assets/screen_shot_2019-02-19at22643pm.png)

1. Cliquez sur **Enregistrer** pour activer la propriété **Screens Offline Content Services** et, par conséquent, utiliser SmartSync pour AEM Screens.
1. Une fois que vous avez activé SmartSync, accédez à votre projet et cliquez sur **Mettre à jour le contenu hors ligne** *(dans la barre d’actions),* comme illustré ci-dessous.

   ![screen_shot_2019-02-25at102605am](assets/screen_shot_2019-02-25at102605am.png)
