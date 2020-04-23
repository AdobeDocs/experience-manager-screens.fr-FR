---
title: Mise à jour de contenu à l’aide du lancement d’écrans
seo-title: Mise à jour de contenu à l’aide du lancement d’écrans
description: Les auteurs de contenu peuvent créer une version ultérieure du ou des canaux, connue sous le nom de Lancement, et la définition de la date d’activation de ce canal permet au contenu d’être en ligne sur les périphériques ou lecteurs.
seo-description: Les auteurs de contenu peuvent créer une version ultérieure du ou des canaux, connue sous le nom de Lancement, et la définition de la date d’activation de ce canal permet au contenu d’être en ligne sur les périphériques ou lecteurs.
uuid: fb13117c-b99b-48bd-adb6-040dbd13af16
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
discoiquuid: 9cd8892b-fe5d-4ad3-9b10-10ff068adba6
docset: aem65
translation-type: tm+mt
source-git-commit: 14a45b58862477ec6be082ab1c059f991b086755

---


# Mise à jour de contenu à l’aide du lancement d’écrans {#launches}

Les auteurs de contenu peuvent créer une future version du ou des (s), connue sous le nom de **lancement** d’écrans, et définir plus avant la date d’activation de ce lancement. Cela permet au contenu d’être en ligne sur des périphériques ou des lecteurs à la date de production spécifiée.

With the help of **Screens Launches**, authors can preview each channel in the launch and should be able to initiate a request for review. Le groupe des approbateurs reçoit une notification et peut approuver ou rejeter la demande. Lorsque la date d’activation est atteinte, le contenu est lu sur les périphériques.

Par exemple, si l’auteur souhaite créer des versions futures de c1, c2 (canaux), un lancement est créé et une date d’activation est définie (par exemple, le 10 novembre à 8 heures). Toute mise à jour ultérieure du contenu est envoyée pour révision. Une fois approuvé, ce lancement lira à la date d’activation (10 novembre, 8 h) le contenu sur les périphériques ou lecteurs.

## Conditions requises {#requirements}

Avant de  tirer parti des lancements d’écrans dans un projet AEM Screens, assurez-vous de bien comprendre le concept de la période de grâce et sa pertinence.

L’exécution d’une expérience à la date définie sur le lecteur implique :

* promotion du lancement (en général, quelques secondes)

* la publication des ressources pour publier des instances (en général, cela prend quelques minutes, selon la taille du ou des ressources à publier)

* temps nécessaire à l’exécution de la mise à jour du contenu hors ligne (en général, il faut quelques minutes)

* le temps nécessaire par les lecteurs pour télécharger le contenu à partir de l’instance de publication (en général, cela prend des minutes en fonction de la bande passante et de la taille des ressources à télécharger).

* toutes les différences de temps entre le serveur et le lecteur

### Présentation de la période de grâce {#understanding-grace-period}

Pour que le joueur puisse de lire le contenu à la date d’activation définie, nous devons  lejeu de la  avant la date d’activation.

Si la date d’activation est le 24 *novembre, 9:00 et que la période de grâce est de* 24 heures **, la séquence d’actions ci-dessus  à (date d’activation - période de grâce), c’est-à-dire le 23 novembre, 9:00 heure du serveur. Cela donne 24 heures pour terminer toutes les actions mentionnées ci-dessus et le contenu atteindra les joueurs. Les joueurs comprendront qu’il s’agit d’un contenu de lancement, de sorte que le contenu ne sera pas lu immédiatement, mais les lecteurs stockeront ce contenu comme une version ultérieure et de  de lecture exactement à la date de mise en service définie sur le fuseau horaire du lecteur.

Par exemple, supposons que le serveur utilisent le fuseau horaire PST et les périphériques le fuseau horaire EST, que la différence de temps maximale est de 3 heures dans ce cas et supposons que la promotion durera 1 minute, que la publication de l’auteur à la publication prend 10 minutes et que le lecteur peut généralement télécharger les ressources en 10-15 minutes. Ensuite, période de grâce = écart de  l’heure (3 heures) + temps pour promouvoir le lancement (1 min) + temps pour publier le lancement (10 min) + temps pour télécharger au lecteur (10-15 min) + mémoire tampon (pour être sûr, disons 30 min) = 3 heures 56 min = 14160 secondes. Ainsi, lorsque nous planifions un lancement en direct, la promotion commence tôt en fonction de ce délai (décalage). Dans l&#39;équation ci-dessus, la plupart des éléments ne prennent pas beaucoup de temps, nous pouvons utiliser une estimation correcte de ce décalage à condition de connaître l’écart maximal de l’heure entre le serveur et n&#39;importe quel lecteur.

