---
title: Utilisation d’une séquence incorporée dynamique
description: Découvrez comment implémenter des séquences incorporées dynamiques dans votre projet AEM Screens.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3208d058-0812-44e1-83e3-b727b384876a
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '2426'
ht-degree: 48%

---

# Utilisation d’une séquence incorporée dynamique {#using-dynamic-embedded-sequence}

L’utilisation de séquences incorporées dynamiques couvre les rubriques suivantes :

* **Présentation**
* **Utilisation de l’expérience incorporée dynamique dans AEM Screens**
* **Affichage des résultats**
* **Restriction des utilisateurs et modification des listes de contrôle d’accès**

## Présentation {#overview}

***Séquences incorporées dynamiques*** sont créés pour les grands projets qui respectent la hiérarchie parent-enfant, où l’enfant est référencé dans un dossier d’emplacement et non dans un dossier de canaux. Cela permet à l’utilisateur d’incorporer une séquence à l’intérieur d’un canal par ***Rôle de canal***. Cela permet à l’utilisateur de définir des espaces réservés spécifiques à un emplacement pour différents bureaux à l’aide d’une séquence incorporée dans un canal principal.

Lors de l’attribution d’un canal à un affichage, vous avez la possibilité de spécifier le chemin de l’affichage ou le rôle du canal qui résout un canal réel en fonction du contexte.

Pour utiliser la séquence incorporée dynamique, il faut affecter un canal par ***rôle de canal***. Le rôle du canal définit le contexte de l’affichage. Le rôle est ciblé par diverses actions ; il est indépendant du canal qui remplit le rôle. Cette section décrit un cas d’utilisation qui définit les canaux par rôle et comment vous pouvez appliquer ce contenu à un canal global. Vous pouvez également considérer le rôle comme un identifiant pour l’attribution ou comme un alias pour le canal dans le contexte.

### Avantages de l’utilisation de séquences incorporées dynamiques {#benefits-of-using-dynamic-embedded-sequences}

Le principal avantage du placement d’un canal de séquence à l’intérieur d’un emplacement au lieu du dossier des canaux est de permettre aux auteurs locaux ou régionaux de modifier le contenu qui les intéresse. Tout cela, tout en étant interdit de modifier les canaux situés à un niveau supérieur de la hiérarchie.

Référencer une *Canal par rôle*, vous permet de créer une version locale d’un canal afin de résoudre dynamiquement le contenu spécifique à un emplacement. Il permet également de créer un canal global qui utilise le contenu pour les canaux spécifiques à un emplacement.

>[!NOTE]
>
>**Séquences incorporées ou Séquences incorporées dynamiques**
>
>Une séquence incorporée dynamique est semblable à une séquence incorporée, mais permet à l’utilisateur de suivre une hiérarchie où les modifications/mises à jour effectuées sur un canal sont propagées aux autres canaux liés. Elle respecte une hiérarchie parent-enfant et comprend également des ressources telles que des images ou des vidéos.
>
>Les ***séquences incorporées dynamiques*** permettent d’afficher du contenu spécifique à l’emplacement, tandis que les ***séquences incorporées*** affichent uniquement un diaporama général du contenu. En outre, lors de la configuration des séquences incorporées dynamiques, configurez le canal à l’aide du rôle et du nom du canal. Pour une mise en oeuvre pratique, reportez-vous aux étapes ci-dessous.
>
>Pour en savoir plus sur l’implémentation de séquences incorporées, voir [Séquences incorporées](embedded-sequences.md) dans AEM Screens.

L’exemple suivant fournit une solution en se concentrant sur les termes clés suivants :

* a ***canal de séquence principal*** pour la séquence globale.
* ***séquence incorporée dynamique*** composants pour chaque partie localement personnalisable de la séquence.
* ***canaux de séquence individuels*** dans les emplacements respectifs avec une *rôle* dans l’affichage correspondant à la fonction **du composant de séquence incorporée dynamique *rôle***.

>[!NOTE]
>
>Pour en savoir plus sur l’attribution des canaux, voir **[Attribution des canaux](channel-assignment.md)** dans la section Création de la documentation relative à AEM Screens.

