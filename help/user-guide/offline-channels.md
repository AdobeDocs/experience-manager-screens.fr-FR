---
title: Canaux hors ligne
seo-title: Canaux hors ligne
description: 'Le lecteur AEM Screens fournit une prise en charge hors ligne des canaux grâce à la technologie ContentSync. Suivez cette page pour en savoir plus sur les gestionnaires de mise à jour et pour activer la configuration hors ligne d’un canal.  '
seo-description: 'Le lecteur AEM Screens fournit une prise en charge hors ligne des canaux grâce à la technologie ContentSync. Suivez cette page pour en savoir plus sur les gestionnaires de mise à jour et pour activer la configuration hors ligne d’un canal.  '
uuid: 18b9d175-ff26-42db-86aa-5ea978909f71
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: bd572743-652f-4fc5-8b75-a3c4c74536f4
docset: aem65
translation-type: ht
source-git-commit: f25176be89424059b8c51296969f069687328536
workflow-type: ht
source-wordcount: '481'
ht-degree: 100%

---


# Canaux hors ligne {#offline-channels}

Le lecteur Screens fournit une prise en charge hors ligne des canaux grâce à la technologie ***ContentSync***.

Les lecteurs utilisent un serveur http local pour diffuser le contenu décompressé.

Quand un canal est configuré de manière à s’exécuter *en ligne*, le lecteur met à disposition les ressources de canal en accédant au serveur AEM, mais lorsque le canal est configuré de sorte à s’exécuter *hors ligne*, le lecteur met à disposition les ressources de canal d’un serveur http local.

Le workflow du processus est le suivant :

1. Analyser la ou les pages demandées
1. Collecter tous les actifs associés
1. Encapsuler le tout dans un fichier zip
1. Télécharger le zip et l’extraire localement
1. Afficher une copie locale du contenu

## Gestionnaires de mise à jour   {#update-handlers}

***ContentSync*** utilise des gestionnaires de mise à jour pour analyser et collecter toutes les pages et tous les actifs nécessaires à un projet spécifique. AEM Screens utilise les gestionnaires de mise à jour suivants :

### Options communes   {#common-options}

* *type* : type de gestionnaire de mise à jour à utiliser
* *path* : chemin d’accès à la ressource
* *[targetRootDirectory]* : dossier cible dans le fichier zip

<table>
 <tbody>
  <tr>
   <td><strong>Type</strong></td> 
   <td><strong>Description</strong></td> 
   <td><strong>Options </strong></td> 
  </tr>
  <tr>
   <td>channels</td> 
   <td>collecte un canal</td> 
   <td>extension : extension de la ressource à collecter<br /> [pathSuffix=''] : suffixe à ajouter au chemin du canal<br /> </td> 
  </tr>
  <tr>
   <td>clientlib</td> 
   <td>collecte la bibliothèque cliente spécifiée</td> 
   <td>[extension=''] : peut être soit css, soit js, pour collecter uniquement la première, soit la seconde</td> 
  </tr>
  <tr>
   <td>assetrenditions</td> 
   <td>collecte des rendus de ressources</td> 
   <td>[renditions=[]] : liste des rendus à collecter. Défini par défaut sur le rendu d’origine</td> 
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

1. Ouvrez `https://localhost:4502/libs/cq/contentsync/content/console.html`
1. Sélectionner votre configuration dans la liste
1. Cliquer sur Effacer le cache
1. Cliquer sur Mettre à jour le cache
1. Cliquer sur Télécharger tout le module
1. Extraire le fichier zip
1. Démarrer un serveur local dans le dossier extrait
1. Ouvrir la page de démarrage et vérifier l’état de l’application

## Activation de la configuration hors ligne d’un canal   {#enabling-offline-config-for-a-channel}

Suivez les étapes ci-dessous pour activer la configuration hors ligne d’un canal :

1. Inspectez le contenu du canal et vérifiez s’il est demandé par une instance AEM (en ligne).

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. Accédez au tableau de bord du canal et cliquez sur **...** dans le panneau **INFORMATIONS SUR LES CANAUX** pour modifier les propriétés.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Accédez aux propriétés des canaux et assurez-vous que la case à cocher est désactivée dans l’onglet **Canal**. Cliquez sur **Enregistrer et fermer**.

   ![screen_shot_2017-12-19at122422pm](assets/screen_shot_2017-12-19at122422pm.png)

   Avant que le contenu ne soit correctement déployé sur le périphérique, cliquez sur **Mettre à jour le contenu hors ligne**.

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   Le statut **Hors ligne** sous **PROPRIÉTÉ** est également mis à jour en conséquence.

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1. Inspectez le contenu du canal et vérifiez s’il est demandé par le cache du lecteur local.

   ![chlimage_1-26](assets/chlimage_1-26.png)

>[!NOTE]
>
>Pour en savoir plus sur le modèle des gestionnaires de ressources hors ligne personnalisés et sur les exigences minimales relatives au fichier `pom.xml` pour ce projet spécifique, voir [Modèle pour les gestionnaires personnalisés](/help/user-guide/developing-custom-component-tutorial-develop.md#custom-handlers) dans **Développement d’un composant personnalisé pour AEM Screens**.