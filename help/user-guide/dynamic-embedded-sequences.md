---
title: Utilisation d’une séquence incorporée dynamique
description: Découvrez comment implémenter des séquences incorporées dynamiques dans votre projet AEM Screens.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 3208d058-0812-44e1-83e3-b727b384876a
source-git-commit: dcaaa1c7ab0a55cecce70f593ed4fded8468130b
workflow-type: tm+mt
source-wordcount: '2451'
ht-degree: 98%

---

# Utilisation d’une séquence incorporée dynamique {#using-dynamic-embedded-sequence}

L’utilisation de séquences incorporées dynamiques couvre les rubriques suivantes :

* **Présentation**
* **Utilisation de l’expérience incorporée dynamique dans AEM Screens**
* **Affichage des résultats**
* **Restriction des utilisateurs et modification des listes de contrôle d’accès**

## Vue d’ensemble {#overview}

Les ***séquences incorporées dynamiques*** sont créées pour les projets de grande envergure qui respectent la hiérarchie enfant-parent, où l’enfant est référencé dans un dossier d’emplacement et non dans un dossier de canal. Cela permet à l’utilisateur d’incorporer une séquence à l’intérieur d’un canal par ***Rôle de canal***. Cela permet à l’utilisateur ou l’utilisatrice de définir des espaces réservés spécifiques à un emplacement pour différents bureaux à l’aide d’une séquence incorporée dans un canal principal.

Lorsque vous attribuez un canal à un affichage, vous avez la possibilité de spécifier le chemin d’accès de l’affichage. Ou vous pouvez indiquer le rôle du canal, qui désignera un canal réel en fonction du contexte.

Pour utiliser la séquence incorporée dynamique, il faut affecter un canal par ***rôle de canal***. Le rôle du canal définit le contexte de l’affichage. Le rôle cible diverses actions ; il est indépendant du canal qui remplit le rôle. Cette section décrit un cas d’utilisation qui définit les canaux par rôle et comment vous pouvez appliquer ce contenu dans un canal global. Vous pouvez également considérer le rôle comme un identifiant pour l’attribution ou comme un alias pour le canal dans le contexte.

### Avantages de l’utilisation de séquences incorporées dynamiques {#benefits-of-using-dynamic-embedded-sequences}

Le placement d’un canal de séquence à l’intérieur d’un emplacement au lieu du dossier de canaux permet aux auteurs et autrices locaux ou régionaux de modifier le contenu qui les intéresse. Il permet également de ne pas modifier des canaux situés à un niveau supérieur de la hiérarchie.

Référencer un *canal par rôle* vous permet de créer une version locale d’un canal. Cela permet de résoudre dynamiquement un contenu spécifique à un emplacement et vous permet également de créer un canal global qui utilise le contenu pour les canaux spécifiques à un emplacement.

>[!NOTE]
>
>**Séquences incorporées ou Séquences incorporées dynamiques**
>
>Une séquence incorporée dynamique est semblable à une séquence incorporée, mais permet aux personnes de suivre une hiérarchie où les modifications et les mises à jour effectuées sur un canal sont propagées aux autres canaux liés. Elle respecte une hiérarchie parent-enfant et comprend également des ressources telles que des images ou des vidéos.
>
>Les ***séquences incorporées dynamiques*** permettent d’afficher du contenu spécifique à l’emplacement, tandis que les ***séquences incorporées*** affichent uniquement un diaporama général du contenu. De plus, lors de la configuration des séquences incorporées dynamiques, configurez le canal à l’aide du rôle et du nom du canal. Reportez-vous aux étapes ci-dessous pour la mise en œuvre.
>
>Pour en savoir plus sur l’implémentation de séquences incorporées, voir [Séquences incorporées](embedded-sequences.md) dans AEM Screens.

L’exemple suivant fournit une solution en se concentrant sur les termes clés suivants :

* un ***canal de séquence principal*** pour la séquence globale ;
* des composants de ***séquence incorporée dynamique*** pour chaque partie localement personnalisable de la séquence ;
* des ***canaux de séquence individuels*** dans les emplacements respectifs avec un *rôle* dans l’affichage correspondant au **rôle *du composant de séquence incorporée dynamique***.

