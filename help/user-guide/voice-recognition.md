---
title: Reconnaissance vocale dans AEM Screens
description: Découvrez la reconnaissance vocale et comment l’utiliser dans AEM Screens.
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 6cf0aa9f-7bac-403f-a113-51727c1f5374
source-git-commit: 6720e20f5254e869bde814bd167730e426d0f8fe
workflow-type: tm+mt
source-wordcount: '1092'
ht-degree: 100%

---

# Reconnaissance vocale dans AEM Screens {#voice-recognition}

>[!IMPORTANT]
>
>**Informations importantes concernant la confidentialité**
>
>Lorsque vous utilisez la fonctionnalité de reconnaissance vocale, suivez toutes les directives légales et éthiques applicables à votre région. Ces instructions incluent, sans s’y limiter, la notification visible aux utilisateurs et utilisatrices finaux indiquant que le lecteur utilise la reconnaissance vocale). Adobe ne reçoit, ne stocke ni ne traite aucune information relative à la voix. Les lecteurs AEM Screens utilisent l’API vocale web standard intégrée au moteur de navigation. En arrière-plan, cette API envoie une forme d’onde de votre discours aux serveurs Google pour la conversion de la parole en texte. Le lecteur compare le texte aux mots-clés configurés.
>
>Pour plus d’informations, consultez l’[article technique de Google relatif à la confidentialité concernant l’API vocale web](https://www.google.com/chrome/privacy/whitepaper.html#speech).


La fonction de reconnaissance vocale permet de modifier le contenu d’un canal AEM Screens par interaction vocale.

Un auteur ou une autrice de contenu peut configurer un affichage pour permettre la reconnaissance vocale. Cette fonctionnalité permet aux clientes et clients d’utiliser la voix pour interagir avec leurs écrans. Certains cas pratiques similaires prévoient la recherche de recommandations de produits dans les magasins ainsi que la commande de plats indiqués dans les menus des restaurants. Cette fonctionnalité accroît l’accessibilité pour les utilisateurs et peut améliorer considérablement l’expérience client.

>[!NOTE]
>Le matériel du lecteur doit prendre en charge l’entrée vocale, par exemple à l’aide d’un microphone.

## Mise en œuvre de la reconnaissance vocale {#implementing}

>[!IMPORTANT]
> La fonction de reconnaissance vocale n’est disponible que sur les lecteurs Chrome OS et Windows.

Pour mettre en œuvre la reconnaissance vocale dans votre projet AEM Screens, activez la reconnaissance vocale pour l’affichage et associez chaque canal à une balise unique afin de déclencher une transition de canal.

La section suivante décrit l’activation et l’utilisation de la fonctionnalité de reconnaissance vocale dans un projet AEM Screens.

## Affichage du contenu en mode Plein écran ou Canal d’écran partagé {#sequence-channel}

Avant d’utiliser une fonctionnalité de reconnaissance vocale, assurez-vous d’avoir un projet et un canal avec du contenu configuré pour le projet.

1. L’exemple suivant présente un projet de démonstration nommé **VoiceDemo** et trois canaux de séquence **Main**, **ColdDrinks** et **HotDrinks**, comme illustré dans la figure ci-dessous.

   ![image](assets/voice-recognition/vr-1.png)

   >[!NOTE]
   >
   >Pour savoir comment créer un canal ou ajouter du contenu à un canal, voir [Création et gestion des canaux](/help/user-guide/managing-channels.md).

   Ou,

   Vous pouvez créer trois canaux de séquence **Main**, **ColdDrinks** et **HotDrinks**, ainsi qu’un canal d’écran partagé 1x2 supplémentaire **SplitScreen**, comme illustré dans la figure ci-dessous.

   ![image](assets/voice-recognition/vr-emb-1.png)

1. Accédez à chacun des canaux et ajoutez du contenu. Par exemple, accédez à **VoiceDemo** > **Canaux** > **Main** et cliquez sur le canal. Cliquez sur **Modifier** dans la barre d’actions, puis ajoutez du contenu (images/vidéos) selon vos besoins. De même, ajoutez du contenu aux canaux **ColdDrinks** et **HotDrinks**.

   Les canaux contiennent maintenant des ressources (images), comme le montrent les figures ci-dessous.

   **Main** :

   ![image](assets/voice-recognition/vr-4.png)

   **ColdDrinks** :

   ![image](assets/voice-recognition/vr-3.png)

   **HotDrinks** :

   ![image](assets/voice-recognition/vr-2.png)

   Si vous avez ajouté le canal d’écrans partagés à votre projet, accédez à **SplitScreen** et glissez-déposez les deux séquences incorporées. Ajoutez des chemins aux canaux **ColdDrinks** et **HotDrinks** comme illustré dans la figure ci-dessous.
   ![image](assets/voice-recognition/vr-emb-6.png)


### Configuration de balises pour les canaux {#setting-tags}

Une fois le contenu ajouté aux canaux, accédez à chacun d’eux et ajoutez les balises appropriées pour déclencher la reconnaissance vocale.

Procédez comme suit pour ajouter des balises à votre canal :

1. Accédez à chacun des canaux et ajoutez du contenu. Par exemple, accédez à **VoiceDemo** > **Canaux** > **Main** et cliquez sur le canal.

1. Cliquez sur **Propriétés** dans la barre d’actions.

   ![image](assets/voice-recognition/vr-5.png)

1. Accédez à l’onglet **Concepts de base** et cliquez sur une balise existante dans le champ **Balises**, ou créez-en une.

   Vous pouvez créer une balise en lui donnant un nouveau nom et appuyer sur la touche `return`, comme illustré dans la figure ci-dessous :

   ![image](assets/voice-recognition/vr-6.png)

   Ou,

   Vous pouvez également créer au préalable des balises à partir de votre instance AEM pour votre projet et les sélectionner également. Une fois que vous avez suivi les étapes décrites dans [Création de balises](#creating-tags), vous pouvez sélectionner la balise à partir de l’emplacement et l’ajouter à votre canal, comme indiqué dans la figure ci-dessous :

   ![image](assets/voice-recognition/vr-tag1.png)

1. De même, ajoutez une balise intitulée **hot** au canal **HotDrinks**.

1. Si vous utilisez un canal d’écran partagé, ajoutez les deux balises (**hot** et **cold**) aux propriétés du canal **SplitScreen**, comme indiqué dans la figure ci-dessous.

   ![image](assets/voice-recognition/vr-emb-7.png)

1. Une fois que vous avez terminé, cliquez sur **Enregistrer et fermer**.


### Création de balises {#creating-tags}

Pour créer des balises, procédez comme suit :

1. Accédez à votre instance AEM.

1. Cliquez sur l’icône Outils > **Balisage**.
   ![image](assets/voice-recognition/vr-7.png)

1. Cliquez sur **Créer** > **Créer un espace de noms**.
   ![image](assets/voice-recognition/vr-tag3.png)

1. Entrez le nom de votre projet, par exemple, **VoiceDemo** et cliquez sur **Créer**.

1. Cliquez sur le projet **VoiceDemo**, puis sur **Créer une balise** dans la barre d’actions.
   ![image](assets/voice-recognition/vr-tag4.png)

1. Saisissez le nom de votre balise, puis cliquez sur **Envoyer**.
   ![image](assets/voice-recognition/vr-tag5.png)

Vous pouvez désormais utiliser ces balises dans votre projet AEM Screens.

### Attribution d’un canal à un affichage et activation de la reconnaissance vocale {#channel-assignment}

1. Créez un affichage dans le dossier **Emplacements**, comme illustré ci-dessous.

   ![image](assets/voice-recognition/vr-loc.png)

   >[!NOTE]
   >Pour savoir comment attribuer un canal à un affichage, voir [Création et gestion des affichages](/help/user-guide/managing-displays.md).

1. Attribuez les canaux **Main**, **ColdDrinks** et **HotDrinks** à votre **LobbyDisplay**. De plus, si vous utilisez le canal **SplitScreen** pour votre projet, assurez-vous de l’attribuer également à l’affichage.

   >[!NOTE]
   >Si vous avez créé un canal d’écran partagé, attribuez aussi le canal **SplitScreen** à votre affichage.

1. Lors de l’attribution des canaux, définissez les propriétés suivantes pour chacun d’eux.

   | **Nom du canal** | **Priorité** | **Événements pris en charge** |
   |---|---|---|
   | Principal | 2 | Charge initiale, écran inactif, minuteur |
   | HotDrinks | 1 | Interaction de l’utilisateur |
   | ColdDrinks | 1 | Interaction de l’utilisateur |
   | SplitScreen | 1 | Interaction de l’utilisateur |

   >[!NOTE]
   >
   >Pour savoir comment attribuer un canal à un affichage, voir [Création et gestion des affichages](/help/user-guide/managing-displays.md).

1. Une fois que vous avez attribué des canaux à un affichage, accédez au **LobbyDisplay** et cliquez sur l’affichage. Cliquez sur **Propriétés** dans la barre d’actions.

1. Accédez à l’onglet **Affichage** et activez l’option **Voix activée** dans **Contenu**.

   ![image](assets/voice-recognition/vr-disp.png)

   >[!IMPORTANT]
   >Il est obligatoire d’activer la fonction de reconnaissance vocale à partir de l’affichage.

### Affichage du contenu dans le lecteur Chrome {#viewing-content}

Lorsque les étapes précédentes sont effectuées, vous pouvez enregistrer votre appareil Chrome pour afficher la sortie.

>[!NOTE]
>Voir [Enregistrement des appareils](device-registration.md).

**Sortie désirée du canal de séquence**

Le canal **Main** lit son contenu. Toutefois, lorsque vous utilisez le mot-clé **hot** (chaud) comme dans *Je voudrais une boisson chaude*, le canal commence à lire le contenu du canal **HotDrinks**.

De même, si vous utilisez un mot-clé **cold** (froid) comme dans *Je voudrais avoir quelque chose de froid*, le canal commence à lire le contenu du canal **ColdDrinks**.

**Sortie désirée du canal SplitScreen**

Le canal **Main** lit son contenu. Toutefois, lorsque vous utilisez les mots-clés **hot** (chaud) et **cold** (froid) ensemble comme dans *Je voudrais voir le menu des boissons chaudes et froides*, le canal commence à lire le contenu du canal **SplitScreen**. Si vous dites *Revenir au menu principal*, le processus revient au canal **Main**.
