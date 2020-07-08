---
title: Mise à jour du contenu à l’aide d’un lancement Screens
seo-title: Mise à jour du contenu à l’aide d’un lancement Screens
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
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: tm+mt
source-wordcount: '1617'
ht-degree: 100%

---


# Mise à jour du contenu à l’aide d’un lancement Screens {#launches}

Les auteurs de contenu peuvent créer une version ultérieure du ou des canaux, connue sous le nom de **lancement Screens**, et en définir la date d’activation. Le contenu est ainsi en ligne sur des appareils ou des lecteurs à la date d’activation spécifiée.

Grâce au ***lancement Screens***, les auteurs peuvent prévisualiser chaque canal du lancement et doivent être en mesure de lancer une demande de révision. Le groupe des approbateurs reçoit une notification et peut approuver ou rejeter la demande. Lorsque la date d’activation est atteinte, le contenu est lu sur les périphériques.

Par exemple, si l’auteur souhaite créer des versions futures de c1, c2 (canaux), un lancement est créé et une date d’activation est définie (par exemple, le 10 novembre à 8 heures). Toute mise à jour ultérieure du contenu est envoyée pour révision.

Une fois approuvé, ce lancement lira à la date d’activation (10 novembre, 8 h) le contenu sur les périphériques ou lecteurs.

## Conditions requises {#requirements}

Avant de commencer à utiliser des *lancements Screens* dans un projet AEM Screens, veillez à bien comprendre le concept de période de grâce et sa pertinence.

L’exécution d’une expérience sur le lecteur à la date d’activation définie implique :

* la promotion du lancement (ne prend en général que quelques secondes) ;

* la publication des ressources sur les instances de publication (cela prend généralement quelques minutes, selon la taille des canaux ou ressources à publier) ;

* le temps nécessaire à l’exécution de la mise à jour du contenu hors ligne (en général, il faut compter quelques minutes) ;

* le temps pris par les lecteurs pour télécharger le contenu à partir de l’instance de publication (cela prend généralement plusieurs minutes en fonction de la bande passante et de la taille des ressources à télécharger) ;

* les éventuels décalages horaires entre serveur et lecteur.

### Présentation de la période de grâce {#understanding-grace-period}

Pour que le lecteur puisse lire le contenu à la date d’activation définie, nous devons démarrer les activités précédentes avant cette date.

Si la date d’activation est le *24 novembre à 9 h 00* et que la période de grâce est de *24 heures*, la séquence d’actions ci-dessus débutera à (date d’activation - période de grâce), c’est-à-dire le 23 novembre à 9 h 00 (heure du serveur). Cela laisse 24 heures pour terminer toutes les actions figurant ci-dessus de façon à ce que le contenu atteigne les lecteurs. Les lecteurs comprendront qu’il s’agit d’un contenu de lancement, de sorte qu’il ne sera pas lu immédiatement, mais ils le stockeront comme une version ultérieure et commenceront à le lire exactement à la date d’activation définie dans le fuseau horaire du lecteur.

Par exemple, supposons que le serveur utilisent le fuseau horaire PST et les appareils le fuseau horaire EST (la différence de temps maximale est de 3 heures dans ce cas) et supposons que la promotion durera 1 minute, que la publication de l’auteur à la publication prend 10 minutes et que le lecteur peut généralement télécharger les ressources en 10 à 15 minutes. Alors, période de grâce = décalage horaire (3 heures) + temps pour promouvoir le lancement (1 min) + temps pour publier le lancement (10 min) + temps pour télécharger sur le lecteur (10 à 15 min) + marge (pour être sûr, disons 30 min) = 3 heures 56 min = 14 160 secondes.

Ainsi, lorsque nous planifions un lancement, la promotion commencera plus tôt en fonction de ce décalage. Dans l’équation ci-dessus, la plupart des éléments ne prennent pas beaucoup de temps, nous pouvons obtenir une estimation raisonnable du décalage à condition de connaître le décalage horaire maximal entre le serveur et n’importe quel lecteur.

>[!NOTE]
>
>Par défaut, la période de grâce d’un lancement Screens est définie sur 24 heures, ce qui signifie que lorsque nous définissons la date d’activation de n’importe quel lancement pour les ressources sous */content/screens*, la promotion commence avec ce décalage.