## Utilisation d’une séquence incorporée dynamique {#using-dynamic-embedded-sequence-2}

La section suivante explique la création d’une séquence incorporée dynamique dans un canal AEM Screens.

### Prérequis {#prerequisites}

Avant de commencer à implémenter cette fonctionnalité, assurez-vous que les conditions préalables suivantes sont satisfaites avant de commencer à implémenter des séquences incorporées dynamiques :

* Créez un projet AEM Screens (dans cet exemple, **Démonstration**).
* Création d’un canal comme **Global** under **Canaux** dossier.
* Ajoutez du contenu à vos **Global** Canal (*Vérifier **Resources.zip**pour les ressources appropriées*).

L’image suivante montre le projet **Demo** avec le canal **Global** dans le dossier **Canaux**.
![screen_shot_2018-09-07at21032pm](assets/screen_shot_2018-09-07at21032pm.png)

### Ressources {#resources}

Vous pouvez télécharger les ressources suivantes (images et les ajouter aux ressources) et les utiliser comme contenu de canal à des fins de démonstration.

[Obtenir le fichier](assets/resources.zip)

>[!NOTE]
>
>Pour plus d’informations sur la création d’un projet et sur la création d’un canal de séquence, voir les ressources suivantes :
>
>* **[Création et gestion des projets](creating-a-screens-project.md)**
>* **[Gestion d’un canal](managing-channels.md)**
>

Séquence incorporée dynamique dans un projet AEM Screens implique trois tâches principales :

1. **Configuration de la taxonomie du projet, y compris les canaux, emplacements et écrans**
1. **Création d’une planification**
1. **Attribution d’une planification à chaque affichage**

Suivez les étapes ci-dessous pour mettre en œuvre la fonctionnalité :

>[!CAUTION]
>
>Lors de l’implémentation de séquences incorporées dynamiques, veillez à la variable **Nom** et **Titre** lors de la création de canaux sous chaque emplacement. Suivez attentivement les instructions relatives à la nomenclature.

1. **Créez deux dossiers Emplacements.**

   Accédez au dossier **Emplacements** dans votre projet AEM Screens et créez deux dossiers d’emplacement : **Région A** et **Région B**.

   >[!NOTE]
   >
   >Lors de la création du dossier d’emplacement **Région A**, veillez à saisir le **Titre** **Région A**. Vous pouvez laisser le champ **Nom** vide, afin que le nom **région-a** soit automatiquement sélectionné.
   >
   >C’est également le cas pour la création d’un dossier d’emplacement. **Région B**, comme illustré ci-dessous :

   ![screen_shot_2018-09-13at23212pm](assets/screen_shot_2018-09-13at23212pm.png)

   >[!NOTE]
   >Pour savoir comment créer un emplacement, voir **[Création et gestion des emplacements](managing-locations.md)**.

1. **Créez deux emplacements et un canal sous chaque dossier d’emplacement.**

   1. Accédez à **Démonstration** > **Emplacements** > **Région A**.
   1. Cliquez sur **Région A** et cliquez sur **+ Créer** dans la barre d’actions.
   1. Cliquez sur **Emplacement** de l’assistant avec **Titre** as **Magasin 1**. De même, créez un autre emplacement dans l’assistant intitulé **Magasin 2** pour **Titre** **Magasin 2**. Vous pouvez laisser le champ **Nom** vide lors de la création de **Magasin 1** et **Magasin 2**.
   1. Répétez l’étape (b) et cliquez maintenant sur **Canal de séquence** dans l’assistant. Saisissez le **Titre** **Région A** et le **Nom** **région** pour ce canal.

   >[!CAUTION]
   >
   >Assurez-vous que lors de la création du canal **Région A**, saisissez la variable **Titre** as **Région A** et la variable **Nom** as **region**.

   ![screen_shot_2018-09-13at22857pm](assets/screen_shot_2018-09-13at22857pm.png)

   De même, créez deux emplacements dans la **Région B**, intitulés **Magasin 3** et **Magasin 4**. Créez également un **Canal de séquence** avec pour **Titre** **Région B** et pour **Nom** **région**.

   >[!CAUTION]
   >
   >Veillez à utiliser le même nom pour les canaux créés dans **Région A** et **Région B** as **region**.

   ![screen_shot_2018-09-13at24408pm](assets/screen_shot_2018-09-13at24408pm.png)

