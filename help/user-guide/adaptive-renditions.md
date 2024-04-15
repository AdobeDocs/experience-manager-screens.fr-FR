---
title: Présentation et configurations de l’architecture des rendus adaptatifs
description: Découvrez la présentation et les configurations architecturales dans CRXDE Lite pour les rendus adaptatifs dans AEM Screens.
exl-id: 0419b9c6-3c27-4a61-84ff-a6fe697e773f
source-git-commit: 3b44fd920dd6c98ecc0e2b45bf95b81685647c0f
workflow-type: tm+mt
source-wordcount: '622'
ht-degree: 43%

---

# Rendus adaptatifs : présentation et configurations de l’architecture {#adaptive-renditions}

## Présentation {#introduction}

Les rendus adaptatifs permettent aux appareils de sélectionner automatiquement le meilleur rendu pour un appareil en fonction des règles définies par le client. Les périphériques téléchargent et lisent automatiquement le rendu le plus approprié d’une ressource en fonction de ces règles, ce qui permet aux clients de se concentrer uniquement sur la conception de la *main* expérience.

## Objectif {#objective}

En tant que développeur AEM Screens, vous pouvez désormais configurer des rendus de ressources spécifiques pour un appareil afin qu’ils soient téléchargés et lus automatiquement sans avoir à créer manuellement toutes les variations de contenu. Configurez les rendus adaptatifs avant qu’un auteur de contenu ne puisse utiliser cette fonctionnalité dans un canal AEM Screens.

## Aperçu de l’architecture {#architectural-overview}

Les rendus adaptatifs sont basés sur l’idée d’avoir plusieurs rendus d’une ressource nommés selon une convention d’affectation de nom spécifique. La décision de lire un rendu spécifique est prise en évaluant les expressions de requête multimédia qui ne peuvent être résolues que sur les appareils dotés des fonctionnalités attendues.

La possibilité d’avoir un modèle de dénomination de rendu associé définit une règle de mappage de rendu, telle qu’un portrait ou un paysage, comme illustré dans la figure ci-dessous. Après avoir calculé toutes les expressions disponibles, le lecteur Screens collecte les modèles de dénomination correspondant aux règles correspondantes. Les modèles sont utilisés pour rechercher les rendus corrects pendant la lecture de la séquence en recherchant les modèles dans les noms de rendu.

![image](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## Ajout d’une propriété de mappage de rendu au projet Screens {#rendition-mapping-new}

Pour activer la fonction Rendus adaptatifs, les règles de mappage suivantes doivent être présentes et la configuration tenant compte du contexte (CA) peut être résolue pour les canaux et les affichages.

>[!NOTE]
>Pour en savoir plus sur les configurations basées sur le contenu, rendez-vous [ici](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html).

Suivez les étapes ci-dessous pour configurer l’installation :

1. Accédez à **CRXDE Lite**. Vérifiez si la configuration **rendition-mapping** existe dans `/conf/screens/sling:configs/rendition-mapping`, comme illustré dans la figure ci-dessous.

   >![image](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

   >[!IMPORTANT]
   >Si vous avez installé le dernier Feature Pack 202109, le **mapping de rendu** structure de noeud prérenseignée dans `/conf/screens/sling:configs/rendition-mapping` en CRXDE Lite. Voir les [Notes de mise à jour du Feature Pack 202109](/help/user-guide/release-notes-fp-202109.md) pour obtenir des informations sur le dernier Feature Pack.
   >Pour les projets existants, assurez-vous que la configuration **rendu-mapping** est associée au projet Screens. Voir [Ajout d’un mappage de rendu à un projet existant](#rendition-mapping-existing) pour plus d’informations.

### Ajout d’une propriété de mappage de rendu à un projet existant {#rendition-mapping-existing}

1. Accédez à **CRXDE Lite**.

1. Définissez explicitement l’association de mappage de rendu en ajoutant `sling:configRef` pointant vers `/conf/screens` au noeud de contenu du projet, comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/adaptive-renditions/renditon-mapping2.png)


## Ajout de règles de mappage de rendu {#add-rendition-mapping-rules}

Suivez les étapes ci-dessous pour ajouter un nœud dans le mappage de rendu :

1. Accédez à ce chemin `/conf/screens/sling:configs/rendition-mapping` à partir de **CRXDE Lite**.
1. Créez un nœud sous **rendition-mapping**. Clic droit **mapping de rendu** et sélectionnez **Créer** > **Créer un noeud**, comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/adaptive-renditions/add-node1.png)

1. Saisissez le **Nom** pour votre règle de mappage, telle que **rule1** et le noeud **Type** as **`nt:unstructured`** in **Créer un noeud** de la boîte de dialogue Sélectionnez **OK**.

   ![image](/help/user-guide/assets/adaptive-renditions/add-node2.png)


1. Ajoutez la propriété expression avec la valeur contenant l’expression de la requête.

   >[!NOTE]
   >Voir [Utilisation de la syntaxe des requêtes de média](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_media_queries/Using_media_queries) pour en savoir plus.

   Sélectionner **rule1** que vous avez créé et saisissez **expression** in **Nom** et **(orientation:paysage)** in **Valeur**, comme illustré ci-dessous. Sélectionnez **Ajouter**.

   ![image](/help/user-guide/assets/adaptive-renditions/add-node3.png)

1. Ajoutez la propriété motif avec la valeur contenant le modèle de dénomination de rendu.

   >[!NOTE]
   >La valeur définie dans la propriété pattern correspond au nouveau rendu de ressource et est sélectionnée si l’expression est évaluée sur true.

   Pour ajouter la propriété pattern, sélectionnez **rule1** que vous avez créé et saisissez **pattern** in **Nom** et **paysage** in **Valeur**, comme illustré ci-dessous. Sélectionnez **Ajouter**.

   ![image](/help/user-guide/assets/adaptive-renditions/add-node4.png)

1. Sélectionner **Enregistrer tout** et notez les propriétés sous le noeud que vous avez créé sous **mapping de rendu**.

   ![image](/help/user-guide/assets/adaptive-renditions/add-node5.png)

## Étapes suivantes {#next-steps}

Après avoir ajouté des propriétés et des règles de mappage de rendu, vous pouvez configurer vos ressources en tant qu’auteur de contenu. Pour ce faire, utilisez les rendus adaptatifs et migrez également vos appareils pour que les grands réseaux utilisent cette fonctionnalité dans vos canaux AEM Screens. Voir [Utilisation de rendus adaptatifs dans AEM Screens](/help/user-guide/using-adaptive-renditions.md) pour plus d’informations.