>[!NOTE]
>Out-of-the-box, the grace period for screens launches is set to 24 hours which means that when we set live date for any launch for the resources under */content/screens*, the promotion will start with this offset.

### Updating out-of-the-box Grace Period {#updating-out-of-the-box-grace-period}

Cette section explique comment mettre à jour une période de grâce prête à l’emploi sur 10 minutes :

1. Accédez à CRXDE Lite, puis à `/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`.
2. Cliquez avec le bouton droit de la souris et copiez le fichier.
3. Accédez à `/apps/system/config` et cliquez avec le bouton droit de la souris et collez.
4.  cliquez sur `/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config` pour ouvrir le fichier dans l’éditeur de CRXDE Lite. Il doit afficher la période de grâce du chemin */content/screens/* sur 86400. Remplacez cette valeur par **600**.

Le contenu du fichier texte doit maintenant ressembler à :

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

Puisque vous avez défini la période de grâce sur 10 minutes dans l’exemple précédent, lorsque vous définissez la date de lancement pour les ressources sous */content/screens*, la promotion  avec ce décalage.

Si, par exemple, la date d’activation est définie sur 24 novembre, 9:00 et que la période de grâce est de 600 secondes, la tâche de promotion  le 24 novembre à 8:50.

## Utilisation du lancement d’écrans {#using-launches}

Suivez la section ci-dessous pour implémenter les lancements dans votre projet AEM Screens. Cette section traite des sujets suivants :

1. **Création d’un lancement d’écran**
1. **Modification d’un lancement d’écran pour définir la date et l’étendue d’activation**

### Creating a Screens Launch {#creating-a-launch}

Suivez les étapes ci-dessous pour mettre en oeuvre la fonctionnalité de lancements dans votre projet AEM Screens :

1. Create a sequence channel in your AEM Screens project, for example **LaunchesDemo** --> **Channels** --> **FutureLaunch**, as shown below.

   >[!CAUTION]
   >
   >Vous devez créer un lancement à partir d’un canal préexistant dans votre projet AEM Screens.

   ![Image](/help/user-guide/assets/launches-images/launches-11.png)

1. Select the channel **FutureLaunch** and click **Create Launch** from the action bar.

   ![Image](/help/user-guide/assets/launches-images/launches-12.png)

1. L’assistant **Créer un lancement** s’ouvre. Vous pouvez soit sélectionner le  de déjà visible dans l’assistant, soit cliquer sur **+ Ajouter** pour ajouter le pour lequel vous souhaitez créer le lancement.


#### Utilisation du existant {#existing-channel-launch}

1. Sélectionnez le  qui existe déjà dans l’assistant **Créer un lancement** et cliquez sur **Suivant**.

   ![image](/help/user-guide/assets/launches-images/launches-b.png)

1. Select the channel and click **Next** from the action bar.

   >[!NOTE]
   >**L’option Inclure les sous-pages** est sélectionnée par défaut.

   ![Image](/help/user-guide/assets/launches-images/launches-b.png)