1. **Créez Affichage et Canal sous chaque emplacement.**

   1. Accédez à **Démonstration** > **Emplacements** > **Région A** > **Magasin 1**.
   1. Cliquez sur **Magasin 1** et cliquez sur **+ Créer** dans la barre d’actions.
   1. Cliquez sur **Affichage** à partir de l’assistant et créez **`Store1Display`**.
   1. Répétez l’étape (b) et cliquez cette fois sur **Canal de séquence** dans l’assistant. Saisissez le **Titre** as **`Store1Channel`** et la variable **Nom** as **store**.

   >[!CAUTION]
   >
   >Lorsque vous créez un canal de séquence, vous pouvez choisir librement le **titre** du canal, mais le **Nom** doit être identique dans tous les canaux locaux.
   >Dans cet exemple, les canaux situés sous **Région A** et **Région B** share **Nom** as **region** et les canaux sous **`Store 1`**, **`Store 2`**, **`Store 3`**, et **`Store 4`** share **Nom** as **store**.

   ![screen_shot_2018-09-19at120206pm](assets/screen_shot_2018-09-19at120206pm.png)

   De même, créez un affichage sous la forme **`Store2Display`** et un canal **`Store2Channel`** under **`Store `2** (avec le nom comme **store**).

   >[!NOTE]
   >Veillez à utiliser le même nom pour les canaux créés dans **`Store 1`** et **`Store 2`** as **store**.

   ![screen_shot_2018-09-19at120329pm](assets/screen_shot_2018-09-19at120329pm.png)

   Suivez les étapes précédentes pour créer un canal et l’afficher dans **`Store 3`** et **`Store 4`** under **Région B**. Vérifiez que vous utilisez la même **Nom** as **store** lors de la création d’un canal **`Store3Channel`** et **`Store4Channel`** respectivement.

   L’image suivante montre l’affichage et le canal dans **`Store 3`**.

   ![screen_shot_2018-09-19at120448pm](assets/screen_shot_2018-09-19at120448pm.png)

   L’image suivante montre l’affichage et le canal dans **`Store 4`**.

   ![screen_shot_2018-09-19at120552pm](assets/screen_shot_2018-09-19at120552pm.png)

1. **Ajoutez du contenu aux canaux dans leurs emplacements respectifs.**

   Accédez au **Démonstration** > **Emplacements** > **Région A** > **Région A** et cliquez sur **Modifier** dans la barre d’actions. Faites glisser-déposer les ressources à ajouter au canal.

   >[!NOTE]
   >Vous pouvez utiliser le fichier ***Resources.zip*** de la section **Ressources** ci-dessus pour utiliser les images comme ressources pour le contenu de votre canal.

   ![screen_shot_2018-09-12at12438pm](assets/screen_shot_2018-09-12at12438pm.png)

   De même, accédez à la **Démonstration** > **Emplacements** > **Région B** > **Région B** et cliquez sur **Modifier** à partir de la barre d’actions pour faire glisser les ressources vers votre canal, comme illustré ci-dessous :

   ![screen_shot_2018-09-12at13133pm](assets/screen_shot_2018-09-12at13133pm.png)

   Suivez les étapes précédentes et les ressources pour ajouter du contenu aux canaux suivants :

   * **`Store1Channel`**
   * **`Store2Channel`**
   * **`Store3Channel`**
   * **`Store4Channel`**

1. **Créer un calendrier**

   Naviguez et cliquez sur **Planifications** dans votre projet AEM Screens. Cliquez ensuite sur **Créer** dans la barre d’actions.

   L’image suivante montre le **AdSchedule** créé dans le projet **Demo**.

   ![screen_shot_2018-09-13at33307pm](assets/screen_shot_2018-09-13at33307pm.png)