>[!NOTE]
>
>Pour en savoir plus sur l’attribution des canaux, voir **[Attribution des canaux](channel-assignment.md)** dans la section Création de la documentation relative à AEM Screens.

## Utilisation d’une séquence incorporée dynamique {#using-dynamic-embedded-sequence-2}

La section suivante explique la création d’une séquence incorporée dynamique dans un canal AEM Screens.

### Conditions préalables {#prerequisites}

Avant de commencer à implémenter cette fonctionnalité, assurez-vous que les conditions préalables suivantes sont satisfaites avant de commencer à implémenter des séquences incorporées dynamiques :

* Créer un projet AEM Screens (dans cet exemple, **Demo**).
* Créez un canal **global** dans le dossier **Canaux**.
* Ajoutez du contenu à votre canal **Global** (*Consultez **Resources.zip**pour connaître les ressources appropriées*).

L’image suivante montre le projet **Démo** avec le canal **global** dans le dossier **Canaux**.
![screen_shot_2018-09-07at21032pm](assets/screen_shot_2018-09-07at21032pm.png)

### Ressources {#resources}

Vous pouvez télécharger les ressources suivantes (images et les ajouter aux ressources) et les utiliser comme contenu de canal à des fins de démonstration.

[Obtenir le fichier](assets/resources.zip)

>[!NOTE]
>
>Pour plus d’informations sur la création d’un projet et la création d’un canal de séquence, reportez-vous aux ressources ci-dessous :
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
>Lors de l’implémentation de séquences incorporées dynamiques, prêtez attention aux champs **Nom** et **Titre** lors de la création de canaux sous chaque emplacement. Suivez attentivement les instructions relatives à la nomenclature.

1. **Créez deux dossiers Emplacements.**

   Accédez au dossier **Emplacements** dans votre projet AEM Screens et créez deux dossiers d’emplacement : **Région A** et **Région B**.

   >[!NOTE]
   >
   >Lors de la création du dossier d’emplacement **Région A**, veillez à saisir le **Titre** **Région A**. Vous pouvez laisser le champ **Nom** vide, afin que le nom **région-a** soit automatiquement sélectionné.
   >
   >Il en va de même pour la création du dossier d’emplacement **Région B**, comme illustré ci-dessous :

   ![screen_shot_2018-09-13at23212pm](assets/screen_shot_2018-09-13at23212pm.png)

   >[!NOTE]
   >Pour savoir comment créer un emplacement, voir **[Création et gestion des emplacements](managing-locations.md)**.

1. **Créez deux emplacements et un canal sous chaque dossier d’emplacement.**

   1. Accédez à **Demo** > **Emplacements** > **Région A**.
   1. Cliquez sur **Région A**, puis cliquez sur **+Créer** dans la barre d’actions.
   1. Cliquez sur **Emplacement** dans l’assistant avec le **Titre** **Magasin 1**. De même, créez un autre emplacement dans l’assistant intitulé **Magasin 2** avec le **Titre** **Magasin 2**. Vous pouvez laisser le champ **Nom** vide lors de la création de **Magasin 1** et **Magasin 2**.
   1. Répétez l’étape (b) et cliquez maintenant sur **Canal de séquence** dans l’assistant. Saisissez le **Titre** **Région A** et le **Nom** **région** pour ce canal.

   >[!CAUTION]
   >
   >Lors de la création du canal **Région A**, saisissez le **Titre** **Région A** et le **Nom** **région**.

   ![screen_shot_2018-09-13at22857pm](assets/screen_shot_2018-09-13at22857pm.png)

   De même, créez deux emplacements dans la **Région B**, intitulés **Magasin 3** et **Magasin 4**. Créez également un **Canal de séquence** avec pour **Titre** **Région B** et pour **Nom** **région**.

   >[!CAUTION]
   >
   >Veillez à utiliser le même nom pour les canaux créés dans **Région A** et **Région B**, à savoir **région**.

   ![screen_shot_2018-09-13at24408pm](assets/screen_shot_2018-09-13at24408pm.png)

