---
title: Configuration et dépannage de la lecture vidéo
description: Découvrez comment déboguer et résoudre les problèmes liés à la lecture de vidéos dans votre canal pour AEM Screens.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
feature: Channels, Interactive
role: Developer
level: Intermediate
exl-id: dfdd58b6-689b-47ca-9459-9c205f1841eb
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 38%

---

# Configuration et dépannage de la lecture vidéo {#video-playback-configuration-and-troubleshooting}

Lorsque vous téléchargez une vidéo dans la gestion des ressources numériques et que vous l’ajoutez à votre canal, il se peut que vous rencontriez des problèmes de lecture de la vidéo dans le lecteur AEM Screens.

Les sections suivantes décrivent comment déboguer et dépanner la lecture vidéo dans votre canal.

## Rendus de la gestion des actifs numériques (DAM) {#dam-renditions}

Une fois la vidéo chargée dans le canal, AEM doit commencer à créer des rendus. Les vidéos sont répertoriées sous la catégorie Ressources.

Pour visionner la vidéo, procédez comme suit :

1. Accédez à votre vidéo, par exemple `http://localhost:4502/assets.html/content/dam/we-retail/en/videos`.
1. Cliquez sur la vidéo, développez le menu supérieur gauche, puis cliquez sur **Rendus**.

Il doit y avoir différents rendus (MP4 ou M4V).

S’il n’existe aucun rendu, vérifiez que vous avez installé ffmpeg sur le système d’exploitation où AEM est exécuté.

