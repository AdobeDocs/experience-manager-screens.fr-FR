---
title: Rendus adaptatifs dans AEM Screens
description: Cette page décrit la présentation de l’architecture et les configurations pour les rendus adaptatifs dans AEM Screens.
index: false
source-git-commit: f9e10463418ddc44f75c7d6c689298dcba20338f
workflow-type: tm+mt
source-wordcount: '525'
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

## Configuration de la configuration pour l’utilisation des rendus adaptatifs {#setup-adaptive-renditions}

Pour activer la fonction Rendus adaptatifs , les règles de mappage suivantes doivent être présentes et la configuration tenant compte du contexte (CA) peut être résolue pour les canaux et les affichages.

>[!NOTE]
>Pour en savoir plus sur les configurations basées sur le contenu, voir [ici](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html).

Pour configurer la configuration, procédez comme suit :

1. Accédez à **CRXDE Lite**. Vérifiez si la configuration **rendition-mapping** existe dans `JCR`, comme illustré dans la figure ci-dessous.

   >[!NOTE]
   >Cette structure de noeud est prérenseignée pour tous les derniers Feature Packs.

   ![image](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

1. Assurez-vous que la configuration du mappage de rendu est associée au projet Screens.

   * Chaque nouveau projet créé avec l’assistant de projet Screens contient une référence pointant vers la configuration **rendition-mapping**.

      ![image](/help/user-guide/assets/adaptive-renditions/mapping-rules2.png)

   * Dans une ancienne version des projets Screens, vous devez définir explicitement l’association en ajoutant la propriété `sling:configRef` pointant vers `/conf/screens` au noeud de contenu du projet.

      ![image](/help/user-guide/assets/adaptive-renditions/mapping-rules3.png)

## Configuration de l’auteur et de la publication {#setup-author-publish}

Tenez compte des recommandations suivantes dans les sections Création et Publication avant d’utiliser les rendus adaptatifs :

* Le mappage de rendu doit être répliqué manuellement.

* Les rendus de ressources ne sont pas répliqués par défaut. Toutes les ressources appropriées doivent être répliquées manuellement.

## Ajout de règles de mappage de rendu {#add-rendition-mapping-rules}

1. Pour ajouter une règle de mappage, vous devez créer un noeud de type `nt:unstructured` sous le noeud **rendition-mapping** .

1. Ajoutez la propriété expression avec la valeur contenant l’expression de la requête.

   >[!NOTE]
   >Pour en savoir plus, consultez la section [Utilisation de la syntaxe de requête multimédia](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries) .

1. Ajoutez la propriété pattern avec la valeur contenant le modèle de nommage du rendu qui sera sélectionné, si l’expression est évaluée sur true.

   ![image](/help/user-guide/assets/adaptive-renditions/mapping-rules4.png)


## Étapes suivantes {#next-steps}

Une fois que vous avez configuré et chargé les rendus, en tant qu’auteur de contenu, vous pouvez désormais utiliser les rendus adaptatifs et également migrer vos appareils pour les réseaux de grande taille afin de bénéficier de cette fonctionnalité, dans vos canaux AEM Screens. Voir [Utilisation des rendus adaptatifs](/help/user-guide/using-adaptive-renditions.md) pour plus d’informations.
