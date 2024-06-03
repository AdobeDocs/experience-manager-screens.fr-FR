---
title: Configuration et dépannage de la lecture vidéo
description: Découvrez comment déboguer et résoudre les problèmes liés à la lecture vidéo dans votre canal pour AEM Screens.
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: troubleshoot
feature: Channels, Interactive
role: Developer
level: Intermediate
exl-id: dfdd58b6-689b-47ca-9459-9c205f1841eb
source-git-commit: 8dde26d36847fb496aed6d4bf9732233116b5ea6
workflow-type: tm+mt
source-wordcount: '799'
ht-degree: 80%

---

# Configuration et dépannage de la lecture vidéo {#video-playback-configuration-and-troubleshooting}

Lorsque vous téléchargez une vidéo dans la gestion des ressources numériques et l’ajoutez à votre canal, il se peut que vous rencontriez des problèmes de lecture de la vidéo dans le lecteur AEM Screens.

Les sections ci-après décrivent comment déboguer et résoudre les problèmes liés à la lecture vidéo dans votre canal.

## Rendus de la gestion des actifs numériques (DAM) {#dam-renditions}

Une fois la vidéo chargée dans le canal, AEM doit commencer à créer des rendus. Les vidéos sont répertoriées sous la catégorie Ressources.

Pour visionner la vidéo, procédez comme suit :

1. Accédez à votre vidéo, par exemple `http://localhost:4502/assets.html/content/dam/we-retail/en/videos`.
1. Cliquez sur la vidéo, développez le menu supérieur gauche, puis cliquez sur **Rendus**.

Il doit y avoir différents rendus (MP4 ou M4V).

S’il n’existe aucun rendu, assurez-vous que FFMPEG est installé sur le système d’exploitation sur lequel AEM est en cours d’exécution.

