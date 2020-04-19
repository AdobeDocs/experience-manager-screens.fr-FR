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
source-git-commit: 6c833984748c89cc271e70450c7f51abda2fa7c7

---


# Mise à jour de contenu à l’aide du lancement d’écrans {#launches}

Content authors can create future version of the channel(s), known as **Screens Launch** and further setting live date for this launch allows content to be live in devices or players.

Grâce à une publication ultérieure, les auteurs peuvent  chaque  au lancement et doivent être en mesure d’initier une demande de révision. Le groupe des approbateurs reçoit une notification et peut approuver ou rejeter la demande. Lorsque la date d’activation est atteinte, le contenu est lu sur les périphériques.

Par exemple, si l’auteur souhaite créer des versions futures de c1, c2 (canaux), un lancement est créé et une date d’activation est définie (par exemple, le 10 novembre à 8 heures). Toute mise à jour ultérieure du contenu est envoyée pour révision. Une fois approuvé, ce lancement lira à la date d’activation (10 novembre, 8 h) le contenu sur les périphériques ou lecteurs.

## Conditions requises {#requirements}

Avant de  l’implémentation de la publication future dans un projet AEM Screens, assurez-vous de bien comprendre le concept de la période de grâce et sa pertinence.

La section suivante explique la période de grâce et comment la configurer en standard. Vous pouvez également télécharger un exemple de configuration de test pour comprendre son utilisation.

### Présentation de la période de grâce {#understanding-grace-period}

The following setup allows the admin to configure the ***Grace Period***, required in future publish.

La **Période de grâce** comprend :

* promotion du lancement
* publication des ressources aux instances de publication
* temps nécessaire aux périphériques pour télécharger le contenu à partir de l’instance de publication et  tout écart d’heure entre le serveur et le lecteur

Par exemple, supposons que le serveur utilisent le fuseau horaire PST et les périphériques le fuseau horaire EST, que la différence de temps maximale est de 3 heures dans ce cas et supposons que la promotion durera 1 minute, que la publication de l’auteur à la publication prend 10 minutes et que le lecteur peut généralement télécharger les ressources en 10-15 minutes. Ensuite, période de grâce = écart de  l’heure (3 heures) + temps pour promouvoir le lancement (1 min) + temps pour publier le lancement (10 min) + temps pour télécharger au lecteur (10-15 min) + mémoire tampon (pour être sûr, disons 30 min) = 3 heures 56 min = 14160 secondes. Ainsi, lorsque nous planifions un lancement en direct, la promotion commence tôt en fonction de ce délai (décalage). Dans l&#39;équation ci-dessus, la plupart des éléments ne prennent pas beaucoup de temps, nous pouvons utiliser une estimation correcte de ce décalage à condition de connaître l’écart maximal de l’heure entre le serveur et n&#39;importe quel lecteur.

### Configuration par défaut de la période de grâce {#configuring-out-of-the-box-grace-period}

Par défaut, la période de grâce d’un lancement est définie sur 24 heures, ce qui signifie que lorsque nous définissons la date  d’activation de n’importe quel lancement pour les ressources sous */content/screens*, la promotion commence avec ce décalage. Par exemple, si la date de production est définie sur le 24 novembre à 9h00 et que la période de grâce est de 24 heures, la tâche de promotion démarrera le 23 novembre à 9h00.

### Téléchargement des configurations {#downloading-configurations}

Téléchargez les configurations de test suivantes :

[Obtenir un fichier](assets/launches_event_handlerconfig-10.zip)

>[!NOTE]
>
>La configuration mentionnée ci-dessus comporte une période de grâce de 600 secondes dans cette configuration de test.

#### Mise à jour des configurations {#updating-the-configurations}

Si vous souhaitez modifier la configuration ci-dessus, suivez les instructions ci-dessous :

* créez le fichier ***sling:OsgiConfig/ nt:file dans /apps/system/config*** sous le nom **com.adobe.cq.wcm.launches.impl.LaunchesEventHandler.config** et le contenu

   *launches.eventhandler.updatelastmodification=B&quot;false&quot;
launches.eventhandler.launch.promotion.graceperiod=[&quot;/content/screens(/.*):600&quot;]launches.eventhandler.threadpool.maxsize=I&quot;5&quot;
launches.eventhandler.threadpool.priority=&quot;MIN&quot;*

* `launches.eventhandler.launch.promotion.graceperiod=["/content/screens(/.&#42;):600"`, vous permet de définir une période de grâce de 600 secondes dans le chemin */content/screens*.

Cela signifie que lorsque vous définissez la date d’activation d’un lancement pour les ressources sous */content/screens*, la promotion commence avec ce décalage. Si, par exemple, la date d’activation est définie sur 24 novembre à 9h00 et que la période de grâce est de 600 secondes, la tâche de promotion démarrera le 24 novembre à 8h50.

## Utilisation du lancement d’écrans {#using-launches}

Suivez la section ci-dessous pour implémenter les lancements dans votre projet AEM Screens. Cette section traite des sujets suivants :

1. **Création d’un lancement d’écran**
1. **Modification d’un lancement d’écran pour définir la date et l’étendue d’activation**

### Création d’une publication future {#creating-a-launch}

Suivez les étapes ci-dessous pour mettre en œuvre les futures fonctionnalités de publication dans votre projet AEM Screens :

1. Accédez au canal dans votre projet AEM Screens, par exemple **LaunchesDemo** —> **Canaux** —> **FutureLaunch**, comme illustré ci-dessous.

   >[!CAUTION]
   >
   >Vous devez créer un lancement à partir d’un canal préexistant dans votre projet AEM Screens.

   ![screen_shot_2019-06-25at15052pm](assets/screen_shot_2019-06-25at15052pm.png)

