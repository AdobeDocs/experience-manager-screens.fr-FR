---
title: Rendus adaptatifs dans AEM Screens
description: Cette page décrit la présentation de l’architecture et les configurations pour les rendus adaptatifs dans AEM Screens.
index: false
source-git-commit: fcc7126ac545c80004d718888b39c6477624cd33
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 2%

---


# Rendus adaptatifs : Présentation et configurations de l’architecture {#adaptive-renditions}

## Présentation {#introduction}

Les rendus adaptatifs permettent aux appareils de sélectionner automatiquement le meilleur rendu pour un appareil en fonction des règles définies par le client. Les périphériques téléchargent et lisent automatiquement le rendu le plus approprié d’une ressource en fonction de ces règles, ce qui permet aux clients de se concentrer uniquement sur la conception de l’expérience *main*.

## Objectif {#objective}

En tant que développeur AEM Screens, vous pouvez désormais configurer des rendus de ressources spécifiques à l’appareil pour qu’ils soient téléchargés et lus automatiquement sans avoir à créer manuellement toutes les variations de contenu. Vous devez configurer les rendus adaptatifs pour qu’un auteur de contenu puisse utiliser cette fonctionnalité dans un canal AEM Screens.

Ainsi, si vous avez déployé divers appareils, l’utilisation de cette fonctionnalité permet à l’appareil de télécharger et de lire automatiquement le rendu le plus approprié d’une ressource en fonction des règles.

## Présentation de l’architecture {#architectural-overview}

Les rendus adaptatifs sont basés sur l’idée d’avoir plusieurs rendus de ressources nommés selon une convention d’affectation des noms spécifique. La décision de lire un rendu spécifique est prise en évaluant les expressions de requête multimédia qui ne peuvent être résolues que sur les appareils dotés des fonctionnalités attendues. La possibilité d’avoir un modèle de dénomination de rendu associé définit une règle de mappage de rendu. Après avoir calculé toutes les expressions disponibles, le lecteur Screens collecte les modèles de dénomination correspondant aux règles correspondantes. Les modèles sont utilisés pour rechercher les rendus corrects pendant la lecture de la séquence en recherchant les modèles dans les noms de rendu.

![image](/help/user-guide/assets/adaptive-renditions/adaptive-renditions.png)

## Configuration de la configuration pour l’utilisation des rendus adaptatifs {#setup-adaptive-renditions}

Pour activer la fonction Rendus adaptatifs , les règles de mappage doivent être présentes et la configuration contextuelle résolvable pour les canaux et les affichages :

1. Vérifiez si la configuration du mappage de rendu existe dans `JCR`. Cette structure de noeud est prérenseignée pour tous les derniers Feature Packs.

   >[!NOTE]
   >Cette structure de noeud est prérenseignée pour tous les derniers Feature Packs.

   ![image](/help/user-guide/assets/adaptive-renditions/mapping-rules1.png)

1. Assurez-vous que la configuration du mappage de rendu est associée au projet Screens.

   * Chaque nouveau projet créé avec l’assistant de projet Screens contient une référence pointant vers la configuration du mappage de rendu.

      ![image](/help/user-guide/assets/adaptive-renditions/mapping-rules2.png)

   * Dans une ancienne version des projets Screens, l’association doit être explicitement définie en ajoutant la propriété `sling:configRef` pointant vers `/conf/screens` au noeud de contenu du projet.

      ![image](/help/user-guide/assets/adaptive-renditions/mapping-rules3.png)



## Configuration de l’auteur et de la publication {#setup-author-publish}

Tenez compte des recommandations suivantes dans les sections Création et Publication avant d’utiliser les rendus adaptatifs :

* Le mappage de rendu doit être répliqué manuellement.

* Les rendus de ressources ne sont pas répliqués par défaut. Toutes les ressources appropriées doivent être répliquées manuellement.

## Ajout de règles de mappage de rendu {#add-rendition-mapping-rules}

1. Pour ajouter une règle de mappage, vous devez créer un noeud de type `nt:unstructured` sous le noeud de mappage de rendu.

1. Ajoutez la propriété expression avec la valeur contenant l’expression de la requête.

   >[!NOTE]
   >Pour en savoir plus, consultez la section [Utilisation de la syntaxe de requête multimédia](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries) .

1. Ajoutez la propriété pattern avec la valeur contenant le modèle de nommage du rendu qui sera sélectionné, si l’expression est évaluée sur true.

   ![image](/help/user-guide/assets/adaptive-renditions/mapping-rules4.png)



## Étapes suivantes {#next-steps}

Une fois que vous avez configuré et chargé les rendus, vous pouvez désormais utiliser les rendus adaptatifs dans vos canaux AEM Screens. Pour plus d’informations, voir Utilisation des rendus adaptatifs .