>[!CAUTION]
>
>S’il n’existe aucun rendu, assurez-vous que FFMPEG est installé sur le système d’exploitation sur lequel AEM est en cours d’exécution.
>
>Cliquez sur [here](https://www.ffmpeg.org/download.html) pour installer FFMPEG.

## Ressources vidéo {#video-assets}

S’il n’y a pas d’attribut source sous la vidéo, il est possible que la vidéo n’ait pas été transcodée. Si la vidéo est transcodée correctement, elle s’affiche dans le tableau de bord, comme illustré ci-après :

Vérifiez que FFMPEG est installé et les profils vidéo.

![chlimage_1-2](assets/chlimage_1-2.png)

### Vérifier le profil vidéo {#checking-video-profile}

1. Accédez au **Profil vidéo**, à savoir `http://localhost:4502/etc/dam/video.html`, et cliquez sur **Charger la vidéo de test**.

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. Chargez une vidéo de test et cliquez sur **OK** pour commencer le transcodage.

   Si la vidéo transcodée échoue, développez la sortie FFMPEG pour comprendre les erreurs dans la sortie console de FFMPEG.

   ![chlimage_1-4](assets/chlimage_1-4.png)

   En revanche, si la vidéo est transcodée correctement, il est possible de télécharger le fichier transcodé.

   ![chlimage_1-5](assets/chlimage_1-5.png)

   >[!NOTE]
   >
   >Avant de l’ajouter à un canal, veillez à laisser suffisamment de temps pour le transcodage de la vidéo (l’indicateur « Nouvelle » et non « Traitement en cours » doit s’afficher).

### Vérification du profil avec un composant vidéo {#checking-profile-with-a-video-component}

Vérifiez la liste des profils de la conception de page si le composant vidéo n’est pas correctement configuré.

1. Accédez à votre canal et cliquez sur le mode **Conception**.

   ![chlimage_1-6](assets/chlimage_1-6.png)

1. Cliquez sur la vidéo et ouvrez la boîte de dialogue **Modifier**. Ouvrez l’onglet **Profils**.

   >[!NOTE]
   >Cliquez sur différents profils (au moins le profil &quot;H.264 haute qualité&quot; doit être présent).

### Vérifier la vidéo dans le lecteur web {#checking-the-video-in-the-web-player}

Utilisez le **lecteur web** `http://localhost:4502/content/mobileapps/cq-screens-player/firmware.html/content/screens/we-retail/locations/demo/flagship/single/device0` pour valider la lecture dans les navigateurs (Chrome et Safari). Chrome est utilisé sur les appareils Android™, tandis que Safari est le navigateur d’OS X et d’iOS.

Si la vidéo n’est pas lue sous Safari, elle ne fonctionnera pas dans les lecteurs OS X et iOS. Ce problème est probablement un problème de codage et la vidéo doit être réencodée.

Pour utiliser un workflow de gestion des ressources numériques pour créer des rendus Full HD, procédez comme suit :

1. Accédez à l’*administration des modèles de workflow*, à savoir `http://localhost:4502/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`.
1. Cliquez sur le modèle **Ressource de mise à jour de Screens**.
1. Cliquez sur **Démarrer le workflow** dans la barre d’actions.
1. Dans la boîte de dialogue **Exécuter le workflow**, cliquez sur votre ressource vidéo dans la **Payload**.
1. Cliquez sur **Exécuter**.

>[!NOTE]
>
>Patientez un certain temps pour créer les rendus, mais après quelques secondes/minutes (selon la taille de la vidéo), rechargez le lecteur web sur Safari.

#### Dépanner l’indicateur de politique de lecture automatique {#troubleshooting-autoplay-policy-flag}

Si le lecteur AEM Screens sélectionne la vidéo mais ne l’affiche pas, vous devez résoudre les problèmes liés à l’indicateur de politique de lecture automatique.

Pour résoudre le problème d’indicateur de politique de lecture automatique de Google, procédez comme suit :

1. Accédez à ***chrome://flags/#autoplay-policy***
1. Changez la **politique de lecture automatique** de **par défaut** à **aucun geste requis de la part de l’utilisateur**

1. Relancez votre navigateur Web et mettez à jour le lecteur

>[!NOTE]
>
>Pour en savoir plus sur les bonnes pratiques à appliquer aux utilisateurs ayant recours aux nouvelles stratégies de lecture automatique dans Chrome. Voir *Modification de la stratégie de lecture automatique* at `https://developers.google.com/web/updates/2017/09/autoplay-policy-changes#webaudio`.

### Synchroniser des vidéos sur plusieurs lecteurs {#syncing-video-across-multiple-players}

Pour lire des vidéos en mode synchrone sur plusieurs appareils, utilisez la stratégie absolue pour la séquence dont fait partie la vidéo.

#### Conditions requises {#requirements}

* 2+ joueurs identiques
* Matériel similaire, dans l’idéal
* Topologie de réseau identique (les lecteurs sont connectés à un serveur NTP, qui synchronise leurs horloges système internes)

#### Configurer la stratégie absolue {#setting-up-the-absolute-strategy}

La stratégie absolue :

* Calcule l’heure d’ancrage (minuit du jour en cours).
* Calcule la durée de la séquence (somme de la durée de tous ses éléments).
* Calcule, à tout moment, l’élément qui doit être en cours de lecture et l’élément suivant à l’aide de la formule sequence_remaining_time = (current_time - anchor_time) % sequence_duration (temps restant de la séquence = (heure actuelle - heure d’ancrage) % durée de la séquence).

Pour configurer une stratégie absolue, procédez comme suit :

1. Accédez à votre canal de création et cliquez sur le composant de séquence, comme illustré ci-dessous.
1. Ouvrez sa boîte de dialogue de configuration.
1. Modifiez la **Stratégie** et ajoutez « absolue ».

   ![chlimage_1-8](assets/chlimage_1-8.png)

   >[!NOTE]
   >Le système d’exploitation des lecteurs doit posséder la même horloge.

**Aligner les horloges sur OS X** Pour aligner les horloges sur OS X, procédez comme suit :

1. Ouvrez les préférences **Date et heure** pour chaque lecteur OS X.
1. Activez l’option **Définir automatiquement la date et l’heure**.
1. Collez value 0.pool.ntp.org, 1.pool.ntp.org, 2.pool.ntp.org, 3.pool.ntp.org, time.apple.com dans la liste déroulante ou exécutez simplement *sudo ntpdate -u -v 0.pool.ntp.org*.
1. Démarrez deux lecteurs ou plus.

Il peut s’écouler un certain temps avant que les lecteurs ne commencent une nouvelle séquence synchronisée.
