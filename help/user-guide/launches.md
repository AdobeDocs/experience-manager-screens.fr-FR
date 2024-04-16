---
title: Mise à jour du contenu à l’aide d’un lancement Screens
description: Découvrez comment créer une version ultérieure des canaux, connue sous le nom de Launch, et définir une date d’activation pour le lancement afin de rendre le contenu actif sur les appareils ou lecteurs.
contentOwner: jsyal
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
content-type: reference
topic-tags: authoring
docset: aem65
feature: Authoring Screens, Launches
role: Admin, Developer
level: Intermediate
exl-id: b610e5dd-e0c6-45e6-bf9b-27be2054bc8f
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '1556'
ht-degree: 31%

---

# Mise à jour du contenu à l’aide d’un lancement Screens {#launches}

Les auteurs de contenu peuvent créer une version ultérieure des canaux, appelée **Lancement Screens** et définissez ensuite la date d’activation de ce lancement. Le contenu est ainsi en ligne sur des appareils ou des lecteurs à la date d’activation spécifiée.

Grâce au ***lancement Screens***, les auteurs peuvent prévisualiser chaque canal du lancement et doivent être en mesure de lancer une demande de révision. Le groupe des approbateurs reçoit une notification et peut approuver ou rejeter la demande. Lorsque la date d’activation est atteinte, le contenu est lu sur les appareils.

Par exemple, si l’auteur souhaite créer des versions futures de c1, c2 (canaux), un lancement est créé et une date d’activation est définie (par exemple, le 10 novembre à 8 heures). Toute mise à jour supplémentaire du contenu est envoyée pour révision.

Après approbation et à la date d’activation (10 novembre à 8 heures), ce lancement lit le contenu sur les appareils ou lecteurs.

## Conditions requises {#requirements}

Avant de commencer à utiliser *Lancement Screens* dans un projet AEM Screens, veillez à bien comprendre le concept de période de grâce et sa pertinence.

L’exécution d’une expérience sur le lecteur à la date d’activation définie implique :

* Promotion du lancement (qui prend généralement quelques secondes).

* La publication des ressources pour publier des instances (cela prend généralement quelques minutes, selon la taille des canaux ou des ressources à publier).

* Temps nécessaire à l’achèvement de la mise à jour du contenu hors ligne (généralement quelques minutes).

* Temps nécessaire aux lecteurs pour télécharger le contenu à partir de l’instance de publication (cela prend généralement des minutes en fonction de la bande passante et de la taille des ressources à télécharger).

* Différences en tout temps entre le serveur et le lecteur.

### Présentation de la période de grâce {#understanding-grace-period}

Pour que le lecteur puisse lire le contenu à la date d’activation définie, démarrez les activités précédentes avant la date d’activation.

Si la date d’activation est *24 novembre à 9 heures* et la période de grâce est *24 heures*, la séquence d’actions ci-dessus démarrera à (date d’activation - période de grâce), c’est-à-dire le 23 novembre à 9h00 (heure du serveur). Cela donne 24 heures pour terminer toutes les actions mentionnées ci-dessus pour que le contenu atteigne les lecteurs. Les lecteurs comprennent qu’il s’agit d’un contenu de lancement. Par conséquent, le contenu n’est pas lu immédiatement, mais les lecteurs peuvent stocker ce contenu en tant que version ultérieure et le faire lire exactement à la date d’activation définie sur le fuseau horaire du lecteur.

Par exemple, le serveur est en PST et les périphériques en EST. Dans ce cas, la différence de temps maximale est de trois heures. Elle suppose que la promotion prend 1 minute et que la publication de l’auteur à la publication prend 10 minutes et que le lecteur peut généralement télécharger les ressources en 10 à 15 minutes. Ensuite, la période de grâce = décalage horaire (trois heures) :

* Plus de temps pour promouvoir le lancement (1 minute)
* Plus de temps pour publier le lancement (10 minutes)
* Temps de téléchargement supplémentaire au lecteur (10 à 15 minutes)
* Plus de mémoire tampon (30 minutes)

Est égal à 3 heures 56 minutes (14 160 secondes).

Ainsi, chaque fois que vous planifiez un lancement actif, la promotion commence tôt en fonction de ce décalage. Dans l’équation ci-dessus, la plupart des éléments ne prennent pas beaucoup de temps. Vous pouvez utiliser une estimation correcte de ce décalage lorsque vous connaissez la différence de temps maximale entre le serveur et n’importe quel lecteur.