### Mise à jour de la période de grâce par défaut {#updating-out-of-the-box-grace-period}

Cette section explique comment redéfinir la période de grâce par défaut sur 10 minutes.

1. Accédez à CRXDE Lite, puis à `/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`.
2. Cliquez avec le bouton droit et copiez le fichier.
3. Accédez à `/apps/system/config`, cliquez avec le bouton droit et collez.
4.  Double-cliquez sur `/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config` pour ouvrir le fichier dans l’éditeur de CRXDE Lite. Il doit afficher la période de grâce du chemin */content/screens/* comme étant de **86 400**. Remplacez cette valeur par **600**.

Le contenu du fichier texte doit maintenant ressembler à :

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

Puisque vous avez défini la période de grâce sur 10 minutes dans l’exemple précédent, lorsque vous définissez la date d’activation du lancement pour les ressources sous */content/screens*, la promotion démarrera avec ce décalage.

Si, par exemple, la date d’activation est définie sur le 24 novembre à 9 h 00 et que la période de grâce est de 600 secondes, la tâche de promotion démarrera le 24 novembre à 8 h 50.

## Utilisation du lancement Screens {#using-launches}

Cette section explique comment mettre en œuvre le lancement Screens dans votre projet AEM Screens.

### Création d’un lancement Screens {#creating-a-launch}

Suivez les étapes ci-dessous pour mettre en œuvre la fonctionnalité de lancement Screens dans votre projet AEM Screens :

1. Créez un canal de séquence dans votre projet AEM Screens, par exemple **LaunchesDemo** --> **Canaux** --> **FutureLaunch**, comme illustré ci-dessous.

   >[!CAUTION]
   >
   >Vous devez créer un lancement à partir d’un canal préexistant dans votre projet AEM Screens.

   ![Image](/help/user-guide/assets/launches-images/launches-11.png)

1. Sélectionnez le canal **FutureLaunch** et cliquez sur **Créer un lancement** dans la barre d’actions.

   ![Image](/help/user-guide/assets/launches-images/launches-12.png)

1. L’assistant **Créer un lancement** s’ouvre. Vous pouvez soit sélectionner le canal déjà visible dans l’assistant, soit cliquer sur **+ Ajouter un canal** de façon à ajouter le canal pour lequel vous souhaitez créer le lancement.

1. Cliquez sur **Suivant** dans l’assistant **Créer un lancement**. L’option **Inclure les sous-pages** est sélectionnée par défaut.

   ![image](/help/user-guide/assets/launches-images/launches-d.png)

   >[!NOTE]
   >Vous pouvez utiliser l’option **+ Ajouter un canal** afin d’ajouter un autre canal pour lequel vous souhaitez créer le lancement.

   Pour utiliser l’option **Ajouter un canal**, accédez au canal pour lequel vous souhaitez créer le lancement, puis cliquez sur **Sélectionner**.

   L’option **Sélectionner** est désactivée si vous essayez de sélectionner plusieurs canaux ou un dossier pour ajouter le lancement.

   ![image](/help/user-guide/assets/launches-images/launches-14.png)

   Une fois le ou les canaux sélectionnés, cliquez sur **Suivant**.