1. **Attribuer des canaux à une planification**

   1. Accédez à **Démonstration** > **Planifications** > **AdSchedule** et cliquez sur **Tableau de bord** dans la barre d’actions.
   1. Cliquez sur **+ Attribuer le canal** de **CANAUX ATTRIBUÉS** pour ouvrir le panneau **Attribution de canaux** de la boîte de dialogue
   1. Cliquez sur **Canal de référence** par chemin.
   1. Cliquez sur le bouton **Chemin du canal** as **Démonstration** > ***Canaux*** > ***Global***.
   1. Définissez le **rôle du canal** sur **GlobalAdSegment**.
   1. Cliquez sur le bouton **Événements pris en charge** as **Charge initiale**, **Écran inactif**, et **Interaction de l’utilisateur**.
   1. Cliquez sur **Enregistrer**.

   **Attribution d’un canal par rôle pour la région :**

   1. Cliquez sur **+ Attribuer le canal** de **CANAUX ATTRIBUÉS** du panneau.
   1. Dans la boîte de dialogue Attribution de canaux, cliquez sur **Canal de référence** par nom.
   1. Saisissez comme **Nom du canal** **région***.
   1. Définissez le **rôle du canal** sur **RegionAdSegment**.
   1. Cliquez sur **Enregistrer**.

   **Attribution d’un canal par rôle pour le magasin :**

   1. Cliquez sur **+ Attribuer le canal** de **CANAUX ATTRIBUÉS** du panneau.
   1. Dans la boîte de dialogue Attribution de canaux, cliquez sur **Canal de référence** par nom.
   1. Saisissez le **Nom du canal** **magasin**.
   1. Définissez le **Rôle du canal** sur **StoreAdSegment**.
   1. Cliquez sur **Enregistrer**.

   L’image suivante montre les canaux attribués par chemin et par rôle.

   ![screen_shot_2018-09-12at21429pm](assets/screen_shot_2018-09-12at21429pm.png)

1. **Configuration d’une séquence incorporée dynamique sur le canal global.**

   Accédez au **Global** Canal que vous avez initialement créé dans **Démonstration** projet.

   Cliquez sur **Modifier** dans la barre d’actions.

   ![screen_shot_2018-09-13at52754pm](assets/screen_shot_2018-09-13at52754pm.png)

   Dans l’éditeur, effectuez un glisser-déposer de deux **Séquence incorporée dynamique** composants dans l’éditeur de canal.

   Ouvrez les propriétés de l’un des composants et saisissez le rôle **d’attribution de canaux** sous la forme **RegionAdSegment**.

   De même, cliquez sur les autres composants et ouvrez les propriétés pour entrer dans le **Rôle d’attribution de canaux** as **StoreAdSegment**.

   ![channeldisplay4](assets/channeldisplay4.gif)

1. **Attribution d’une planification à chaque affichage**

   1. Accédez à chaque affichage, par exemple : **Démonstration** > **Emplacements** > **Région A** >**Magasin 1** >**`Store1Display`**.
   1. Cliquez sur **Tableau de bord** dans la barre d’actions.
   1. Dans le tableau de bord, cliquez sur **..** de la **CANAUX ET PLANIFICATIONS AFFECTÉS** puis cliquez sur **+Attribuer une planification**.
   1. Cliquez sur le chemin d’accès au planning (par exemple, ici, **Démonstration** > **Planifications** > **AdSchedule**).
   1. Cliquez sur **Enregistrer**.

## Affichage des résultats {#viewing-the-results}

Une fois la configuration des canaux et l’affichage terminés, lancez le lecteur AEM Screens pour afficher le contenu.