>[!NOTE]
>
>Par défaut, la période de grâce du lancement Screens est définie sur 24 heures. Cela signifie que lorsque vous définissez la date d’activation d’un lancement pour les ressources sous */content/screens*, la promotion commence avec ce décalage.

### Mise à jour de la période de grâce par défaut {#updating-out-of-the-box-grace-period}

Cette section explique comment redéfinir la période de grâce par défaut sur 10 minutes.

1. Accédez à CRXDE Lite, puis à `/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`.
1. Cliquez avec le bouton droit de la souris et copiez le fichier.
1. Accédez à `/apps/system/config`, cliquez avec le bouton droit et collez.
1. Double-cliquez `/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config` vous pouvez donc ouvrir le fichier dans l’éditeur en CRXDE Lite. Il doit afficher la période de grâce du chemin */content/screens/* comme étant de **86 400**. Remplacez cette valeur par **600**.

Le contenu du fichier texte doit maintenant ressembler à :

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

Puisque vous avez défini la période de grâce sur 10 minutes dans l’exemple précédent, lorsque vous définissez la date d’activation d’un lancement pour les ressources sous */content/screens*, la promotion commence avec ce décalage.

Par exemple, si la date d’activation est définie sur 24 novembre à 9h00 et que la période de grâce est de 600 secondes, la tâche de promotion commence le 24 novembre à 8h50.

## Utilisation du lancement Screens {#using-launches}

Cette section explique comment mettre en œuvre le lancement Screens dans votre projet AEM Screens.

### Création d’un lancement Screens {#creating-a-launch}

Suivez les étapes ci-dessous pour mettre en œuvre la fonctionnalité de lancement Screens dans votre projet AEM Screens :

1. Créez un canal de séquence dans votre projet AEM Screens, par exemple **LaunchesDemo** > **Canaux** > **FutureLaunch**, comme illustré ci-dessous.

   >[!CAUTION]
   >
   >Créez un lancement à partir d’un canal préexistant dans votre projet AEM Screens.

   ![Image](/help/user-guide/assets/launches-images/launches-11.png)

1. Cliquez sur le canal **FutureLaunch** et cliquez sur **Créer un lancement** dans la barre d’actions.

   ![Image](/help/user-guide/assets/launches-images/launches-12.png)

1. L’assistant **Créer un lancement** s’ouvre. Vous pouvez cliquer sur le canal déjà visible dans l’assistant ou cliquer sur **+ Ajouter des canaux** pour ajouter le canal pour lequel vous souhaitez créer le lancement.

1. Cliquez sur **Suivant** dans l’assistant **Créer un lancement**. L’option **Inclure les sous-pages** est sélectionnée par défaut.

   ![image](/help/user-guide/assets/launches-images/launches-d.png)

   >[!NOTE]
   >Vous pouvez utiliser **+ Ajouter des canaux** pour ajouter un autre canal pour lequel vous souhaitez créer le lancement.

   Pour utiliser l’option **Ajouter un canal**, accédez au canal pour lequel vous souhaitez créer le lancement, puis cliquez sur **Sélectionner**.

   La variable **Sélectionner** est désactivée si vous essayez de cliquer sur plusieurs canaux ou sur un dossier pour ajouter le lancement.

   ![image](/help/user-guide/assets/launches-images/launches-14.png)

   Après avoir cliqué sur le ou les canaux, cliquez sur **Suivant**.


