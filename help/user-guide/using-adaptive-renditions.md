---
title: Utilisation des rendus adaptatifs dans AEM Screens
description: Découvrez comment utiliser les rendus adaptatifs dans AEM Screens.
exl-id: e7f68ed4-73c3-492a-b33a-dd915ef1f8be
source-git-commit: 2a51258ffe7b969962378dcd0558bd001b616ba1
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 100%

---

# Utilisation des rendus adaptatifs dans AEM Screens {#adaptive-renditions}

## Présentation {#introduction}

Les rendus adaptatifs permettent aux appareils de cliquer automatiquement sur le meilleur rendu pour un appareil en fonction des règles définies par le client ou la cliente. Les appareils téléchargent et lisent automatiquement le rendu le plus approprié d’une ressource en fonction de ces règles. Cela permet aux clientes et clients de se concentrer sur la conception de la *principale* expérience.

## Objectif {#objective}

En tant qu’auteur ou autrice de contenu AEM Screens, vous pouvez désormais configurer des rendus de ressources spécifiques pour un appareil afin qu’ils soient téléchargés et lus automatiquement sans avoir à créer manuellement toutes les variations de contenu.
Une fois qu’un développeur ou qu’une développeuse ajoute les propriétés et les règles de mappage de rendu, vous pouvez appliquer le mappage de rendu aux ressources et les inclure ensuite dans un canal AEM Screens.

>[!IMPORTANT]
>Avant de commencer à utiliser les rendus adaptatifs, dans un canal AEM Screens, Adobe recommande d’en savoir plus sur la vue d’ensemble et la configuration de l’architecture de cette fonctionnalité. Voir [Rendus adaptatifs : vue d’ensemble et configurations de l’architecture](/help/user-guide/adaptive-renditions.md).

## Utilisation de rendus adaptatifs dans les canaux {#using-adaptive-renditions}

>[!NOTE]
>Après avoir ajouté la [propriété de mappage de rendu au projet Screens](/help/user-guide/adaptive-renditions.md#rendition-mapping-new) et les [règles de mappage de rendu](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules), en tant qu’auteur ou autrice de contenu, vous pouvez appliquer les rendus à vos ressources.

### Application de rendu aux ressources {#apply-renditions-assets}

Pour appliquer des rendus aux ressources que vous souhaitez utiliser dans le canal Tour Screens, procédez comme suit.

1. Accédez au dossier **Ressources** dans votre instance AEM.
1. Créez une version de la ressource qui convient le mieux à l’affichage de la signalétique, par exemple `seahorse.jpg`.
1. Choisissez le modèle de dénomination du rendu, par exemple `landscape`, similaire à ce qui a été défini dans la propriété **motif** dans **CRXDE Lite**. Pour plus d’informations, voir [Ajout de règles de mappage de rendu](/help/user-guide/adaptive-renditions.md#add-rendition-mapping-rules).
1. Cliquez sur **Ajouter le rendu** pour charger le rendu, comme illustré dans la figure ci-dessous.

   ![image](/help/user-guide/assets/adaptive-renditions/manage-pub-asset2.png)

1. Cliquez sur le fichier de ressource renommé. Le rendu que vous ajoutez doit contenir le modèle (défini à l’étape 3), par exemple `seahorse-landscape.png`.
1. Lorsque vous avez ajouté la ressource, cliquez dessus, puis sur **Gérer la publication** dans la barre d’actions pour la publier.

   ![image](/help/user-guide/assets/adaptive-renditions/manage-pub-asset1.png)

   >[!NOTE]
   >Pour en savoir plus sur la gestion de la publication et la diffusion de mises à jour de contenu de l’instance de création vers l’instance de publication vers l’appareil, voir [Mise à jour de contenu à la demande](https://experienceleague.adobe.com/fr/docs/experience-manager-screens/user-guide/authoring/content-updates/on-demand-content).

## Stratégie de migration {#migration-strategy}

>[!IMPORTANT]
>Pour les réseaux volumineux, Adobe recommande que la migration soit réalisée progressivement afin d’atténuer les risques. Cela est dû au fait que la fonction peut introduire des modifications dans le format de stockage de manifeste et de fichier. L’ajout de `sling:configRef` à l’ensemble du projet implique la mise à jour de tous les lecteurs vers le pack de fonctionnalités 6.5.9. Si vous avez mis à jour certains lecteurs, ajoutez `sling:configRef` uniquement aux dossiers d’affichages, d’emplacements ou de canaux dont tous les lecteurs ont été mis à jour vers le pack de fonctionnalités 6.5.9.

Le diagramme suivant illustre la stratégie de migration pour les réseaux de taille importante :

![image](/help/user-guide/assets/adaptive-renditions/migration-strategy1.png)

Pour activer la fonction, ajoutez au moins une règle de mappage et assurez-vous que la configuration du mappage de rendu peut être résolue dans le contexte des affichages et des canaux. Pour réaliser la migration, procédez comme suit :

1. Ajoutez les [Règles de mappage de rendu](/help/user-guide/adaptive-renditions.md).
1. Créez un dossier pour les nouveaux canaux et ajoutez une référence pointant vers la configuration du mappage de rendu.
1. Créez des canaux pour remplacer les anciens et chargez des rendus.
1. Réaffectez les affichages aux nouveaux canaux.
1. Ajoutez une référence aux affichages ou aux emplacements migrés pointant vers la configuration du mappage de rendu.
1. Répétez les étapes 3, 4 et 5 pour tous les autres canaux et affichages.

   >[!NOTE]
   >Une fois la migration terminée, veillez à supprimer toutes les références de configuration des canaux, affichages et emplacements, et à en ajouter une seule au nœud de contenu du projet.
