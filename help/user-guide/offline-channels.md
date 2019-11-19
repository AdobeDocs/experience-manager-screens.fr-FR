---
title: Canaux hors connexion
seo-title: Canaux hors connexion
description: 'Le lecteur AEM Screens fournit une prise en charge hors ligne des canaux grâce à la technologie ContentSync. Suivez cette page pour en savoir plus sur les gestionnaires de mise à jour et pour activer la configuration hors ligne d’un canal.  '
seo-description: 'Le lecteur AEM Screens fournit une prise en charge hors ligne des canaux grâce à la technologie ContentSync. Suivez cette page pour en savoir plus sur les gestionnaires de mise à jour et pour activer la configuration hors ligne d’un canal.  '
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: bd572743-652f-4fc5-8b75-a3c4c74536f4
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Canaux hors ligne {#offline-channels}

The Screens player provides offline support for the channels by leveraging the ***ContentSync*** technology.

Les lecteurs utilisent un serveur http local pour diffuser le contenu décompressé.

Quand un canal est configuré de manière à s’exécuter *en ligne*, le lecteur met à disposition les ressources de canal en accédant au serveur AEM, mais lorsque le canal est configuré de sorte à s’exécuter *hors ligne*, le lecteur met à disposition les ressources de canal d’un serveur http local.

Le workflow du processus est le suivant :

1. Analyser la ou les pages demandées
1. Collecter tous les actifs associés
1. Encapsuler le tout dans un fichier zip
1. Télécharger le zip et l’extraire localement
1. Afficher une copie locale du contenu

## Mettre à jour les gestionnaires {#update-handlers}

***ContentSync**utilise des gestionnaires de mise à jour pour analyser et collecter toutes les pages et tous les actifs nécessaires à un projet spécifique.* AEM Screens utilise les gestionnaires de mise à jour suivants :

### Options communes {#common-options}

* *type* : type de gestionnaire de mise à jour à utiliser
* *path* : chemin d’accès à la ressource
* *[targetRootDirectory]*: dossier cible dans le fichier zip

<table>
 <tbody>
  <tr>
   <td><strong>Type</strong></td> 
   <td><strong>Description</strong></td> 
   <td><strong>Options</strong></td> 
  </tr>
  <tr>
   <td>canaux</td> 
   <td>collecte un canal</td> 
   <td>extension : extension de la ressource à collecter<br /> [pathSuffix='''] : suffixe à ajouter au chemin du canal<br /> </td> 
  </tr>
  <tr>
   <td>clientlib</td> 
   <td>collecte de la bibliothèque cliente spécifiée</td> 
   <td>[extension='''] : peut être soit css, soit js, pour collecter uniquement la première, soit la seconde</td> 
  </tr>
  <tr>
   <td>assertions</td> 
   <td>collecte des rendus de ressources</td> 
   <td>[rendus=[]] : liste des rendus à collecter. Valeur par défaut du rendu d’origine</td> 
  </tr>
  <tr>
   <td>Copier</td> 
   <td>copier la structure spécifiée à partir du chemin</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### Test de la configuration de ContentSync {#testing-contentsync-configuration}

Suivez les étapes ci-dessous pour tester la configuration de ContentSync :

1. Ouvrir `https://localhost:4502/libs/cq/contentsync/content/console.html`
1. Sélectionner une config dans la liste
1. Cliquez sur Effacer le cache
1. Cliquez sur Mettre à jour le cache
1. Cliquez sur Télécharger complet
1. Extraire le fichier zip
1. Démarrage d’un serveur local dans le dossier extrait
1. Ouvrir la page de démarrage et vérifier l’état de l’application

## Activation de la configuration hors ligne d’un canal {#enabling-offline-config-for-a-channel}

Suivez les étapes ci-dessous pour activer la configuration hors ligne d’un canal :

1. Inspectez le contenu du canal et vérifiez s’il est demandé par une instance AEM (en ligne).

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. **Accédez au tableau de bord du canal et cliquez sur**... dans le panneau INFORMATIONS **DU** CANAL pour modifier les propriétés.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Accédez aux propriétés des canaux et assurez-vous que la case à cocher est désactivée dans l’onglet **Canal**. Cliquez sur **Enregistrer et fermer**.

   ![screen_shot_2017-12-19at122422pm](assets/screen_shot_2017-12-19at122422pm.png)

   Avant que le contenu ne soit correctement déployé sur l’appareil, cliquez sur **Mettre à jour le contenu hors ligne**.

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   Le statut **Hors ligne** sous **PROPRIÉTÉ** est également mis à jour en conséquence.

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1. Inspectez le contenu du canal et vérifiez s’il est demandé par le cache de lecteur local.

   ![chlimage_1-26](assets/chlimage_1-26.png)

