---
title: Implémentation de Cloud Player
seo-title: Implementing Cloud Player
description: Consultez cette page pour en savoir plus sur l’implémentation de Cloud Player.
seo-description: Follow  this page to learn about the implementation of the Cloud Player.
uuid: eee84286-fa81-475c-ad6f-db2d6cf1fed5
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
discoiquuid: 1be944f0-02ed-48c6-98bc-504d758ff866
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 184168f5-6070-4c33-a2c5-5429061dac75
source-git-commit: 5b64ab8eea274aa85c61311d34b1ce065a5ba601
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 82%

---

# Implémentation de Cloud Player  {#implementing-cloud-player}

AEM Screens propose traditionnellement des applications de lecteur natives distinctes pour différentes plateformes, notamment ChromeOS, Windows, Android et Tizen. Cependant, en réponse aux besoins changeants de nos utilisateurs, nous avons introduit une solution innovante : le lecteur cloud AEM Screens.

Le lecteur cloud représente une différence significative par rapport à nos applications natives précédentes. Il s’agit d’une application web progressive (PWA), hébergée sur un serveur. Grâce à cette approche transformatrice, nos clients disposent d’un lecteur indépendant des plateformes qui s’exécute directement dans un navigateur web.

L’accès au lecteur cloud est aussi simple que de consulter https://player.adobescreens.com. Les utilisateurs et utilisatrices peuvent l’installer sur leur appareil, quelle que soit la plateforme, et profiter d’une expérience de signalétique numérique transparente. La compatibilité du lecteur Cloud dépend de la présence d’un navigateur moderne avec prise en charge des PWA, assurant des performances homogènes sur divers appareils. Dites adieu aux mises à jour manuelles et bonjour à un lecteur qui fournit automatiquement des correctifs et des fonctionnalités, en vous assurant que vous disposez toujours des dernières fonctionnalités à portée de main. Ce passage à un lecteur cloud PWA marque une évolution passionnante de nos offres d’affichage numérique, ce qui le rend plus accessible, polyvalent et convivial que jamais auparavant.

Cette section décrit l’implémentation de Cloud Player.

>[!NOTE]
>
>La compatibilité de Cloud Player requiert un navigateur moderne avec prise en charge de PWA pour garantir des performances homogènes sur divers appareils.

## Installation de Cloud Player {#installing-cloud-player}

L’installation de Cloud Player peut varier selon les plateformes. En règle générale, toute plateforme disposant d’un navigateur moderne peut exécuter l’application Cloud Player en procédant comme suit :