1. Saisissez le **Titre du lancement** **SummerPromotions** et vous n’aurez pas besoin de définir la **Date de lancement**, comme illustré dans la figure ci-dessous. Cliquez sur **Créer**.

   >[!NOTE]
   >
   >*Activer ou cocher* l’option **Hériter des données actives de la page source** permet de créer les canaux en tant que Live Copies dans le lancement. Si des modifications sont apportées au canal d’origine, elles sont automatiquement appliquées aux canaux de lancement.
   >
   >
   >*Désactivation ou désactivation* **Hériter des données actives de la page source** permet de copier les canaux sans aucune relation dynamique dans le lancement. Ainsi, si des modifications sont apportées au canal d’origine, elles ne sont pas appliquées aux canaux de lancement.

   ![Image](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >Vous pouvez définir la date de lancement dans cette étape ou la configurer ultérieurement lors de la modification des propriétés du lancement une fois qu’il a été créé.

   **Présentation de la portée de la promotion de lancement**

   * **Convertir le lancement complet** - Tous les canaux du lancement sont promus à la date d’activation définie.
   * **Promouvoir les pages modifiées** - Seules les ressources de lancement modifiées sont promues. Utilisez cette option lorsque la révision du lancement n’est pas requise.
   * **Promouvoir les pages approuvées** - Cette option nécessite que le workflow d’approbation du lancement s’exécute sur les canaux de lancement. Seules les pages approuvées sont promues à la date d’activation définie.

     >[!CAUTION]
     >
     >La date d’activation du lancement se conforme au fuseau horaire du lecteur/de l’appareil plutôt qu’à celui du serveur.

1. Notez que votre lancement est créé. Vous pouvez cliquer sur **Ouvrir** pour afficher les pages dans l’éditeur ou sur **Terminé** pour revenir à votre projet.

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   Sélection **Terminé** vous permet de revenir à la **FutureLaunch** canal.

   ![Image](/help/user-guide/assets/launches-images/launches-16.png)


### Modification des propriétés de lancement pour définir la date d’activation et la portée {#editing-the-launch-properties-to-set-the-live-date-and-scope}

Une fois le lancement créé, vous pouvez mettre à jour les propriétés telles que la date d’activation, le titre du lancement et la portée de la promotion à l’aide de la fonction **Propriétés de lancement**.

* **Date de lancement** - Date d’activation, c’est-à-dire la date ou l’heure de lecture du contenu dans le lecteur Screens selon le fuseau horaire du lecteur.
* **Prêt pour la production** - Permet de publier les canaux après les avoir promus, ce paramètre prêt à l’emploi étant activé, il n’est donc pas nécessaire de le modifier.
* **Portée** - Détermine les canaux qui sont promus pendant la promotion du lancement.

Pour modifier les propriétés de lancement, procédez comme suit :

1. Accédez au canal **FutureLaunch** *(lancement en attente)*, puis cliquez sur le canal comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/launches-images/launches-17.png)

1. Cliquez sur **Tableau de bord** à partir de la barre d’actions, le **LANCEMENTS EN ATTENTE** du tableau de bord des canaux.

   ![image](/help/user-guide/assets/launches-images/launches-18.png)

1. Cliquez sur le lancement, puis sur **Propriétés de lancement** de la **LANCEMENTS EN ATTENTE** du panneau.

   ![image](/help/user-guide/assets/launches-images/launches-19.png)

### Modification du lancement Screens pour ajouter ou supprimer des canaux  {#editing-the-screens-launch-to-add-or-remove-channels}

Après avoir créé le lancement, vous pouvez ajouter ou supprimer des canaux pour celui-ci à l’aide de l’option **Modifier le lancement**.

Lorsque vous avez terminé, cliquez sur **Enregistrer** pour revenir à **FutureLaunch** canal.

### Promotion manuelle du lancement Screens{#promote-the-screens-launch-manually}

Vous pouvez promouvoir le lancement manuellement à l’aide du **`Promote Launch`** de l’option **LANCEMENTS EN ATTENTE** du panneau.

Vous pouvez choisir les ressources que vous souhaitez promouvoir manuellement dans l’**Assistant Promotion du lancement**.

![image](/help/user-guide/assets/launches-images/launches-e.png)

1. Vous pouvez activer ou désactiver l’option de suppression du lancement après production.
1. Vous pouvez définir la variable **Portée** du lancement avec les options suivantes :
   * **Convertir le lancement complet** - Tous les canaux du lancement sont promus à la date d’activation définie.
   * **Promouvoir les pages modifiées** - Seules les ressources de lancement modifiées sont promues. Utilisez cette option lorsque la révision du lancement n’est pas requise.
   * **Promouvoir les pages approuvées** - Cette option nécessite que le workflow d’approbation du lancement s’exécute sur les canaux de lancement. Seules les pages approuvées sont promues à la date d’activation définie.
   * **Convertir la page active** - Cette option nécessite que le workflow d’approbation du lancement s’exécute uniquement pour la page active.
1. Cliquez sur **Suivant** dans l’assistant **Promotion du lancement**.
1. Cliquez sur **Promouvoir** pour promouvoir le lancement.

### Suppression du lancement Screens

Vous pouvez supprimer le lancement à l’aide de l’option **Supprimer le lancement** du panneau **LANCEMENTS EN ATTENTE**.

>[!CAUTION]
>
>Cette action supprime également tous les descendants (lancements imbriqués).