1. **Créez Affichage et Canal sous chaque emplacement.**

   1. Accédez à **Demo** > **Emplacements** > **Région A** > **Magasin 1**.
   1. Cliquez sur **Magasin 1** puis cliquez sur **+Créer** dans la barre d’actions.
   1. Cliquez sur **Affichage** dans l’assistant et créez **`Store1Display`**.
   1. Répétez l’étape (b) et cliquez cette fois sur **Canal de séquence** dans l’assistant. Saisissez le **Titre** **`Store1Channel`** et le **Nom** **magasin**.

   >[!CAUTION]
   >
   >Lorsque vous créez un canal de séquence, vous pouvez choisir librement le **titre** du canal, mais le **Nom** doit être identique dans tous les canaux locaux.
   >Dans cet exemple, les canaux situés sous **Région A** et **Région B** partagent le **Nom** **région** et les canaux sous **`Store 1`**, **`Store 2`**, **`Store 3`** et **`Store 4`** partagent le **Nom** **magasin**.

   ![screen_shot_2018-09-19at120206pm](assets/screen_shot_2018-09-19at120206pm.png)

   De même, créez un affichage **`Store2Display`** et un canal **`Store2Channel`** sous **`Store `2** (avec le nom **magasin**).

   >[!NOTE]
   >Veillez à utiliser le même nom pour les canaux créés dans **`Store 1`** et **`Store 2`**, à savoir **magasin**.

   ![screen_shot_2018-09-19at120329pm](assets/screen_shot_2018-09-19at120329pm.png)

   Suivez les étapes précédentes pour créer un canal et un affichage dans **`Store 3`** et **`Store 4`** sous **Région B**. Là encore, veillez à utiliser le même **Nom**, à savoir **magasin** lors de la création des canaux **`Store3Channel`** et **`Store4Channel`** respectivement.

   L’image suivante présente l’affichage et le canal dans **`Store 3`**.

   ![screen_shot_2018-09-19at120448pm](assets/screen_shot_2018-09-19at120448pm.png)

   L’image suivante présente l’affichage et le canal dans **`Store 4`**.

   ![screen_shot_2018-09-19at120552pm](assets/screen_shot_2018-09-19at120552pm.png)

1. **Ajoutez du contenu aux canaux dans leurs emplacements respectifs.**

   Accédez à **Demo** > **Emplacements** > **Région A** > **Région A** et cliquez sur **Modifier** dans la barre d’actions. Faites glisser-déposer les ressources à ajouter au canal.

   >[!NOTE]
   >Vous pouvez utiliser le fichier ***Resources.zip*** de la section **Ressources** ci-dessus pour utiliser les images comme ressources pour le contenu de votre canal.

   ![screen_shot_2018-09-12at12438pm](assets/screen_shot_2018-09-12at12438pm.png)

   De même, accédez à la **Démo** > **Emplacements** > **Région B** > **Région B** et cliquez sur **Modifier** dans la barre d’actions pour faire glisser les ressources vers votre canal, comme illustré ci-dessous :

   ![screen_shot_2018-09-12at13133pm](assets/screen_shot_2018-09-12at13133pm.png)

   Suivez les étapes précédentes et les ressources pour pouvoir ajouter du contenu aux canaux suivants :

   * **`Store1Channel`**
   * **`Store2Channel`**
   * **`Store3Channel`**
   * **`Store4Channel`**

1. **Créer un planning**

   Accédez au dossier **Plannings** et cliquez dessus dans votre projet AEM Screens. Cliquez ensuite sur **Créer** dans la barre d’actions.

   L’image suivante montre le **AdSchedule** créé dans le projet **Démo**.

   ![screen_shot_2018-09-13at33307pm](assets/screen_shot_2018-09-13at33307pm.png)