1. Saisissez le **Titre du lancement** **SummerPromotions** et vous n’aurez pas besoin de définir la **Date de lancement**, comme illustré dans la figure ci-dessous. Cliquez sur **Créer**.

   >[!NOTE]
   >
   >*Activer ou cocher* l’option **Hériter les données dynamiques de la page source** permet de créer les canaux en tant que copies dynamiques au lancement. Si des modifications sont apportées au canal d’origine, elles sont automatiquement appliquées aux canaux de lancement.
   >
   >
   >*Désactiver ou décocher* Hériter les données dynamiques de la page source **** permet de copier les canaux sans aucune relation active au lancement. Ainsi, si des modifications sont apportées au canal d’origine, elles ne sont pas appliquées aux canaux de lancement.

   ![Image](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >Vous pouvez définir la date de lancement en direct dans cette étape ou la configurer ultérieurement lors de la modification des propriétés du lancement une fois qu’il a déjà été créé.

1. Vous verrez que votre lancement est créé. Vous pouvez cliquer sur **Ouvrir** pour afficher les pages dans l’éditeur ou sur **Terminé** pour revenir à votre projet.

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   Clicking **Done** allows you to navigate back to your **FutureLaunch** channel.

   ![Image](/help/user-guide/assets/launches-images/launches-16.png)


#### Utilisation de l’option Ajouter {#add-channel-launch}

1. Cliquez sur **+ Ajouter** pour ajouter le  pour lequel vous souhaitez créer le lancement.

   ![image](/help/user-guide/assets/launches-images/launches-13.png)

   >[!NOTE]
   >L’option **Sélectionner** est désactivée si vous essayez de sélectionner plusieurs  de ou un dossier pour ajouter le lancement.

1. Accédez au pour lequel vous souhaitez créer le lancement, puis cliquez sur **Sélectionner**.

   ![image](/help/user-guide/assets/launches-images/launches-14.png)

1. Vous pouvez maintenant sélectionner le pour lequel vous avez ajouté un lancement et cliquer sur **Suivant**.

   ![image](/help/user-guide/assets/launches-images/launches-15.png)

1. Saisissez le **Titre du lancement** **SummerPromotions** et vous n’aurez pas besoin de définir la **Date de lancement**, comme illustré dans la figure ci-dessous. Cliquez sur **Créer**.

   >[!NOTE]
   >
   >*Activer ou cocher* l’option **Hériter les données dynamiques de la page source** permet de créer les canaux en tant que copies dynamiques au lancement. Si des modifications sont apportées au canal d’origine, elles sont automatiquement appliquées aux canaux de lancement.
   >
   >
   >*Désactiver ou décocher* Hériter les données dynamiques de la page source **** permet de copier les canaux sans aucune relation active au lancement. Ainsi, si des modifications sont apportées au canal d’origine, elles ne sont pas appliquées aux canaux de lancement.

   ![Image](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >Vous pouvez définir la date de lancement en direct dans cette étape ou la configurer ultérieurement lors de la modification des propriétés du lancement une fois qu’il a déjà été créé.

1. Vous verrez que votre lancement est créé. Vous pouvez cliquer sur **Ouvrir** pour afficher les pages dans l’éditeur ou sur **Terminé** pour revenir à votre projet.

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   Clicking **Done** allows you to navigate back to your **FutureLaunch** channel.

   ![Image](/help/user-guide/assets/launches-images/launches-16.png)

### Modification des propriétés de lancement pour définir la date et la portée d’activation {#editing-the-launch-properties-to-set-the-live-date-and-scope}

Après avoir créé le lancement, vous devez modifier les propriétés de lancement pour définir la date d’activation et la portée du lancement.

Pour modifier les propriétés de lancement, procédez comme suit :

1. Accédez au  **FutureLaunch***,* (c’est le lancement en attente)et sélectionnez le  de, comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/launches-images/launches-17.png)

1. Cliquez sur **de** à partir de la barre d&#39;action et vous verrez le panneau LANCEMENTS **** EN ATTENTE à partir de la  de.

   ![image](/help/user-guide/assets/launches-images/launches-18.png)

1. Sélectionnez le lancement, puis cliquez sur l’une des actions de votre choix dans le panneau **LANCEMENTS** EN ATTENTE.

   ![image](/help/user-guide/assets/launches-images/launches-19.png)

1. Par exemple, vous cliquez sur **Propriétés** de lancement pour modifier les propriétés des promotions **d’**&#x200B;été de lancement.

   ![image](/help/user-guide/assets/launches-images/launches-20.png)

1. Vous pouvez modifier le titre **du** Luanch et renseigner les champs suivants :

   * Sélectionner la **Date de lancement**
   * Cocher **Prêt pour production**
   * Sélectionnez **Promouvoir les pages** approuvées dans **Portée**
   **Présentation des entrées Lancements sous Promotion automatique :**

   * **Date de lancement**, fait référence à la date d’activation, c’est-à-dire la date/l’heure de lecture du contenu dans le lecteur Screens selon le fuseau horaire du lecteur.
   * **Prêt pour production** permet de promouvoir les canaux et signifie que le lancement est prêt à être utilisé.
   * **Portée** fait référence aux canaux qui peuvent être promus lors d’un lancement.
   Les trois options suivantes sont disponibles pour configurer la portée :

   * **Promouvoir le lancement complet** : tous les canaux du lancement sont promus à la date d’activation définie.
   * **Promouvoir les pages modifiées** : seules les ressources de lancement modifiées seront promues. Il est recommandé d’utiliser cette option lorsque la révision du lancement n’est pas requise. Elle permet de promouvoir les modifications apportées aux canaux de lancement.
   * **Promouvoir les pages approuvées** : seules les pages approuvées sont promues à la date d’activation définie.

      >[!CAUTION]
      >
      >La promotion du lancement se conforme au fuseau horaire du lecteur/périphérique plutôt que celui du serveur.



1. Cliquez sur **Enregistrer et fermer** pour revenir au canal **FutureLaunch**.

