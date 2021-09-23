---
title: Utilisation de rendus adaptatifs dans AEM Screens
description: Cette page décrit comment utiliser les rendus adaptatifs dans AEM Screens.
index: false
source-git-commit: d3a54ed85b9fa2ddf3918161566ba2c82c373be0
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 1%

---

# Utilisation de rendus adaptatifs dans AEM Screens {#adaptive-renditions}

## Présentation {#introduction}

Les rendus adaptatifs permettent aux appareils de sélectionner automatiquement le meilleur rendu pour un appareil en fonction des règles définies par le client. Les périphériques téléchargent et lisent automatiquement le rendu le plus approprié d’une ressource en fonction de ces règles, ce qui permet aux clients de se concentrer uniquement sur la conception de l’expérience *main*.

## Objectif {#objective}

En tant qu’auteur de contenu AEM Screens, vous pouvez désormais configurer des rendus de ressources spécifiques à l’appareil pour qu’ils soient téléchargés et lus automatiquement sans avoir à créer manuellement toutes les variations de contenu.
Une fois qu’un développeur ajoute les propriétés et les règles de mappage de rendu, vous êtes prêt à appliquer le mappage de rendu aux ressources et à les inclure ensuite dans un canal AEM Screens.

>[!IMPORTANT]
>Avant de commencer à utiliser les rendus adaptatifs, dans un canal AEM Screens, il est recommandé d’en savoir plus sur la présentation et la configuration de l’architecture de cette fonctionnalité. Voir Rendus adaptatifs : Présentation et configurations de l’architecture pour plus d’informations.

## Stratégie de migration {#migration-strategy}

>[!IMPORTANT]
>Pour les réseaux volumineux, il est recommandé d’effectuer la migration graduellement afin d’atténuer les risques, car la fonctionnalité introduira des modifications dans le format de stockage de manifeste et de fichier.

Le diagramme suivant illustre la stratégie de migration pour les réseaux volumineux :

![image](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

Pour activer la fonction, ajoutez au moins une règle de mappage et assurez-vous que la configuration du mappage de rendu peut être résolue dans le contexte des affichages et des canaux. Pour migrer, procédez comme suit :

1. Ajoutez [Règles de mappage de rendu](/help/user-guide/adaptive-renditions.md).
1. Créez un dossier pour les nouveaux canaux et ajoutez une référence pointant vers la configuration du mappage de rendu.
1. Créez des canaux qui remplacent les anciens et téléchargez des rendus.
1. Réaffecter les affichages aux nouveaux canaux.
1. Ajoutez une référence aux affichages ou emplacements migrés pointant vers la configuration du mappage de rendu.
1. Répétez les étapes 3, 4 et 5 pour tous les autres canaux et affichages.

   >[!NOTE]
   >Une fois la migration terminée, veillez à supprimer toutes les références de configuration des canaux, affichages et emplacements, et à en ajouter une seule au noeud de contenu du projet.


## Téléchargement de rendus et utilisation de rendus adaptatifs dans un canal AEM Screens {#upload-renditions}

1. Créez une version de la ressource qui convient le mieux à l’affichage de la signalétique, par exemple `portrait orientation`.

1. Choisissez le modèle de dénomination du rendu, par exemple,`portrait`.

1. Renommez le fichier de ressource afin qu’il contienne le modèle, par exemple `my_asset_portrait.png`.

1. Cliquez sur **Ajouter le rendu** pour télécharger le rendu, comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/adaptive-renditions/add-rendition.png)