1. Sélectionnez le canal **FutureLaunch**, puis cliquez sur **Créer**. Sélectionnez **Lancer** dans le menu déroulant.

   ![screen_shot_2019-06-25at15459pm](assets/screen_shot_2019-06-25at15459pm.png)

1. L’assistant **Créer un lancement** s’ouvre. Cliquez sur **+ Ajouter des pages** pour sélectionner les canaux AEM Screens pour lesquels vous souhaitez créer le lancement.

   ![screen_shot_2019-06-11at93710am](assets/screen_shot_2019-06-11at93710am.png)

1. Accédez au canal et cliquez sur **Sélectionner**.

   ![screen_shot_2019-06-25at20030pm](assets/screen_shot_2019-06-25at20030pm.png)

1. Une fois la page sélectionnée, cliquez sur **Suivant** pour avancer d’une étape vers l’assistant **Créer un lancement**.

   ![screen_shot_2019-06-25at20128pm](assets/screen_shot_2019-06-25at20128pm.png)

1. Saisissez le **Titre du lancement** **SummerPromotions** et vous n’aurez pas besoin de définir la **Date de lancement**, comme illustré dans la figure ci-dessous. Cliquez sur **Créer**.

   >[!NOTE]
   >
   >*Activer ou cocher* l’option **Hériter les données dynamiques de la page source** permet de créer les canaux en tant que copies dynamiques au lancement. Si des modifications sont apportées au canal d’origine, elles sont automatiquement appliquées aux canaux de lancement.
   >
   >
   >*Désactiver ou décocher* Hériter les données dynamiques de la page source **** permet de copier les canaux sans aucune relation active au lancement. Ainsi, si des modifications sont apportées au canal d’origine, elles ne sont pas appliquées aux canaux de lancement.

   ![screen_shot_2019-06-25at20215pm](assets/screen_shot_2019-06-25at20215pm.png)

   >[!NOTE]
   >
   >Vous pouvez définir la date de lancement en direct dans cette étape ou la configurer ultérieurement lors de la modification des propriétés du lancement une fois qu’il a déjà été créé.

1. Vous verrez que votre lancement est créé. Vous pouvez cliquer sur **Ouvrir** pour afficher les pages dans l’éditeur ou sur **Terminé** pour revenir à votre projet.

   ![screen_shot_2019-06-25at20355pm](assets/screen_shot_2019-06-25at20355pm.png)

   Cliquez sur **Terminé** pour revenir à votre projet **LaunchesDemo**.

   ![screen_shot_2019-06-25at20434pm](assets/screen_shot_2019-06-25at20434pm.png)

### Modification des propriétés de lancement pour définir la date et la portée d’activation {#editing-the-launch-properties-to-set-the-live-date-and-scope}

Après avoir créé le lancement, vous devez modifier les propriétés de lancement pour définir la date d’activation et la portée du lancement.

Pour modifier les propriétés de lancement, procédez comme suit :

1. Accédez au canal (**FutureLaunch**) et sélectionnez-le, comme illustré ci-dessous. Ouvrez le rail **Références** à partir du rail latéral gauche.

   >[!NOTE]
   >
   >Sélectionnez l’option **Arborescence de contenu** dans le rail de gauche pour ouvrir le lancement que vous avez créé.

   ![screen_shot_2019-06-25at25852pm](assets/screen_shot_2019-06-25at25852pm.png)

1. Accédez à **Lancements** et sélectionnez le lancement (**SummerPromotions**) que vous avez créé. Cliquez sur **Modifier les propriétés**.

   ![screen_shot_2019-06-25at30008pm](assets/screen_shot_2019-06-25at30008pm.png)

1. La boîte de dialogue **SummerPromotions** s’ouvre. Renseignez les champs suivants :

   * Sélectionner la **Date de lancement**
   * Cocher **Prêt pour production**
   * Sélectionnez **Promouvoir les pages** approuvées dans **Portée**
   >[!NOTE]
   >
   >Comprendre les entrées Lancements sous **Promotion automatique** :

   >    * **Date de lancement**, fait référence à la date d’activation, c’est-à-dire la date/l’heure de lecture du contenu dans le lecteur Screens selon le fuseau horaire du lecteur.
   >    * **Prêt pour production** permet de promouvoir les canaux et signifie que le lancement est prêt à être utilisé.
   >    * **Portée** fait référence aux canaux qui peuvent être promus lors d’un lancement.


   Les trois options suivantes sont disponibles pour configurer la portée :
   1. **Promouvoir le lancement complet** : tous les canaux du lancement sont promus à la date d’activation définie.
   1. **Promouvoir les pages modifiées** : seules les ressources de lancement modifiées seront promues. Il est recommandé d’utiliser cette option lorsque la révision du lancement n’est pas requise. Elle permet de promouvoir les modifications apportées aux canaux de lancement.
   1. **Promouvoir les pages approuvées** : seules les pages approuvées sont promues à la date d’activation définie.
   ![screen_shot_2019-06-26at113805am](assets/screen_shot_2019-06-26at113805am.png)

   >[!CAUTION]
   >
   >La promotion du lancement se conforme au fuseau horaire du lecteur/périphérique plutôt que celui du serveur.

1. Cliquez sur **Enregistrer et fermer** pour revenir au canal **FutureLaunch**.

   ![screen_shot_2019-06-26at114332am](assets/screen_shot_2019-06-26at114332am.png)