>[!NOTE]
>
>Pour en savoir plus sur le lecteur AEM Screens, consultez les ressources suivantes :
>
>* [Téléchargement du lecteur AEM Screens](https://download.macromedia.com/screens/)
>* [Utilisation du lecteur AEM Screens](working-with-screens-player.md)


La sortie suivante confirme le contenu de votre canal dans le lecteur AEM Screens, selon le chemin d’affichage.

**Scénario 1**:

Si vous attribuez le chemin d’affichage comme **Démonstration** > **Emplacements** > **Région A** > **Magasin 1** > **`Store1Display`**, le contenu suivant s’affiche sur votre lecteur AEM Screens.

![channeldisplay1](assets/channeldisplay1.gif)

**Scénario 1**:

Si vous attribuez le chemin d’affichage comme **Démonstration** > **Emplacements** > **Région B** > **Magasin 3** > **`Store3Display`**, le contenu suivant s’affiche sur votre lecteur AEM Screens.

![channeldisplay2](assets/channeldisplay2.gif)

## Restriction des utilisateurs et modification des listes de contrôle d’accès {#restricting-users-and-modifying-the-acls}

Vous pouvez créer des auteurs globaux, régionaux ou locaux afin de pouvoir modifier le contenu qui les concerne sans possibilité de modifier des canaux situés à un niveau supérieur de la hiérarchie.

Modifiez les listes de contrôle d’accès afin de restreindre l’accès de l’utilisateur au contenu en fonction de son emplacement.

### Exemple de cas d’utilisation {#example-use-case}

L’exemple suivant vous permet de créer trois utilisateurs pour le projet de démonstration ci-dessus.

Les privilèges sont attribués à chaque groupe comme suit :

**Groupes** :

* **Global-Auteur** : comprend les utilisateurs qui ont accès à tous les emplacements et canaux du projet **Demo** et disposent de toutes les autorisations de lecture, d’écriture et de modification.

* **Région-Auteur** : comprend les utilisateurs qui disposent d’autorisations de lecture, d’écriture et de modification pour la **région A** et la **région B**.

* **Magasin-Auteur** : comprend les utilisateurs qui disposent d’autorisations de lecture, d’écriture et de modification uniquement pour le **Magasin 1**, le **Magasin 2**, le **Magasin 3** et le **Magasin 4.**

#### Procédure de création de groupes d’utilisateurs, d’utilisateurs et de configuration des listes de contrôle d’accès {#steps-for-creating-user-groups-users-and-setting-up-acls}

>[!NOTE]
>
>Pour savoir comment séparer les projets à l’aide des listes de contrôle d’accès afin que chaque personne ou équipe gère son propre projet, voir **Configuration des listes de contrôle d’accès**.

Suivez les étapes ci-dessous pour créer des groupes, des utilisateurs et modifier les listes de contrôle d’accès en fonction des autorisations :

1. **Création de groupes**

   1. Accédez à **Adobe Experience Manager**.
   1. Cliquez sur **Outils** > **Sécurité** > **Groupes**.
   1. Cliquez sur **Créer un groupe** et saisissez **Global-Auteur** dans **ID**.
   1. Cliquez sur **Enregistrer et fermer**.

   De même, créez deux autres groupes comme **Région-Auteur** et **Magasin-Auteur**.

   ![screen_shot_2018-09-17at34008pm](assets/screen_shot_2018-09-17at34008pm.png)

1. **Création d’utilisateurs et ajout d’utilisateurs à des groupes**

   1. Accédez à **Adobe Experience Manager**.
   1. Cliquez sur **Outils** > **Sécurité** > **Utilisateurs**.
   1. Cliquez sur **Créer un utilisateur** et saisissez **Global-Utilisateur** dans **ID**.
   1. Saisissez le **mot de passe** et confirmez le mot de passe de cet utilisateur.
   1. Cliquez sur le bouton **Groupes** et saisissez le nom du groupe dans **Cliquez sur Groupe**, par exemple, saisissez **Global-Auteur** ajouter **Global-User** à ce groupe spécifique.
   1. Cliquez sur **Enregistrer et fermer**.

   De même, créez deux autres utilisateurs, comme **Région-Utilisateur** et **Magasin-Utilisateur**, puis ajoutez-les à **Région-Auteur** et à **Magasin-Auteur** respectivement.

   >[!NOTE]
   >Il est recommandé de commencer par ajouter des utilisateurs à un groupe, puis d’attribuer des autorisations à chaque groupe d’utilisateurs.

   ![screen_shot_2018-09-17at34412pm](assets/screen_shot_2018-09-17at34412pm.png)

1. **Ajouter tous les groupes aux contributeurs**

   1. Accédez à **Adobe Experience Manager**.
   1. Cliquez sur **Outils** > **Sécurité** > **Groupes**.
   1. Cliquez sur **Contributeurs** dans la liste, puis cliquez sur **Membres** .
   1. Cliquez sur le bouton **Groupe** par exemple **Global-Auteur**, **Region-Auteur,** et **Store-Author** aux contributeurs.
   1. Cliquez sur **Enregistrer et fermer**.

1. **Accès aux autorisations pour chaque groupe**

   1. Accédez à l’*utilisateur admin* et utilisez cette interface utilisateur pour modifier les autorisations de différents groupes.
   1. Recherchez **Global-Auteur** et cliquez sur l’onglet **Autorisations**, comme illustré dans la figure ci-dessous.
   1. De même, vous pouvez accéder aux autorisations pour **Région-Auteur** et **Magasin-Auteur**.

   ![screen_shot_2018-09-18at73523am](assets/screen_shot_2018-09-18at73523am.png)

1. **Modification des autorisations pour chaque groupe**

   **Pour Global-Auteur :**

   1. Accédez à l’onglet **Autorisations**
   1. Accédez à ***/content/screens/demo*** et cochez toutes les autorisations
   1. Accédez à ***/content/screens/demo/locations*** et cochez toutes les autorisations
   1. Accédez à ***/content/screens/demo/locations/région-a*** et cochez toutes les autorisations. De même, vérifiez les autorisations pour **`region-b`**.

   Consultez la figure suivante pour comprendre les étapes :
   ![screen_shot_2018-09-18at115752am](assets/screen_shot_2018-09-18at115752am.png)

   L’exemple suivant montre que la variable **Global-User** a accès au **Canal global**, et les deux **Région A** et **Région B** avec les quatre magasins, à savoir **Magasin 1**, **Magasin 2**, **Magasin 3**, et **Magasin 4**.

   ![Global](assets/global.gif)

   **Pour Region-Auteur :**

   1. Accédez à l’onglet **Autorisations**
   1. Accédez à ***/content/screens/demo*** et cochez uniquement les autorisations de **lecture**.
   1. Accédez à ***/content/screens/demo/locations*** et cochez uniquement les autorisations de **Lecture**.
   1. Accédez à ***/content/screens/demo/channels*** et désélectionnez les autorisations pour **Global** canal.
   1. Accédez à ***/content/screens/demo/locations***/***région-a*** et cochez toutes les autorisations. De même, vérifiez les autorisations pour **`region-b`**.

   Consultez l’image suivante pour comprendre les étapes :

   ![screen_shot_2018-09-18at125158pm](assets/screen_shot_2018-09-18at125158pm.png)

   L’exemple suivant montre que l’utilisateur de la région a accès aux deux **Région A** et **Région B**, avec les quatre magasins, à savoir : **Magasin 1**, **Magasin 2**, **Magasin 3**, et **Magasin 4**, mais n’accède pas à la variable **Global** Canal.

   ![région](assets/region.gif)

   **Pour Magasin-Auteur :**

   1. Accédez à l’onglet **Autorisations**
   1. Accédez à ***/content/screens/demo*** et cochez uniquement les autorisations de **lecture**.
   1. Accédez à ***/content/screens/demo/locations*** et cochez uniquement les autorisations de **Lecture**.
   1. Accédez à ***/content/screens/demo/channels*** et désélectionnez les autorisations pour **Global** canal.
   1. Accédez à ***/content/screens/demo/locations/région-a*** et cochez uniquement les autorisations de **Lecture**. De même, cochez uniquement la variable **Lecture** autorisations pour **`region-b`**.
   1. Accédez à ***/content/screens/demo/locations***/***région-a /magasin-1*** et cochez toutes les autorisations. De même, vérifiez les autorisations pour **magasin-2,** magasin-3 et **magasin-4**.

   Consultez l’image suivante pour comprendre les étapes :

   ![screen_shot_2018-09-18at12415pm](assets/screen_shot_2018-09-18at12415pm.png)

   L’exemple suivant montre que la variable **Store-User** a accès uniquement à **Magasin 1**, **Magasin 2**, **Magasin 3**, et **Magasin 4**, mais ne dispose pas des autorisations nécessaires pour accéder à la variable **Global** ou région (**Région A** et **Région B**).

   ![store](assets/store.gif)

>[!NOTE]
>
>Pour en savoir plus sur la configuration des autorisations, voir [Configuration des listes de contrôle d’accès](setting-up-acls.md).
