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
source-git-commit: e82cfee5ecc6b639b7b2b65553d1635943b356ea
workflow-type: tm+mt
source-wordcount: '1567'
ht-degree: 60%

---

# Mise à jour du contenu à l’aide d’un lancement Screens {#launches}

Les auteurs de contenu peuvent créer une version ultérieure des canaux et définir la date d’activation de ce lancement. Cette fonctionnalité permet au contenu d’être en ligne sur des appareils ou des lecteurs à la date d’activation spécifiée.

Grâce au ***lancement Screens***, les auteurs et autrices peuvent prévisualiser chaque canal du lancement et doivent être en mesure de lancer une demande de révision. Le groupe des approbateurs et approbatrices reçoit une notification et peut approuver ou rejeter la demande. Lorsque la date d’activation est atteinte, le contenu est lu sur les appareils.

Par exemple, si l’auteur ou l’autrice souhaite créer des versions futures de c1, c2 (canaux), un lancement est créé et une date d’activation est définie (par exemple, le 10 novembre à 8 h 00). Toute mise à jour ultérieure du contenu est envoyée pour révision.

Après approbation et à la date d’activation (10 novembre à 8 heures), ce lancement lit le contenu sur les appareils ou lecteurs.

## Exigences {#requirements}

Avant de commencer à utiliser *Lancement Screens* dans un projet AEM Screens, veillez à bien comprendre le concept de période de grâce et sa pertinence.

L’exécution d’une expérience sur le lecteur à la date d’activation définie implique :

* la promotion du lancement (ne prend en général que quelques secondes) ;

* la publication des ressources sur les instances de publication (cela prend généralement quelques minutes, selon la taille des canaux ou ressources à publier) ;

* Temps nécessaire pour que la mise à jour du contenu hors ligne soit terminée (généralement quelques minutes).

* le temps pris par les lecteurs pour télécharger le contenu à partir de l’instance de publication (cela prend généralement plusieurs minutes en fonction de la bande passante et de la taille des ressources à télécharger) ;

* les éventuels décalages horaires entre serveur et lecteur.

### Présentation du délai de grâce {#understanding-grace-period}

Pour que le lecteur puisse lire le contenu à la date d’activation définie, démarrez les activités précédentes avant la date d’activation.

Si la date d’activation est *24 novembre à 9 heures* et *24 heures* est la période de grâce, puis la séquence d’actions ci-dessus commence à (date d’activation - période de grâce), c’est-à-dire le 23 novembre à 9h00 (heure du serveur). Ce paramètre donne 24 heures pour terminer toutes les actions mentionnées ci-dessus pour que le contenu atteigne les lecteurs. Les lecteurs comprennent que cette période est un contenu de lancement. Par conséquent, le contenu n’est pas lu immédiatement, mais les lecteurs peuvent stocker ce contenu en tant que version ultérieure et le faire lire exactement à la date d’activation définie sur le fuseau horaire du lecteur.

Par exemple, le serveur est en PST et les périphériques en EST. La différence maximale est de trois heures. Cela suppose que la promotion prend 1 minute et que la publication de l’auteur à la publication prend 10 minutes et que le lecteur peut généralement télécharger les ressources en 10 à 15 minutes. Ensuite, le délai de grâce = décalage horaire (trois heures) :

* Plus le temps pour promouvoir le lancement (1 minute)
* Plus le temps pour publier le lancement (10 minutes)
* Plus le temps de téléchargement supplémentaire au niveau du lecteur (10 à 15 minutes)
* Plus la mise mémoire tampon (30 minutes)

Par conséquent, 3 heures 56 minutes (1 4160 secondes).

Ainsi, chaque fois que vous planifiez un lancement actif, la promotion commence tôt en prenant en compte ce décalage. Dans l’équation ci-dessus, la plupart des éléments ne prennent pas beaucoup de temps. Vous pouvez utiliser une estimation correcte de ce décalage lorsque vous connaissez la différence de temps maximale entre le serveur et n’importe quel lecteur.

>[!NOTE]
>
>Par défaut, le délai de grâce du lancement Screens est défini sur 24 heures. Cela signifie que lorsque vous définissez une date d’activation pour un lancement pour les ressources sous */content/screens*, la promotion commence avec ce décalage.

### Mise à jour de la période de grâce prête à l’emploi {#updating-out-of-the-box-grace-period}