1. Saisissez le **Titre du lancement** **SummerPromotions** et vous n’aurez pas besoin de définir la **Date de lancement**, comme illustré dans la figure ci-dessous. Cliquez sur **Créer**.

   >[!NOTE]
   >
   >*Activer ou cocher* l’option **Hériter des données actives de la page source** permet de créer les canaux en tant que Live Copies dans le lancement. Si des modifications sont apportées au canal d’origine, elles sont automatiquement appliquées aux canaux de lancement.
   >
   >
   >*Désactiver ou désélectionner* **Hériter des données actives de la page source** permet de copier les canaux sans aucune relation active dans le lancement. Ainsi, si des modifications sont apportées au canal d’origine, elles ne sont pas appliquées aux canaux de lancement.

   ![Image](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >Vous pouvez définir la date de lancement dans cette étape ou la configurer ultérieurement lors de la modification des propriétés du lancement une fois qu’il a été créé.

   **Présentation de la portée de la promotion de lancement**

   * **Convertir le lancement complet** : tous les canaux du lancement sont promus à la date d’activation définie.
   * **Promouvoir les pages modifiées** : seules les ressources de lancement modifiées seront promues. Il est recommandé d’utiliser cette option lorsque la révision du lancement n’est pas requise.
   * **Convertir les pages approuvées** : cette option nécessite que le workflow d’approbation du lancement s’exécute sur les canaux de lancement. Seules les pages approuvées seront promues à la date d’activation définie.

      >[!CAUTION]
      >
      >La date d’activation du lancement se conforme au fuseau horaire du lecteur/de l’appareil plutôt qu’à celui du serveur.

1. Vous verrez que votre lancement est créé. Vous pouvez cliquer sur **Ouvrir** pour afficher les pages dans l’éditeur ou sur **Terminé** pour revenir à votre projet.

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   Cliquez sur **Terminé** pour revenir à votre canal **FutureLaunch**.

   ![Image](/help/user-guide/assets/launches-images/launches-16.png)


### Modification des propriétés de lancement pour définir la date d’activation et la portée {#editing-the-launch-properties-to-set-the-live-date-and-scope}

Une fois le lancement créé, vous pouvez mettre à jour les propriétés telles que la date d’activation, le titre du lancement et la portée de la promotion à l’aide de **Propriétés du lancement**.

* **Date de lancement**, fait référence à la date d’activation, c’est-à-dire la date ou l’heure de lecture du contenu dans le lecteur Screens selon le fuseau horaire du lecteur.
* **Prêt pour la production**, permet aux canaux d’être publiés après promotion. Cette fonction étant activée par défaut, il n’est pas nécessaire de la modifier.
* **Portée**, détermine les canaux qui seront promus lors de la promotion du lancement.


Pour modifier les propriétés de lancement, procédez comme suit :

1. Accédez au canal **FutureLaunch** *(il s’agit du lancement en attente)* et sélectionnez-le, comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/launches-images/launches-17.png)

1. Cliquez sur **Tableau de bord** dans la barre d’actions et vous verrez le panneau **LANCEMENTS EN ATTENTE** dans le tableau de bord des canaux.

   ![image](/help/user-guide/assets/launches-images/launches-18.png)

1. Sélectionnez le lancement, puis cliquez sur **Propriétés du lancement** dans le panneau **LANCEMENTS EN ATTENTE**.

   ![image](/help/user-guide/assets/launches-images/launches-19.png)

### Modification du lancement Screens pour ajouter ou supprimer des canaux {#editing-the-screens-launch-to-add-or-remove-channels}

Après avoir créé le lancement, vous pouvez ajouter ou supprimer des canaux pour celui-ci à l’aide de l’option **Modifier le lancement**.

Une fois que vous avez terminé, cliquez sur **Enregistrer** pour revenir au canal **FutureLaunch**.

### Promotion manuelle du lancement Screens{#promote-the-screens-launch-manually}

Vous pouvez promouvoir le lancement manuellement à l’aide de l’option **Convertir le lancement** depuis le panneau **LANCEMENTS EN ATTENTE**.

Vous pouvez choisir les ressources que vous souhaitez promouvoir manuellement dans l’**Assistant Promotion du lancement**.

![image](/help/user-guide/assets/launches-images/launches-e.png)

1. Vous pouvez activer ou désactiver l’option de suppression du lancement après production.
1. Vous pouvez définir la **portée** du lancement avec les options suivantes :
   1. **Convertir le lancement complet** : tous les canaux du lancement sont promus à la date d’activation définie.
   1. **Promouvoir les pages modifiées** : seules les ressources de lancement modifiées seront promues. Il est recommandé d’utiliser cette option lorsque la révision du lancement n’est pas requise.
   1. **Convertir les pages approuvées** : cette option nécessite que le workflow d’approbation du lancement s’exécute sur les canaux de lancement. Seules les pages approuvées seront promues à la date d’activation définie.
   1. **Convertir la page active** : cette option nécessite que le workflow d’approbation du lancement s’exécute uniquement pour la page active.
1. Cliquez sur **Suivant** dans l’assistant **Promotion du lancement**.
1. Cliquez sur **Promouvoir** pour promouvoir le lancement.

### Suppression du lancement Screens {#deleting-the-screens-launch}

Vous pouvez supprimer le lancement à l’aide de l’option **Supprimer le lancement** du panneau **LANCEMENTS EN ATTENTE**.

>[ATTENTION]
>Cette action supprimera également tous les descendants (lancements imbriqués).

