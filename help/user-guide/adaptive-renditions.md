---
title: Rendus adaptatifs dans AEM Screens
description: Cette page décrit comment utiliser les rendus adaptatifs dans AEM Screens.
index: false
source-git-commit: 0a870f337f69f3379abb15dac504ee8e8355bc98
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 1%

---

# Rendus adaptatifs {#adaptive-renditions}

## Présentation {#introduction}

Les rendus adaptatifs permettent aux appareils de sélectionner automatiquement le meilleur rendu pour un appareil en fonction des règles définies par le client. Les périphériques téléchargent et lisent automatiquement le rendu le plus approprié d’une ressource en fonction de ces règles, ce qui permet aux clients de se concentrer uniquement sur la conception de l’expérience *main*.

## Objectif {#objective}

En tant qu’auteur de contenu AEM Screens, vous pouvez désormais configurer des rendus de ressources spécifiques à l’appareil pour qu’ils soient téléchargés et lus automatiquement sans avoir à créer manuellement toutes les variations de contenu.

Ainsi, si vous avez déployé divers appareils, l’utilisation de cette fonctionnalité permet à l’appareil de télécharger et de lire automatiquement le rendu le plus approprié d’une ressource en fonction des règles.

## Présentation de l’architecture {#architectural-overview}

Les rendus adaptatifs sont basés sur l’idée d’avoir plusieurs rendus de ressources nommés selon une convention d’affectation des noms spécifique. La décision de lire un rendu spécifique est prise en évaluant les expressions de requête multimédia qui ne peuvent être résolues que sur les appareils dotés des fonctionnalités attendues. La possibilité d’avoir un modèle de dénomination de rendu associé définit une règle de mappage de rendu. Après avoir calculé toutes les expressions disponibles, le lecteur Screens collecte les modèles de dénomination correspondant aux règles correspondantes. Les modèles sont utilisés pour rechercher les rendus corrects pendant la lecture de la séquence en recherchant les modèles dans les noms de rendu.


## Configuration de la configuration pour l’utilisation des rendus adaptatifs {#setup-adaptive-renditions}

Pour activer la fonction Rendus adaptatifs , les règles de mappage doivent être présentes et la configuration de l’autorité de certification peut être résolue pour les canaux et les affichages :

1. Vérifiez si la configuration du mappage de rendu existe dans `JCR`. Cette structure de noeud est prérenseignée pour tous les derniers Feature Packs.

   >[!NOTE]
   >Cette structure de noeud est prérenseignée pour tous les derniers Feature Packs.


1. Assurez-vous que la configuration du mappage de rendu est associée au projet Screens.

   * Chaque nouveau projet créé avec l’assistant de projet Screens contient une référence pointant vers la configuration du mappage de rendu.

   * Dans une ancienne version des projets Screens, l’association doit être explicitement définie en ajoutant la propriété `sling:configRef` pointant vers `/conf/screens` au noeud de contenu du projet.

## Stratégie de migration {#migration-strategy}

>[!IMPORTANT]
>Pour les réseaux volumineux, il est recommandé d’effectuer la migration graduellement afin d’atténuer les risques, car la fonctionnalité introduira des modifications dans le format de stockage de manifeste et de fichier.

Pour activer la fonction, ajoutez au moins une règle de mappage et assurez-vous que la configuration du mappage de rendu peut être résolue dans le contexte des affichages et des canaux :

1. Ajoutez des règles de mappage de rendu.
1. Créez un dossier pour les nouveaux canaux et ajoutez une référence pointant vers la configuration du mappage de rendu.
1. Créez des canaux qui remplacent les anciens et téléchargez des rendus.
1. Réaffecter les affichages aux nouveaux canaux.
1. Ajoutez une référence aux affichages/emplacements migrés pointant vers la configuration du mappage de rendu.
1. Répétez les étapes 3, 4 et 5 pour tous les autres canaux et affichages.
1. Une fois la migration terminée, supprimez toutes les références de configuration des canaux/affichages/emplacements et ajoutez-en une seule au noeud de contenu du projet.

## Configuration de l’auteur et de la publication {#setup-author-publish}

Suivez les étapes ci-dessous pour configurer l’auteur et la publication :

* Le mappage de rendu doit être répliqué manuellement.

* Les rendus de ressources ne sont pas répliqués par défaut. Toutes les ressources appropriées doivent être répliquées manuellement.


## Ajout de règles de mappage de rendu {#adding-rendition-mapping-rules}

1. Pour ajouter une règle de mappage, vous devez créer un noeud de type `nt:unstructured` sous le noeud de mappage de rendu.

1. Ajoutez la propriété expression avec la valeur contenant l’expression de la requête.

   >[!NOTE]
   >Pour en savoir plus, consultez la section [Utilisation de la syntaxe de requête multimédia](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries) .

1. Ajoutez la propriété pattern avec la valeur contenant le modèle de nommage du rendu qui sera sélectionné, si l’expression est évaluée sur true.

## Téléchargement de rendus {#upload-renditions}

1. Créez une version de la ressource qui convient le mieux à l’affichage de la signalétique, par exemple `portrait orientation`.

1. Choisissez le modèle de dénomination du rendu, par exemple,`portrait`.

1. Renommez le fichier de ressource afin qu’il contienne le modèle, par exemple `my_asset_portrait.png`.

1. Téléchargez le rendu en cliquant sur le bouton Ajouter le rendu dans la barre d’outils.


## Étapes suivantes {#next-steps}

Une fois que vous avez chargé les rendus, vous pouvez désormais utiliser des rendus adaptatifs dans vos canaux AEM Screens.
