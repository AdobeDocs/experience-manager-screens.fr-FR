---
title: Vue d’ensemble et configurations de l’architecture des rendus adaptatifs
description: Découvrez la vue d’ensemble de l’architecture et les configurations dans CRXDE Lite pour les rendus adaptatifs dans AEM Screens.
exl-id: 0419b9c6-3c27-4a61-84ff-a6fe697e773f
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 100%

---

# Rendus adaptatifs : présentation et configurations de l’architecture {#adaptive-renditions}

## Présentation {#introduction}

Les rendus adaptatifs permettent aux appareils de sélectionner automatiquement le meilleur rendu pour un appareil en fonction des règles définies par le client ou la cliente. Les appareils téléchargent et lisent automatiquement le rendu le plus approprié d’une ressource en fonction de ces règles, ce qui permet aux clientes et aux clients de se concentrer uniquement sur la conception de l’expérience *principale*.

## Objectif {#objective}

En tant que développeur AEM Screens, vous pouvez désormais configurer des rendus de ressources spécifiques pour un appareil afin qu’ils soient téléchargés et lus automatiquement sans avoir à créer manuellement toutes les variations de contenu. Configurez les rendus adaptatifs avant qu’un auteur ou une autrice de contenu puisse utiliser cette fonctionnalité dans un canal AEM Screens.

## Vue d’ensemble de l’architecture {#architectural-overview}

Les rendus adaptatifs reposent sur l’idée de posséder plusieurs rendus d’une ressource nommés selon une convention de nommage spécifique. La décision de lire un rendu spécifique est prise en évaluant les expressions de requête multimédia qui ne peuvent être résolues que sur les appareils dotés des fonctionnalités attendues.

La possibilité d’avoir un modèle de dénomination des rendus associé définit une règle de mappage des rendus, telle que portrait ou paysage, comme illustré ci-dessous. Après avoir calculé toutes les expressions disponibles, le lecteur Screens collecte les modèles de dénomination des règles correspondantes. Les modèles sont utilisés pour rechercher les rendus corrects pendant la lecture de la séquence en recherchant les modèles dans les noms de rendu.

![image](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## Ajout d’une propriété de mappage de rendu au projet Screens {#rendition-mapping-new}

Pour activer la fonction Rendus adaptatifs, les règles de mappage suivantes doivent être présentes et la configuration tenant compte du contexte (CA) peut être résolue pour les canaux et les affichages.

>[!NOTE]
>Pour en savoir plus sur les configurations basées sur le contenu, rendez-vous [ici](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html).

Suivez les étapes ci-dessous pour configurer l’installation :

1. Accédez à **CRXDE Lite**. Vérifiez si la configuration **rendition-mapping** existe dans `/conf/screens/sling:configs/rendition-mapping`, comme illustré dans la figure ci-dessous.

   >![image](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

   >[!IMPORTANT]
   >Si vous avez installé le dernier pack de fonctionnalités 202109, la structure de nœud **rendition-mapping** est préremplie dans `/conf/screens/sling:configs/rendition-mapping` dans CRXDE Lite. Consultez les [Notes de mise à jour du pack de fonctionnalités 202109](/help/user-guide/release-notes-fp-202109.md) pour obtenir des informations sur le dernier pack de fonctionnalités.
   >Pour les projets existants, assurez-vous que la configuration **rendition-mapping** est associée au projet Screens. Consultez [Ajout d’un mappage de rendu à un projet existant](#rendition-mapping-existing) pour en savoir plus.

### Ajout d’une propriété de mappage de rendu à un projet existant {#rendition-mapping-existing}

1. Accédez à **CRXDE Lite**.

1. Définissez explicitement l’association de mappage de rendu en ajoutant la propriété `sling:configRef` pointant vers `/conf/screens` au nœud de contenu du projet, comme illustré sur la figure ci-dessous.

   ![image](/help/user-guide/assets/adaptive-renditions/renditon-mapping2.png)


## Ajout de règles de mappage de rendu {#add-rendition-mapping-rules}

Suivez les étapes ci-dessous pour ajouter un nœud dans le mappage de rendu :

1. Accédez à ce chemin `/conf/screens/sling:configs/rendition-mapping` à partir de **CRXDE Lite**.
1. Créez un nœud sous **rendition-mapping**. Cliquez avec le bouton droit sur **rendition-mapping** et cliquez sur **Créer** > **Créer un nœud**, comme illustré ci-dessous.

   ![Image](/help/user-guide/assets/adaptive-renditions/add-node1.png)

1. Saisissez le **nom** de votre règle de mappage, par exemple **règle1**, et le **Type** de nœud, **`nt:unstructured`**, dans la boîte de dialogue **Créer un nœud**. Cliquez sur **OK**.

   ![Image](/help/user-guide/assets/adaptive-renditions/add-node2.png)


1. Ajoutez la propriété d’expression avec la valeur contenant l’expression de la requête.

   >[!NOTE]
   >Pour en savoir plus, voir [Utilisation de la syntaxe de requête multimédia](https://developer.mozilla.org/fr/docs/Web/CSS/CSS_media_queries/Using_media_queries).

   Cliquez sur la **règle1** que vous avez créée, puis saisissez l’**expression** dans **Nom** et **(orientation:landscape)** dans **Valeur**, comme illustré ci-dessous. Cliquez sur **Ajouter**.

   ![Image](/help/user-guide/assets/adaptive-renditions/add-node3.png)

1. Ajoutez la propriété motif avec la valeur contenant le modèle de dénomination de rendu.

   >[!NOTE]
   >La valeur définie dans la propriété du modèle est mise en correspondance avec le nouveau rendu de la ressource et est sélectionnée, si l’expression est évaluée comme « true ».

   Pour ajouter la propriété de modèle, cliquez sur la **règle1** que vous avez créée, puis saisissez le **modèle** dans **Nom** et **landscape** dans **Valeur**, comme illustré ci-dessous. Cliquez sur **Ajouter**.

   ![Image](/help/user-guide/assets/adaptive-renditions/add-node4.png)

1. Cliquez sur **Enregistrer tout** et vous verrez les propriétés sous le nœud que vous avez créé dans **rendition-mapping**.

   ![image](/help/user-guide/assets/adaptive-renditions/add-node5.png)

## Étapes suivantes {#next-steps}

Après avoir ajouté les propriétés et les règles de rendition-mapping, vous pouvez configurer vos ressources en tant qu’auteur ou autrice de contenu. Vous pouvez également utiliser des rendus adaptatifs et migrer vos appareils pour que les réseaux de grande taille utilisent cette fonctionnalité dans vos canaux AEM Screens. Consultez [Utiliser des rendus adaptatifs dans AEM Screens](/help/user-guide/using-adaptive-renditions.md) pour plus d’informations.
