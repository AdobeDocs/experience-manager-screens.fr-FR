---
title: Canaux hors ligne
description: Découvrez comment le lecteur AEM Screens fournit une prise en charge hors ligne des canaux à l’aide de la technologie ContentSync.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
docset: aem65
feature: Developing Screens
role: Developer
level: Intermediate
exl-id: 5ad1046f-8b64-490b-9966-ce9008180d54
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 50%

---

# Canaux hors ligne {#offline-channels}

Le lecteur Screens fournit une prise en charge hors ligne des canaux à l’aide du ***ContentSync*** technologie.

Les lecteurs utilisent un serveur HTTP local pour diffuser le contenu décompressé.

Lorsqu’un canal est configuré pour s’exécuter *en ligne*, le lecteur diffuse les ressources du canal en accédant au serveur AEM. Cependant, lorsque le canal est configuré pour s’exécuter *hors ligne*, le lecteur diffuse les ressources de canal à partir d’un serveur http local.

Le workflow du processus est le suivant :

1. Parcourez les pages souhaitées.
1. Collectez toutes les ressources associées.
1. Regroupez tout dans un fichier zip.
1. Téléchargez le fichier zip et extrayez-le localement.
1. Afficher une copie locale du contenu.

## Gestionnaires de mise à jour {#update-handlers}

***ContentSync*** utilise des gestionnaires de mise à jour pour analyser et collecter toutes les pages et tous les actifs nécessaires à un projet spécifique. AEM Screens utilise les gestionnaires de mise à jour suivants :

### Options communes {#common-options}

* *type* : type de gestionnaire de mise à jour à utiliser
* *path* : chemin d’accès à la ressource
* *[targetRootDirectory]* : dossier cible dans le fichier zip

<table>
 <tbody>
  <tr>
   <td><strong>Type</strong></td> 
   <td><strong>Description</strong></td> 
   <td><strong>Options</strong></td> 
  </tr>
  <tr>
   <td><code>channels</code></td> 
   <td>collecte un canal</td> 
   <td>extension : extension de la ressource à collecter<br /> [pathSuffix=''] : suffixe à ajouter au chemin du canal<br /> </td> 
  </tr>
  <tr>
   <td><code>clientlib</code></td> 
   <td>collecte la bibliothèque cliente spécifiée</td> 
   <td>[extension=''] : peut être soit css, soit js, pour collecter uniquement la première, soit la seconde</td> 
  </tr>
  <tr>
   <td><code>assetrenditions</code></td> 
   <td>collecte des rendus de ressources</td> 
   <td>[renditions=[]] : liste des rendus à collecter. Défini par défaut sur le rendu d’origine</td> 
  </tr>
  <tr>
   <td><code>copy</code></td> 
   <td>copier la structure spécifiée à partir du chemin ;</td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

### Test de la configuration de ContentSync {#testing-contentsync-configuration}

Suivez les étapes ci-dessous pour tester la configuration de ContentSync :

1. Ouvrez `https://localhost:4502/libs/cq/contentsync/content/console.html`.
1. Cliquez sur votre configuration dans la liste.
1. Cliquez sur **Effacer le cache**.
1. Cliquez sur **Mettre à jour le cache**.
1. Cliquez sur **Télécharger complet**.
1. Extrayez le fichier zip.
1. Démarrez un serveur local dans le dossier extrait.
1. Ouvrez votre page de démarrage et vérifiez l’état de votre application.

## Activation de la configuration hors ligne d’un canal {#enabling-offline-config-for-a-channel}

Pour activer la configuration hors ligne d’un canal, procédez comme suit :

1. Inspectez le contenu du canal et vérifiez s’il est demandé par une instance AEM (en ligne).

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. Accédez au tableau de bord des canaux.
1. Cliquez sur **..** dans le **INFORMATIONS SUR LES CANAUX** Panneau.

   ![chlimage_1-25](assets/chlimage_1-25.png)

1. Accédez aux propriétés du canal.
1. Sous l’onglet (Canal), assurez-vous que la case à cocher est désactivée, puis cliquez sur **Enregistrer et fermer**.

   ![screen_shot_2017-12-19at122422pm](assets/screen_shot_2017-12-19at122422pm.png)

   Avant que le contenu ne soit correctement déployé sur l’appareil, cliquez sur **Mettre à jour le contenu hors ligne**.

   ![screen_shot_2017-12-19at122637pm](assets/screen_shot_2017-12-19at122637pm.png)

   Le statut **Hors ligne** sous **PROPRIÉTÉ** est également mis à jour en conséquence.

   ![screen_shot_2017-12-19at124735pm](assets/screen_shot_2017-12-19at124735pm.png)

1. Inspectez le contenu du canal et vérifiez s’il est demandé par le cache du lecteur local.

   ![chlimage_1-26](assets/chlimage_1-26.png)

>[!NOTE]
>
>Découvrez le modèle des gestionnaires personnalisés de ressources hors ligne. En savoir plus sur les exigences minimales du `pom.xml` pour le projet. Voir [Modèle pour les gestionnaires personnalisés](/help/user-guide/developing-custom-component-tutorial-develop.md#custom-handlers) in **Développement d’un composant personnalisé pour AEM Screens**.
