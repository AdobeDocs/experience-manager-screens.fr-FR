---
title: Présentation et configurations de l’architecture des rendus adaptatifs
description: Cette page décrit les configurations et l’aperçu de l’architecture dans CRXDE Lite pour les rendus adaptatifs dans AEM Screens.
exl-id: 0419b9c6-3c27-4a61-84ff-a6fe697e773f
source-git-commit: e5da55eeb5da3d0ef9f21bd47bfec75d660a6a1e
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 3%

---

# Rendus adaptatifs : Présentation et configurations de l’architecture {#adaptive-renditions}

## Présentation {#introduction}

Les rendus adaptatifs permettent aux appareils de sélectionner automatiquement le meilleur rendu pour un appareil en fonction des règles définies par le client. Les périphériques téléchargent et lisent automatiquement le rendu le plus approprié d’une ressource en fonction de ces règles, ce qui permet aux clients de se concentrer uniquement sur la conception de l’expérience *main*.

## Objectif {#objective}

En tant que développeur AEM Screens, vous pouvez désormais configurer des rendus de ressources spécifiques à l’appareil pour qu’ils soient téléchargés et lus automatiquement sans avoir à créer manuellement toutes les variations de contenu. Vous devez configurer les rendus adaptatifs avant qu’un auteur de contenu puisse utiliser cette fonctionnalité dans un canal AEM Screens.

## Présentation de l’architecture {#architectural-overview}

Les rendus adaptatifs sont basés sur l’idée d’avoir plusieurs rendus de ressources nommés selon une convention d’affectation des noms spécifique. La décision de lire un rendu spécifique est prise en évaluant les expressions de requête multimédia qui ne peuvent être résolues que sur les appareils dotés des fonctionnalités attendues.

La possibilité d’avoir un modèle de dénomination de rendu associé définit une règle de mappage de rendu, telle qu’un portrait ou un paysage, comme illustré dans la figure ci-dessous. Après avoir calculé toutes les expressions disponibles, le lecteur Screens collecte les modèles de dénomination correspondant aux règles correspondantes. Les modèles sont utilisés pour rechercher les rendus corrects pendant la lecture de la séquence en recherchant les modèles dans les noms de rendu.

![image](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## Ajout d’une propriété de mappage de rendu au projet Screens {#rendition-mapping-new}

Pour activer la fonction Rendus adaptatifs , les règles de mappage suivantes doivent être présentes et la configuration tenant compte du contexte (CA) peut être résolue pour les canaux et les affichages.

>[!NOTE]
>Pour en savoir plus sur les configurations basées sur le contenu, voir [ici](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html).

Pour configurer la configuration, procédez comme suit :

1. Accédez à **CRXDE Lite**. Vérifiez si la configuration **rendition-mapping** existe dans `/conf/screens/sling:configs/rendition-mapping`, comme illustré dans la figure ci-dessous.

   >![image](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

   >[!IMPORTANT]
   >Si vous avez installé le dernier Feature Pack 202109, la structure de noeud **rendition-mapping** est prérenseignée dans `/conf/screens/sling:configs/rendition-mapping` en CRXDE Lite. Voir [Notes de mise à jour du Feature Pack 202109](/help/user-guide/release-notes-fp-202109.md) pour obtenir des détails sur le dernier Feature Pack.
   >Pour les projets existants, assurez-vous que la configuration **rendu-mapping** est associée au projet Screens. Voir [Ajout d’un mappage de rendu à un projet existant](#rendition-mapping-existing) pour en savoir plus.

### Ajout d’une propriété de mappage de rendu à un projet existant {#rendition-mapping-existing}

1. Accédez à **CRXDE Lite**.

1. Définissez explicitement l’association de mappage de rendu en ajoutant la propriété `sling:configRef` pointant vers `/conf/screens` au noeud de contenu du projet, comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/adaptive-renditions/renditon-mapping2.png)


## Ajout de règles de mappage de rendu {#add-rendition-mapping-rules}

Suivez les étapes ci-dessous pour ajouter un noeud sous Mappage de rendu :

1. Accédez à ce chemin `/conf/screens/sling:configs/rendition-mapping` à partir de **CRXDE Lite**.

1. Créez un noeud sous **rendition-mapping**. Cliquez avec le bouton droit sur **rendu-mapping** et cliquez sur **Créer** —> **Créer un noeud**, comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/adaptive-renditions/add-node1.png)

1. Saisissez le **nom** de votre règle de mappage telle que **rule1** et le noeud **Type** comme **nt:unstructured** dans la boîte de dialogue **Créer un noeud**. Cliquez sur **OK**.

   ![image](/help/user-guide/assets/adaptive-renditions/add-node2.png)


1. Vous devez ajouter la propriété expression avec la valeur contenant l’expression de la requête.

   >[!NOTE]
   >Pour en savoir plus, consultez la section [Utilisation de la syntaxe de requête multimédia](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries) .

   Cliquez sur **règle1** que vous avez créée, puis saisissez **expression** dans **Nom** et **(orientation:paysage)** dans **Valeur**, comme illustré ci-dessous. Cliquez sur **Ajouter**.

   ![image](/help/user-guide/assets/adaptive-renditions/add-node3.png)

1. Ajoutez la propriété pattern avec la valeur contenant le modèle de dénomination de rendu.

   >[!NOTE]
   >La valeur définie dans la propriété pattern sera mise en correspondance avec le nouveau rendu de ressource et sera sélectionnée, si l’expression est évaluée sur true.

   Pour ajouter la propriété de modèle, cliquez sur **règle1** que vous avez créée, puis saisissez **pattern** dans **Nom** et **paysage** dans **Valeur**, comme illustré ci-dessous. Cliquez sur **Ajouter**.

   ![image](/help/user-guide/assets/adaptive-renditions/add-node4.png)

1. Cliquez sur **Enregistrer tout** et vous verrez les propriétés sous le noeud que vous avez créé sous **rendu-mapping**.

   ![image](/help/user-guide/assets/adaptive-renditions/add-node5.png)


## Étapes suivantes {#next-steps}

Une fois que vous avez ajouté des propriétés et des règles de mappage de rendu, en tant qu’auteur de contenu, vous pouvez configurer vos ressources pour utiliser les rendus adaptatifs et également migrer vos appareils pour les réseaux de grande taille afin de profiter de cette fonctionnalité, dans vos canaux AEM Screens. Voir [Utilisation des rendus adaptatifs dans AEM Screens](/help/user-guide/using-adaptive-renditions.md) pour plus d’informations.
