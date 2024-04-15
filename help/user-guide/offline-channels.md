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
source-git-commit: b65e59473e175e7c1b31fba900bb7e47eff3a263
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 46%

---

# Canaux hors ligne {#offline-channels}

Le lecteur Screens fournit une prise en charge hors ligne des canaux à l’aide du ***ContentSync*** technologie.

Les lecteurs utilisent un serveur http local pour diffuser le contenu décompressé.

Lorsqu’un canal est configuré pour s’exécuter *en ligne*, le lecteur diffuse les ressources du canal en accédant au serveur AEM. Cependant, lorsque le canal est configuré pour s’exécuter *hors ligne*, le lecteur diffuse les ressources de canal à partir d’un serveur http local.

Le workflow du processus est le suivant :

1. Parcourez les pages souhaitées.
1. Collectez toutes les ressources associées.
1. Regroupez tout dans un fichier zip.
1. Téléchargez le fichier zip et extrayez-le localement.
1. Afficher une copie locale du contenu.

## Gestionnaires de mise à jour {#update-handlers}

***ContentSync*** utilise des gestionnaires de mise à jour pour analyser et collecter toutes les pages et tous les actifs nécessaires à un projet spécifique. AEM Screens utilise les gestionnaires de mise à jour suivants :

### Options communes {#common-options}

* *type*: type de gestionnaire de mise à jour à utiliser
* *path*: chemin d’accès à la ressource
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

## Activation de la configuration hors ligne d’un canal {#enabling-offline-config-for-a-channel}

Pour activer la configuration hors ligne d’un canal, procédez comme suit :

1. Inspect le contenu du canal et vérifiez s’il est demandé à une instance AEM (en ligne).

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
>Pour en savoir plus sur le modèle des gestionnaires personnalisés de ressources hors ligne et sur les exigences minimales du `pom.xml` pour ce projet spécifique, voir [Modèle pour les gestionnaires personnalisés](/help/user-guide/developing-custom-component-tutorial-develop.md#custom-handlers) in **Développement d’un composant personnalisé pour AEM Screens**.