Cette section explique comment mettre à jour une période de grâce d’usine à 10 minutes.

1. Accédez à CRXDE Lite, puis à `/libs/system/config.author/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config`.
1. Cliquez avec le bouton droit et copiez le fichier.
1. Accédez à `/apps/system/config`, cliquez avec le bouton droit et collez.
1. Double-cliquez sur `/apps/system/config/com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config` pour ouvrir le fichier dans l’éditeur de CRXDE Lite. Il doit afficher la période de grâce du chemin */content/screens/* comme étant de **86 400**. Remplacez cette valeur par **600**.

Désormais, le contenu du fichier texte doit ressembler à ce qui suit :

```java
launches.eventhandler.launch.promotion.graceperiod=[ \
   "/content/screens(/.*):600", \
   ]
```

Vous définissez la période de grâce sur 10 minutes dans l’exemple précédent. Par conséquent, lorsque vous définissez une date d’activation pour un lancement pour les ressources sous */content/screens*, la promotion commence avec ce décalage.

Par exemple, si la date d’activation est définie sur 24 novembre à 9h00 et que la période de grâce est de 600 secondes, la tâche de promotion commence le 24 novembre à 8h50.

## Utilisation du lancement Screens {#using-launches}

Cette section explique comment mettre en œuvre le lancement Screens dans votre projet AEM Screens.

### Création d’un lancement Screens {#creating-a-launch}

Pour mettre en œuvre la fonctionnalité de lancement Screens dans votre projet AEM Screens, procédez comme suit :

1. Créez un canal de séquence dans votre projet AEM Screens, par exemple **LaunchesDemo** > **Canaux** > **FutureLaunch**, comme illustré ci-dessous.

   >[!CAUTION]
   >
   >Créez un lancement à partir d’un canal préexistant dans votre projet AEM Screens.

   ![Image](/help/user-guide/assets/launches-images/launches-11.png)

1. Cliquez sur le canal **FutureLaunch** et cliquez sur **Créer un lancement** dans la barre d’actions.

   ![Image](/help/user-guide/assets/launches-images/launches-12.png)

1. L’assistant **Créer un lancement** s’ouvre. Vous pouvez cliquer sur le canal déjà visible dans l’assistant ou cliquer sur **+ Ajouter des canaux** pour ajouter le canal pour lequel vous souhaitez créer le lancement.

1. Cliquez sur **Suivant** dans l’assistant **Créer un lancement**. L’option **Inclure les sous-pages** est sélectionnée par défaut.

   ![image](/help/user-guide/assets/launches-images/launches-d.png)

   >[!NOTE]
   >Vous pouvez utiliser la variable **+ Ajouter des canaux** pour ajouter un autre canal pour lequel vous souhaitez créer le lancement.

   Pour utiliser la variable **Ajout de canaux** , accédez au canal pour lequel vous souhaitez créer le lancement, puis cliquez sur **Sélectionner**.

   La variable **Sélectionner** est désactivée si vous essayez de cliquer sur plusieurs canaux ou sur un dossier pour ajouter le lancement.

   ![image](/help/user-guide/assets/launches-images/launches-14.png)

   Après avoir cliqué sur le ou les canaux, cliquez sur **Suivant**.


1. Saisissez le **Titre du lancement** **SummerPromotions** et vous n’aurez pas besoin de définir la **Date de lancement**, comme illustré dans la figure ci-dessous. Cliquez sur **Créer**.

   >[!NOTE]
   >
   >*Activer ou cocher* l’option **Hériter des données actives de la page source** permet de créer les canaux en tant que Live Copies dans le lancement. Si des modifications sont apportées au canal d’origine, elles sont automatiquement appliquées aux canaux de lancement.
   >
   >
   >*Désactiver ou décocher* **Hériter les données dynamiques de la page source** permet de copier les canaux sans aucune relation active au lancement. Ainsi, si des modifications sont apportées au canal d’origine, elles ne sont pas appliquées aux canaux de lancement.

   ![Image](/help/user-guide/assets/launches-images/launches-c.png)

   >[!NOTE]
   >
   >Vous pouvez définir la date de lancement dans cette étape ou la configurer ultérieurement lors de la modification des propriétés du lancement une fois qu’il a été créé.

   **Présentation de la portée de la promotion de lancement**

   * **Promouvoir le lancement complet** : tous les canaux du lancement sont promus à la date d’activation définie.
   * **Promouvoir les pages modifiées** : seules les ressources de lancement modifiées seront promues. Utilisez cette option lorsque la révision du lancement n’est pas requise.
   * **Convertir les pages approuvées** : cette option nécessite que le workflow d’approbation du lancement s’exécute sur les canaux de lancement. Seules les pages approuvées seront promues à la date d’activation définie.

     >[!CAUTION]
     >
     >La date d’activation du lancement respecte le fuseau horaire du lecteur/de l’appareil plutôt que les serveurs.