1. **Attribuer des canaux à une planification**

   1. Accédez à **Demo** > **Plannings** > **AdSchedule** et cliquez sur **Tableau de bord** dans la barre d’actions.
   1. Cliquez sur **+Attribuer le canal** dans le panneau **CANAUX ATTRIBUÉS** pour ouvrir la boîte de dialogue **Attribution de canaux**.
   1. Cliquez sur **Canal de référence** en fonction du chemin d’accès.
   1. Cliquez sur le **Chemin du canal** **Démo** > ***Canaux*** > ***Global***.
   1. Définissez le **rôle du canal** sur **GlobalAdSegment**.
   1. Cliquez sur les **Événements pris en charge** **Chargement initial**, **Écran d’inactivité** et **Interaction utilisateur**.
   1. Cliquez sur **Enregistrer**.

   **Attribution d’un canal par rôle pour la région :**

   1. Cliquez sur **+ Attribuer le canal** dans le panneau **CANAUX ATTRIBUÉS**.
   1. Dans la boîte de dialogue Attribution de canaux, cliquez sur **Canal de référence** en fonction du nom.
   1. Saisissez comme **Nom du canal** **région***.
   1. Définissez le **rôle du canal** sur **RegionAdSegment**.
   1. Cliquez sur **Enregistrer**.

   **Attribution d’un canal par rôle pour le magasin :**

   1. Cliquez sur **+ Attribuer le canal** dans le panneau **CANAUX ATTRIBUÉS**.
   1. Dans la boîte de dialogue Attribution de canaux, sélectionnez **Canal de référence** en fonction du nom.
   1. Saisissez le **Nom du canal** **magasin**.
   1. Définissez le **Rôle du canal** sur **StoreAdSegment**.
   1. Cliquez sur **Enregistrer**.

   L’image suivante montre les canaux attribués par chemin et par rôle.

   ![screen_shot_2018-09-12at21429pm](assets/screen_shot_2018-09-12at21429pm.png)

1. **Configuration d’une séquence incorporée dynamique sur le canal global.**

   Accédez au canal **Global** que vous avez initialement créé dans le projet **Démo**.

   Cliquez sur **Modifier** dans la barre d’actions.

   ![screen_shot_2018-09-13at52754pm](assets/screen_shot_2018-09-13at52754pm.png)

   Dans l’éditeur, faites glisser et déposez deux composants de **séquence incorporée dynamique** dans l’éditeur de canaux.

   Ouvrez les propriétés de l’un des composants et saisissez le **rôle d’attribution de canaux** sous la forme **RegionAdSegment**.

   De même, cliquez sur l’autre composant et ouvrez les propriétés pour saisir le **rôle d’attribution de canaux** **StoreAdSegment**.

   ![channeldisplay4](assets/channeldisplay4.gif)

1. **Attribution d’une planification à chaque affichage**

   1. Accédez à chaque affichage, par exemple **Demo** > **Emplacements** > **Région A** >**Magasin 1** >**`Store1Display`**.
   1. Cliquez sur **Tableau de bord** dans la barre d’actions.
   1. Sur le tableau de bord, cliquez sur les points de suspension **...** dans le panneau **CANAUX ET PLANNINGS ATTRIBUÉS**, puis sur **+Attribuer un planning**.
   1. Cliquez sur le chemin d’accès au planning (par exemple, ici, **Démo** > **Plannings** > **AdSchedule**).
   1. Cliquez sur **Enregistrer**.

## Affichage des résultats {#viewing-the-results}

Une fois que vous aurez configuré les canaux et l’affichage, lancez le lecteur AEM Screens pour afficher le contenu.