1. Ouvrez le navigateur et saisissez l’[URL de Cloud Player](https://player.adobescreens.com) dans la barre d’adresses.
1. Le navigateur vérifie que Cloud Player peut être installé, puis affiche une icône d’installation dans la barre d’adresses.

   ![image](/help/user-guide/assets/cloud-player-install.png)

1. Cliquez sur l’icône d’installation et sur le bouton d’installation dans la boîte de dialogue de confirmation. Cloud Player est installé en tant qu’application autonome sur votre appareil et peut être lancé à l’aide d’une icône.

>[!NOTE]
>
>### Option d’installation de Cloud Player {#cloud-player-install-option}
>
1. L’option d’installation d’une PWA est également connue sous le nom de fonctionnalité « Ajouter à l’écran d’accueil » ou A2HS. La prise en charge de l’installation de PWA à partir du web varie en fonction du navigateur et de la plateforme.
1. Chaque navigateur comporte des critères différents pour vérifier si l’application PWA peut être ou non installée. En règle générale, le navigateur vérifie ces éléments (plus de détails ici) :
>
* Si l’application dispose d’un fichier JSON manifeste avec un minimum de clés requises pour l’installation de l’application sur la plateforme, c’est-à-dire nom, icônes, start_url, affichage.
* Si l’application comporte un fichier de travail de service avec un listener d’événement de récupération.
* L’application doit être diffusée via https.
>
1. L’option d’installation peut être visible à différents emplacements dans différents navigateurs et types d’appareils. Certains navigateurs peuvent masquer l’icône d’installation dans la barre de menu des options.

## Approvisionnement en bloc de Cloud Player {#bulk-provisioning}

Pour effectuer l’approvisionnement en bloc de Cloud Player sur plusieurs appareils :

1. Choisissez une solution MDM qui prend en charge l’exécution d’un navigateur avec une URL en mode Kiosk.
1. Vous pouvez appliquer les mêmes configurations à tous les appareils en procédant comme suit :

   1. Hébergez config.json sur un serveur de sorte qu’il soit accessible, par exemple : https://&lt;config_server_host>/config.json
   1. Pour installer Cloud Player et appliquer les configurations hébergées, utilisez l’URL de Cloud Player comme : https://player.adobescreens.com?playerConfigAddress=https://&lt;config_server_host>.
   1. L’application Cloud Player recherche config.json à la racine de &lt;config_server_host>, analyse le fichier config.json pour obtenir les configurations personnalisées et appliquer ces configurations.
   1. Ces configurations seront appliquées à chaque rechargement de Player.

## Approvisionnement en bloc sur le système d’exploitation Chrome {#bulk-provisioning-chrome}

Pour en savoir plus sur l’approvisionnement en bloc sur le système d’exploitation Chrome, voir : [Installer Cloud Player sur le système d’exploitation Chrome](https://main--screens-franklin-documentation--hlxscreens.hlx.page/updates/cloud-player/guides/chromeos-install-cloud-player).

## Configuration requise sur les instances AEM {#bulk-provisioning-config-aem}

En fonction du type d’instance AEM, sélectionnez l’un des guides suivants pour activer CORS entre AEM et Cloud Player :
* [AEM On-Promise/AMS](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-onpremandams)
* [AEM Cloud Service](https://main--screens-franklin-documentation--hlxscreens.hlx.live/updates/cloud-player/guides/cors-settings-aem-cs)

>[!NOTE]
>
## Abandon des applications Chrome par Google
>
1. Applications Chrome sur le matériel Chrome OS :
>
Google a activement abandonné les applications Chrome au profit des applications PWA, avec une migration prévue jusqu’en janvier 2025. Par conséquent, l’application du lecteur AEM Screens sur Chrome OS cessera de fonctionner en fonction de la chronologie partagée. Nous exhortons nos clientes et clients qui utilisent actuellement le lecteur Chrome en production à planifier leur transition vers le lecteur cloud Screens.
>
1. Lecteur d’extension Chrome sous Mac, Windows et Linux :
>
En raison du processus d’obsolescence de Google, à partir de Google Chrome version 114, le lecteur d’extension Chrome Screens n’est plus pris en charge. Nous vous conseillons vivement de passer à notre lecteur cloud Screens pour toutes vos exigences de développement et de test.

## Prise en charge hors ligne de la récupération de contenu externe {#offline-support}

Dans divers scénarios d’utilisation, les canaux peuvent nécessiter la récupération de contenu à partir d’une source externe (par exemple, des widgets météorologiques ou des applications d’une seule page intégrées à Commerce) qui ne peuvent pas, par nature, fournir une prise en charge hors ligne. Pour activer la fonctionnalité hors ligne pour ces cas d’utilisation spécifiques, le lecteur cloud prend en charge l’en-tête personnalisé.

Le lecteur cloud utilise une stratégie de mise en cache favorisant le réseau (Network First), ce qui signifie qu’il tente de récupérer du contenu du réseau (puis de mettre à jour le cache avec la dernière version), avant de revenir au contenu mis en cache s’il est disponible. Pour mettre en œuvre la prise en charge hors ligne de cette récupération de contenu, l’en-tête personnalisé doit être inclus dans la requête. Par la suite, la requête avec l’en-tête personnalisé sera mise en cache sur le lecteur, ce qui facilite l’accès hors ligne au contenu tout en conservant la stratégie de mise en cache Network First.

```
// Sample fetch request with the 'X-Cache-Strategy' header
fetch(externalUrl, {
  headers: {
    'X-Cache-Strategy': 'external-cache'
  }
})
  .then(response => {
    // Handle the response, which may be from the network or cache.
    // Your logic here.
  })
  .catch(error => {
    // Handle any errors that may occur during the fetch operation.
    // Your error handling logic here.
  }); 
```

## Feedback

Nous apprécions vos commentaires ! Faites-nous part de ce que vous pensez via ce [formulaire](https://forms.office.com/r/MQXX9JsuEd).
