---
title: Reconnaissance vocale dans AEM Screens
description: Cette page décrit la fonction de reconnaissance vocale d’AEM Screens.
translation-type: tm+mt
source-git-commit: e355d648846034c4762ef8fdcb3e218d868044b6
workflow-type: tm+mt
source-wordcount: '1124'
ht-degree: 34%

---


# Reconnaissance vocale dans AEM Screens {#voice-recognition}

>[!IMPORTANT]
>
>**Informations importantes sur la confidentialité**
>
>Lorsque vous utilisez la fonction de reconnaissance vocale, suivez toutes les directives légales et éthiques applicables à votre région (y compris, mais sans s&#39;y limiter, en indiquant clairement aux utilisateurs finaux que le joueur utilise la reconnaissance vocale). adobe inc, ne reçoit, ne stocke ni ne traite aucune information relative à la voix. Les lecteurs AEM Screens utilisent l’API de parole Web standard intégrée au moteur de navigation. En coulisses, cette API envoie une forme d&#39;onde de votre discours aux serveurs de Google pour la conversion de la parole en texte et ce texte est comparé par le lecteur à des mots-clés configurés.
>
>Consultez le livre blanc sur la confidentialité de [Google sur l’API](https://www.google.com/chrome/privacy/whitepaper.html#speech) de parole Web pour plus d’informations.


La fonction de reconnaissance vocale permet de modifier le contenu dans un canal AEM Screens piloté par l&#39;interaction vocale.

Un auteur de contenu peut configurer un affichage pour permettre la reconnaissance vocale. Cette fonction permet aux clients d’utiliser la parole comme méthode d’interaction avec leurs écrans. Certains cas d&#39;utilisation similaires incluent la recherche de recommandations de produits dans les magasins, la commande d&#39;options de menu dans les restaurants et les dîners. Cette fonctionnalité augmente l’accessibilité pour les utilisateurs et peut améliorer considérablement l’expérience client.

>[!NOTE]
>Le matériel du lecteur doit prendre en charge l’entrée vocale, par exemple à l’aide d’un microphone.

## Mise en œuvre de la reconnaissance vocale {#implementing}

>[!IMPORTANT]
> La fonction de reconnaissance vocale est disponible uniquement sur les lecteurs Chrome OS et Windows.

Pour mettre en oeuvre la reconnaissance vocale dans votre projet AEM Screens, vous devez activer la reconnaissance vocale pour l’affichage et associer chaque canal à une balise unique pour déclencher une transition de canal.

La section suivante décrit comment activer et utiliser la fonction de reconnaissance vocale dans un projet AEM Screens.

## Affichage du contenu en mode Plein écran ou Canal fractionné {#sequence-channel}

Avant d’utiliser la fonction de reconnaissance vocale, assurez-vous d’avoir un projet et un canal avec du contenu configuré pour votre projet.

1. L’exemple suivant présente un projet de démonstration nommé **VoiceDemo** et trois canaux de séquence **Main**, **ColdDrinks** et **HotDrinks**, comme illustré dans la figure ci-dessous.

   ![image](assets/voice-recognition/vr-1.png)

   >[!NOTE]
   >
   >Pour savoir comment créer un canal ou ajouter du contenu à un canal, voir [Création et gestion des canaux](/help/user-guide/managing-channels.md).

   Ou,

   Vous pouvez créer trois canaux de séquence **Main**, **ColdDrinks** et **HotDrinks**, et un canal Split Screens supplémentaire de 1x2 **SplitScreen comme illustré dans la figure ci-dessous.**

   ![image](assets/voice-recognition/vr-emb-1.png)

1. Accédez à chacun des canaux et ajoutez du contenu. Par exemple, accédez à **VoiceDemo** --> **Canaux** --> **Main** et sélectionnez le canal. Cliquez sur **Modifier** dans la barre d’actions pour ouvrir l’éditeur et ajouter du contenu (images/vidéos) selon vos besoins. De même, ajoutez du contenu aux canaux **ColdDrinks** et **HotDrinks**.

   Les canaux contiennent désormais des ressources (images), comme le montrent les figures ci-dessous.

   **Main** :

   ![image](assets/voice-recognition/vr-4.png)

   **ColdDrinks** :

   ![image](assets/voice-recognition/vr-3.png)

   **HotDrinks** :

   ![image](assets/voice-recognition/vr-2.png)

   Si vous avez ajouté le canal Ecrans fractionnés à votre projet, accédez à **SplitScreen** , faites glisser et déposez deux séquences incorporées et ajoutez des chemins d’accès au canal **ColdDrinks** et **HotDrinks** , comme illustré dans la figure ci-dessous.
   ![image](assets/voice-recognition/vr-emb-6.png)


### Configuration de balises pour les canaux {#setting-tags}

Une fois le contenu ajouté aux canaux, vous devez accéder à chacun d’eux et ajouter les balises appropriées pour déclencher la reconnaissance vocale.

Procédez comme suit pour ajouter des balises à votre canal :

1. Accédez à chacun des canaux et ajoutez du contenu. Par exemple, accédez à **VoiceDemo** --> **Canaux** --> **Main** et sélectionnez le canal.

1. Cliquez sur **Propriétés** dans la barre d’actions.

   ![image](assets/voice-recognition/vr-5.png)

1. Accédez à l’onglet **De base** et sélectionnez une balise existante dans le champ **Balises**, ou créez-en une nouvelle.

   Vous pouvez créer une nouvelle balise en entrant un nouveau nom pour la balise et la `return` touche d’accès, comme illustré dans la figure ci-dessous :

   ![image](assets/voice-recognition/vr-6.png)

   Ou,

   Vous pouvez également créer des balises à partir de votre instance AEM au préalable pour votre projet et les sélectionner. Une fois que vous avez suivi les étapes décrites dans la section [Création de balises](#creating-tags), vous pouvez sélectionner la balise à l’emplacement et l’ajouter à votre canal, comme indiqué dans la figure ci-dessous :

   ![image](assets/voice-recognition/vr-tag1.png)

1. De même, ajoutez une balise intitulée **hot** au canal **HotDrinks** .

1. Si vous utilisez un canal Ecrans fractionnés, ajoutez les deux balises (**chaud** et **froid**) aux propriétés du canal **Ecran** fractionné, comme illustré dans la figure ci-dessous.

   ![image](assets/voice-recognition/vr-emb-7.png)

1. Une fois que vous avez terminé, cliquez sur **Enregistrer et fermer**.


### Création de balises {#creating-tags}

Pour créer des balises, procédez comme suit :

1. Accédez à votre instance AEM.

1. Cliquez sur l&#39;icône d&#39;outils —> **Balisage**.
   ![image](assets/voice-recognition/vr-7.png)

1. Click **Create** --> **Create Namespace**.
   ![image](assets/voice-recognition/vr-tag3.png)

1. Entrez le nom de votre projet, par exemple, **VoiceDemo** et cliquez sur **Créer**.

1. Select the **VoiceDemo** project and click **Create Tag** from the action bar.
   ![image](assets/voice-recognition/vr-tag4.png)

1. Saisissez le nom de votre balise, puis cliquez sur **Envoyer**.
   ![image](assets/voice-recognition/vr-tag5.png)

Vous pouvez désormais utiliser ces balises dans votre projet AEM Screens.

### Affectation d’un Canal à un affichage et activation de la reconnaissance vocale {#channel-assignment}

1. Créez un affichage dans le dossier **Emplacements**, comme illustré ci-dessous.

   ![image](assets/voice-recognition/vr-loc.png)

   >[!NOTE]
   >Pour savoir comment attribuer un canal à un affichage, voir [Création et gestion des affichages](/help/user-guide/managing-displays.md).

1. Attribuez les canaux **Main**, **ColdDrinks** et **HotDrinks** à votre **LobbyDisplay**. De plus, si vous utilisez le canal **SplitScreen** pour votre projet, veillez à l’affecter à l’affichage.

   >[!NOTE]
   >Si vous avez créé un canal d’écran partagé, attribuez le canal **SplitScreen** à votre écran.

1. Définissez les propriétés suivantes pour chacun des canaux, lors de l’attribution du canal.

   | **Nom du canal** | **Priorité** | **Événements pris en charge** |
   |---|---|---|
   | Principal | 2 | Charge initiale, écran d’inactivité, minuteur |
   | HotDrinks | 1 | Interaction de l’utilisateur |
   | ColdDrinks | 1 | Interaction de l’utilisateur |
   | SplitScreen | 1 | Interaction de l’utilisateur |

   >[!NOTE]
   >
   >Pour savoir comment attribuer un canal à un affichage, voir [Création et gestion des affichages](/help/user-guide/managing-displays.md).

1. Une fois que vous avez attribué des canaux à un affichage, accédez au **LobbyDisplay** et sélectionnez l’affichage. Sélectionnez **Propriétés** dans la barre d’actions.

1. Accédez à l’onglet **Affichage** et activez l’option **Reconnaissance vocale activée** dans **Contenu**.

   ![image](assets/voice-recognition/vr-disp.png)

   >[!IMPORTANT]
   >Il est obligatoire d’activer la fonction de reconnaissance vocale à partir de l’affichage.

### Affichage du contenu dans le lecteur Chrome {#viewing-content}

Une fois les étapes précédentes terminées, vous pouvez enregistrer votre périphérique chrome pour vue la sortie.

>[!NOTE]
>Voir [Enregistrement des appareils](device-registration.md) pour savoir comment enregistrer un appareil sur un lecteur AEM Screens.

**Sortie désirée pour le Canal de séquence**

Le **canal principal** lit son contenu, mais lorsque vous utilisez des mots avec des mots-clés **chauds** tels que *je voudrais avoir une boisson* chaude, les débuts canaux lisant le contenu du canal **HotDrinks.**

De même, si vous utilisez un mot avec un mot-clé **froid** tel que *je voudrais avoir quelque chose de froid*, le canal début lire le contenu du canal **ColdDrinks** .

**Sortie désirée pour le Canal Ecrans fractionnés**

Le canal **principal** lit son contenu, mais lorsque vous utilisez des mots avec des mots-clés **chauds** et **froids** ensemble, comme *je voudrais voir le menu pour les boissons chaudes et froides, les débuts canaux lisant le contenu du canal SplitScreen.***** Si vous *revenez au menu* principal, il revient au canal principal.