>[!CAUTION]
>
>S’il n’existe aucun rendu, vérifiez que vous avez installé ffmpeg sur le système d’exploitation où AEM est exécuté.
>
>Cliquez [ici](https://www.ffmpeg.org/download.html) pour installer ffmpeg.

## Ressources vidéo {#video-assets}

S’il n’y a pas d’attribut source sous la vidéo, il est possible que la vidéo n’ait pas été transcodée. Si la vidéo est correctement transcodée, elle s’affiche dans le tableau de bord, comme illustré ci-dessous :

Vérifiez que ffmpeg est installé dans les profils vidéo.

![chlimage_1-2](assets/chlimage_1-2.png)

### Vérification du profil vidéo {#checking-video-profile}

1. Accédez au **Profil vidéo**, à savoir `http://localhost:4502/etc/dam/video.html`, et cliquez sur **Charger la vidéo de test**.

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. Téléchargez une vidéo de test et cliquez sur **Ok** vous pouvez donc commencer le transcodage.

   Si la vidéo transcodée échoue, développez la sortie ffmpeg pour comprendre les erreurs dans la sortie de console de ffmpeg.

   ![chlimage_1-4](assets/chlimage_1-4.png)

   En revanche, si la vidéo est transcodée correctement, il est possible de télécharger le fichier transcodé.

   ![chlimage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >Veillez à laisser suffisamment de temps pour que la vidéo soit transcodée (la nouvelle balise devrait s’afficher au lieu d’être traitée) avant de l’ajouter à n’importe quel canal.

### Vérification du profil avec un composant vidéo {#checking-profile-with-a-video-component}

Vérifiez la liste des profils de la conception de page si le composant vidéo n’est pas correctement configuré.

1. Accédez à votre canal et sélectionnez le **Conception** mode .

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. Sélectionnez la vidéo et ouvrez la boîte de dialogue **Modifier**. Ouvrez le **Profils** .

   >[!NOTE]
   >Sélectionnez différents profils (au moins, un profil H.264 de haute qualité doit être présent).

### Vérification de la vidéo dans le lecteur web {#checking-the-video-in-the-web-player}

Utilisez le **lecteur web** `http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html/content/screens/we-retail/locations/demo/flagship/single/device0`pour valider la lecture dans les navigateurs (Chrome et Safari). Chrome est utilisé sur les appareils Android™ tandis que Safari est le navigateur OS X et iOS.

Si la vidéo ne s’exécute pas sur Safari, elle ne s’exécute pas non plus dans les lecteurs OS X et iOS. Il s’agit probablement d’un problème de codage, et la vidéo doit être réencodée.

Pour utiliser un workflow de gestion des actifs numériques pour créer des rendus Full HD, procédez comme suit :

1. Accédez au *administrateur de modèle de workflow* that `http://localhost:4502/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`.
1. Sélectionnez la variable **Ressources de mise à jour de Screens** modèle.
1. Sélectionner **Démarrer le processus** dans la barre d’actions.
1. Dans la **Exécuter le workflow** , sélectionnez votre ressource vidéo dans la boîte de dialogue **Payload**.
1. Sélectionner **Exécuter**.

>[!NOTE]
>
>Patientez un certain temps pour créer les rendus, mais après quelques secondes/minutes (cela dépend de la taille de la vidéo), rechargez le lecteur web sur Safari.

#### Dépannage de l’indicateur de stratégie de lecture automatique {#troubleshooting-autoplay-policy-flag}

Si le lecteur AEM Screens sélectionne la vidéo mais ne l’affiche pas, résolvez les problèmes liés à l’indicateur Stratégie de lecture automatique .

Suivez les étapes ci-dessous pour résoudre le problème d’indicateur de stratégie de lecture automatique de Google :

1. Accédez à ***chrome://flags/#autoplay-policy***
1. Changez la **politique de lecture automatique** de **par défaut** à **aucun geste requis de la part de l’utilisateur**

1. Relancez votre navigateur web et mettez à jour le lecteur

>[!NOTE]
>
>Pour en savoir plus sur les bonnes pratiques relatives aux expériences utilisateur lors de la mise en oeuvre des nouvelles stratégies de lecture automatique dans Chrome, consultez la documentation pour *Modification de la stratégie de lecture automatique* at `https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#webaudio`.

### Synchronisation des vidéos sur plusieurs lecteurs {#syncing-video-across-multiple-players}

Pour lire des vidéos en mode synchrone sur plusieurs appareils, utilisez la stratégie absolue pour la séquence dont fait partie la vidéo.

#### Conditions requises {#requirements}

* 2+ joueurs identiques
* Matériel similaire, dans l’idéal
* Topologie de réseau identique (les lecteurs sont connectés à un serveur NTP, qui synchronise leurs horloges système internes)

#### Configuration de la stratégie absolue {#setting-up-the-absolute-strategy}

La stratégie absolue :

* Calcule l’heure d’ancrage (minuit du jour en cours).
* Calcule la durée de la séquence (somme de la durée de tous ses éléments).
* À tout moment, il calcule l’élément qui doit être lu actuellement et l’élément suivant en résolvant la séquence _restes_time = (current_time - anchor_time) % sequence_duration.

Pour configurer une stratégie absolue, procédez comme suit :

1. Accédez à l’auteur de votre canal et sélectionnez le composant de séquence comme illustré dans la figure ci-dessous.
1. Ouvrez sa boîte de dialogue de configuration.
1. Modifiez la **Stratégie** et ajoutez « absolue ».

   ![chlimage_1-8](assets/chlimage_1-8.png)

   >[!NOTE]
   >Le système d’exploitation des lecteurs doit posséder la même horloge.

**Alignement des horloges sur OS X** Pour aligner les horloges sur OS X, procédez comme suit :

1. Ouvrir **Date et heure** préférences de chaque zone OS X
1. Activez l’option **Définir automatiquement la date et l’heure**.
1. Collez value 0.pool.ntp.org, 1.pool.ntp.org, 2.pool.ntp.org, 3.pool.ntp.org, time.apple.com dans la liste déroulante ou exécutez simplement *sudo ntpdate -u -v 0.pool.ntp.org*.
1. Démarrez deux lecteurs ou plus.

Il peut s’écouler un certain temps avant que les lecteurs ne commencent une nouvelle séquence synchronisée.