1. Notez que votre lancement est créé. Vous pouvez cliquer sur **Ouvrir** pour afficher les pages dans l’éditeur ou sur **Terminé** pour revenir à votre projet.

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   Sélectionnez **Terminé** pour revenir à votre canal **FutureLaunch**.

   ![Image](/help/user-guide/assets/launches-images/launches-16.png)


### Modification des propriétés de lancement pour définir la date d’activation et la portée {#editing-the-launch-properties-to-set-the-live-date-and-scope}

Une fois le lancement créé, vous pouvez mettre à jour les propriétés telles que la date d’activation, le titre du lancement et la portée de la promotion à l’aide des **Propriétés du lancement**.

* **Date de lancement** : fait référence à la date d’activation, c’est-à-dire la date ou l’heure de lecture du contenu dans le lecteur Screens selon le fuseau horaire du lecteur.
* **Prêt pour la production** - Après la promotion, elle permet aux canaux d’être publiés et l’option d’usine est activée, donc il n’est pas nécessaire de la modifier.
* **Portée** : détermine les canaux qui seront promus lors de la promotion du lancement.

Pour modifier les propriétés de lancement, procédez comme suit :

1. Accédez au canal **FutureLaunch** *(lancement en attente)*, puis cliquez sur le canal comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/launches-images/launches-17.png)

1. Cliquez sur **Tableau de bord** à partir de la barre d’actions, le **LANCEMENTS EN ATTENTE** du tableau de bord des canaux.

   ![image](/help/user-guide/assets/launches-images/launches-18.png)

1. Cliquez sur le lancement, puis sur **Propriétés de lancement** de la **LANCEMENTS EN ATTENTE** du panneau.

   ![image](/help/user-guide/assets/launches-images/launches-19.png)

### Modification du lancement Screens pour ajouter ou supprimer des canaux {#editing-the-screens-launch-to-add-or-remove-channels}

Après avoir créé le lancement, vous pouvez ajouter ou supprimer des canaux au lancement existant à l’aide du **Modifier le lancement** .

Lorsque vous avez terminé, cliquez sur **Enregistrer** pour revenir à la **FutureLaunch** canal.

### Promotion manuelle du lancement Screens{#promote-the-screens-launch-manually}

Vous pouvez promouvoir le lancement manuellement à l’aide de l’option **`Promote Launch`** depuis le panneau **LANCEMENTS EN ATTENTE**.

Vous pouvez choisir les ressources que vous souhaitez promouvoir manuellement dans l’**Assistant Promotion du lancement**.

![image](/help/user-guide/assets/launches-images/launches-e.png)

1. Vous pouvez activer ou désactiver l’option de suppression du lancement après production.
1. Vous pouvez définir la **portée** du lancement avec les options suivantes :
   * **Convertir le lancement complet** : tous les canaux du lancement sont promus à la date d’activation définie.
   * **Promouvoir les pages modifiées** : seules les ressources de lancement modifiées seront promues. Utilisez cette option lorsque la révision du lancement n’est pas requise.
   * **Convertir les pages approuvées** : cette option nécessite que le workflow d’approbation du lancement s’exécute sur les canaux de lancement. Seules les pages approuvées seront promues à la date d’activation définie.
   * **Convertir la page active** : cette option nécessite que le workflow d’approbation du lancement s’exécute uniquement pour la page active.
1. Cliquez sur **Suivant** dans l’assistant **Promotion du lancement**.
1. Cliquez sur **Promouvoir** pour promouvoir le lancement.

### Suppression du lancement Screens

Vous pouvez supprimer le lancement à l’aide du **Supprimer Launch** de l’option **LANCEMENTS EN ATTENTE** du panneau.

>[!CAUTION]
>
>Cette action supprimera également tous les descendants (lancements imbriqués).