>[!NOTE]
>
>Pour en savoir plus sur le lecteur AEM Screens, consultez les ressources suivantes :
>
>* [Télécharger le lecteur AEM Screens](https://download.macromedia.com/screens/)
>* [Utilisation du lecteur AEM Screens](working-with-screens-player.md)


La sortie suivante confirme le contenu de votre canal dans le lecteur AEM Screens, selon le chemin d’affichage.

**Scénario 1** :

Si vous attribuez le chemin d’affichage **Démo** > **Emplacements** > **Région A** > **Magasin 1** > **`Store1Display`**, le contenu suivant s’affiche sur votre lecteur AEM Screens.

![channeldisplay1](assets/channeldisplay1.gif)

**Scénario 1**:

Si vous attribuez le chemin d’affichage **Démo** > **Emplacements** > **Région B** > **Magasin 3** > **`Store3Display`**, le contenu suivant s’affiche sur votre lecteur AEM Screens.

![channeldisplay2](assets/channeldisplay2.gif)

## Restriction des utilisateurs et modification des listes de contrôle d’accès {#restricting-users-and-modifying-the-acls}

Vous pouvez créer des autrices ou des auteurs globaux, régionaux ou locaux afin de pouvoir modifier le contenu qui les concerne sans possibilité de modifier des canaux situés à un niveau supérieur de la hiérarchie.

Modifiez les listes de contrôle d’accès pour pouvoir restreindre l’accès de l’utilisateur ou de l’utilisatrice au contenu en fonction de son emplacement.

### Exemple de cas d’utilisation {#example-use-case}

L’exemple suivant vous permet de créer trois utilisateurs et utilisatrices pour le projet de démonstration ci-dessus.

Les privilèges sont attribués à chaque groupe comme suit :

**Groupes** :

* **Global-Auteur** : comprend les utilisateurs qui ont accès à tous les emplacements et canaux du projet **Demo** et disposent de toutes les autorisations de lecture, d’écriture et de modification.

* **Région-Auteur** : comprend les utilisateurs qui disposent d’autorisations de lecture, d’écriture et de modification pour la **région A** et la **région B**.

* **Magasin-Auteur** : comprend les utilisateurs qui disposent d’autorisations de lecture, d’écriture et de modification uniquement pour le **Magasin 1**, le **Magasin 2**, le **Magasin 3** et le **Magasin 4.**

#### Procédure de création de groupes d’utilisateurs et d’utilisatrices, d’utilisateurs et d’utilisatrices et de configuration des listes de contrôle d’accès {#steps-for-creating-user-groups-users-and-setting-up-acls}

>[!NOTE]
>
>Pour savoir comment séparer les projets à l’aide de listes de contrôle d’accès afin que chaque personne ou équipe gère son propre projet, voir **Configuration des listes de contrôle d’accès**.

Pour créer des groupes, des utilisateurs ou utilisatrices et modifier les listes de contrôle d’accès en fonction des autorisations, procédez comme suit :

1. **Création de groupes**

   1. Accédez à **Adobe Experience Manager**.
   1. Cliquez sur **Outils** > **Sécurité** > **Groupes**.
   1. Cliquez sur **Créer un groupe** et saisissez **Global-Auteur** dans **ID**.
   1. Cliquez sur **Enregistrer et fermer**.

   De même, créez deux autres groupes, tels que **Region-Author** et **Store-Author**.

   ![screen_shot_2018-09-17at34008pm](assets/screen_shot_2018-09-17at34008pm.png)

1. **Création d’utilisateurs et ajout d’utilisateurs à des groupes**

   1. Accédez à **Adobe Experience Manager**.
   1. Cliquez sur **Outils** > **Sécurité** > **Utilisateurs ou utilisatrices**.
   1. Cliquez sur **Créer un utilisateur** puis, dans **ID**, saisissez **Global-User**.
   1. Saisissez le **mot de passe** et confirmez le mot de passe de cette personne.
   1. Cliquez sur l’onglet **Groupes** et saisissez le nom du groupe dans **Cliquer sur un groupe**, par exemple, saisissez **Global-Auteur/Autrice** pour ajouter **Global-Utilisateur/Utilisatrice** à ce groupe spécifique.
   1. Cliquez sur **Enregistrer et fermer**.

   De même, créez deux autres utilisateurs, tels que **Region-User** et **Store-User**, puis ajoutez-les respectivement à **Region-Author** et **Store-Author**.

   >[!NOTE]
   >Il est recommandé de commencer par ajouter des utilisateurs à un groupe, puis d’attribuer des autorisations à chaque groupe d’utilisateurs.

   ![screen_shot_2018-09-17at34412pm](assets/screen_shot_2018-09-17at34412pm.png)

1. **Ajouter tous les groupes aux contributeurs**

   1. Accédez à **Adobe Experience Manager**.
   1. Cliquez sur **Outils** > **Sécurité** > **Groupes**.
   1. Cliquez sur **Contributeurs et contributrices** dans la liste, puis sur l’onglet **Membres**.
   1. Cliquez sur le **Groupe**, comme **Global-Auteur/Autrice**, **Région-Auteur/Autrice**, et **Magasin-Auteur/Autrice** pour les contributeurs et contributrices.
   1. Cliquez sur **Enregistrer et fermer**.

1. **Accès aux autorisations pour chaque groupe**

   1. Accédez à l’*administration des utilisateurs et utilisatrices* et utilisez cette interface d’utilisation pour modifier les autorisations de différents groupes.
   1. Recherchez **Global-Auteur/Autrice** et cliquez sur l’onglet **Autorisations**, comme illustré dans la figure ci-dessous.
   1. De même, vous pouvez accéder aux autorisations pour **Région-Auteur** et **Magasin-Auteur**.

   ![screen_shot_2018-09-18at73523am](assets/screen_shot_2018-09-18at73523am.png)

1. **Modification des autorisations pour chaque groupe**

   **Pour Global-Auteur :**

   1. Accédez à l’onglet **Autorisations**
   1. Accédez à ***/content/screens/demo*** et cochez toutes les autorisations
   1. Accédez à ***/content/screens/demo/locations*** et cochez toutes les autorisations
   1. Accédez à ***/content/screens/demo/locations/région-a*** et cochez toutes les autorisations. De même, vérifiez les autorisations pour **`region-b`**.

   Consultez la figure suivante pour comprendre les étapes :
   ![screen_shot_2018-09-18at115752am](assets/screen_shot_2018-09-18at115752am.png)

   L’exemple suivant montre que la variable **Global-User/Utilisatrice** a accès au **Canal global**. Et qu’elle a accès aux **Région A** et **Région B** avec les quatre magasins, à savoir **Magasin 1**, **Magasin 2**, **Magasin 3**, et **Magasin 4**.

   ![Global](assets/global.gif)

   **Pour Region-Auteur :**

   1. Accédez à l’onglet **Autorisations**
   1. Accédez à ***/content/screens/demo*** et cochez uniquement les autorisations de **lecture**.
   1. Accédez à ***/content/screens/demo/locations*** et cochez uniquement les autorisations de **Lecture**.
   1. Accédez à ***/content/screens/demo/channels*** et désélectionnez les autorisations pour le canal **Global**.
   1. Accédez à ***/content/screens/demo/locations***/***région-a*** et cochez toutes les autorisations. De même, vérifiez les autorisations pour **`region-b`**.

   Consultez l’image suivante pour comprendre les étapes :

   ![screen_shot_2018-09-18at125158pm](assets/screen_shot_2018-09-18at125158pm.png)

   L’exemple suivant montre que la variable Région-Utilisateur/utilisatrice a accès aux **Région A** et **Région B**. Et qu’elle a accès aux quatre magasins, à savoir **Magasin 1**, **Magasin 2**, **Magasin 3**, et **Magasin 4**, mais pas au canal **global**.

   ![région](assets/region.gif)

   **Pour Magasin-Auteur :**

   1. Accédez à l’onglet **Autorisations**
   1. Accédez à ***/content/screens/demo*** et cochez uniquement les autorisations de **lecture**.
   1. Accédez à ***/content/screens/demo/locations*** et cochez uniquement les autorisations de **Lecture**.
   1. Accédez à ***/content/screens/demo/channels*** et désélectionnez les autorisations pour le canal **Global**.
   1. Accédez à ***/content/screens/demo/locations/région-a*** et cochez uniquement les autorisations de **Lecture**. De même, vérifiez uniquement les autorisations de **Lecture** pour la **`region-b`**.
   1. Accédez à ***/content/screens/demo/locations***/***région-a /magasin-1*** et cochez toutes les autorisations. De même, vérifiez les autorisations pour **magasin-2, magasin-3** et **magasin-4**.

   Consultez l’image suivante pour comprendre les étapes :

   ![screen_shot_2018-09-18at12415pm](assets/screen_shot_2018-09-18at12415pm.png)

   L’exemple suivant montre que la variable **Magasin-Utilisateur/Utilisatrice** a accès uniquement à **Magasin 1**, **Magasin 2**, **Magasin 3**, et **Magasin 4**. Toutefois, elle ne dispose pas des autorisations nécessaires pour accéder au canal **global** ou de région (**Région A** et **Région B**).

   ![store](assets/store.gif)

>[!NOTE]
>
>Pour plus d’informations sur la configuration des autorisations, voir [Configuration des listes de contrôle d’accès](setting-up-acls.md).
