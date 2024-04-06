---
title: Implémentation de Cloud Player
description: Découvrez la mise en oeuvre du lecteur cloud.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: administering
feature: Administering Screens
role: Admin
level: Intermediate
exl-id: 184168f5-6070-4c33-a2c5-5429061dac75
source-git-commit: 2b865165793b1c0f90f1351518e41096a57ea2ff
workflow-type: tm+mt
source-wordcount: '844'
ht-degree: 36%

---

# Implémentation de Cloud Player  {#implementing-cloud-player}

AEM Screens propose traditionnellement des applications de lecteur natif distinctes pour différentes plateformes, notamment ChromeOS, Windows, Android™ et `Tizen`. Cependant, en réponse aux besoins changeants des utilisateurs, Adobe a introduit une solution innovante : AEM Screens Cloud Player.

Le lecteur cloud représente une différence significative par rapport aux applications natives précédentes d’Adobe. Il s’agit d’une application web progressive (PWA), hébergée sur un serveur. Cette approche transformative permet aux clients d’avoir un lecteur indépendant de la plateforme qui s’exécute directement dans un navigateur web.

L’accès au lecteur cloud est aussi simple que la visite `https://player.adobescreens.com`. Les utilisateurs et utilisatrices peuvent l’installer sur leur appareil, quelle que soit la plateforme, et profiter d’une expérience de signalétique numérique transparente. La compatibilité du lecteur Cloud dépend de la présence d’un navigateur moderne avec prise en charge des PWA, assurant des performances homogènes sur divers appareils. Dites adieu aux mises à jour manuelles et bonjour à un lecteur qui fournit automatiquement des correctifs et des fonctionnalités, en vous assurant que vous disposez toujours des dernières fonctionnalités à portée de main. Ce passage à un lecteur cloud PWA marque une évolution passionnante dans les offres d’affichage numérique de l’Adobe, ce qui le rend plus accessible, polyvalent et convivial que jamais auparavant.

Cette section décrit l’implémentation de Cloud Player.

>[!NOTE]
>
>La compatibilité de Cloud Player requiert un navigateur moderne avec prise en charge de PWA pour garantir des performances homogènes sur divers appareils.

## Installation de Cloud Player {#installing-cloud-player}

L’installation de Cloud Player peut varier selon les plateformes. En règle générale, toute plateforme disposant d’un navigateur moderne peut exécuter l’application Cloud Player en procédant comme suit :

1. Ouvrez le navigateur et saisissez l’[URL de Cloud Player](https://player.adobescreens.com) dans la barre d’adresses.
1. Le navigateur vérifie si le lecteur cloud peut être installé, puis affiche une icône d’installation dans la barre d’adresse.

   ![image](/help/user-guide/assets/cloud-player-install.png)

1. Sélectionnez l’icône d’installation et le bouton d’installation dans la boîte de dialogue de confirmation. Cloud Player est installé en tant qu’application autonome sur votre appareil et peut être lancé à l’aide d’une icône.

>[!NOTE]
>
>### Option d’installation de Cloud Player {#cloud-player-install-option}
>
1. L’option d’installation d’un PWA est également connue sous le nom de fonctionnalité &quot;Ajouter à l’écran d’accueil&quot; ou A2HS. La prise en charge de l’installation de PWA à partir du web varie en fonction du navigateur et de la plateforme.
1. Chaque navigateur comporte des critères différents pour vérifier si l’application PWA peut être ou non installée. En règle générale, le navigateur vérifie ces éléments (plus de détails ici) :
>
* Si l’application dispose d’un fichier json manifeste avec un minimum de clés requises pour installer l’application sur la plateforme, c’est-à-dire son nom, ses icônes, son nom, son adresse start_url, affichez
* Si l’application comporte un fichier de service worker avec un écouteur d’événement de récupération
* L’application doit être diffusée via https
>
1. L’option d’installation peut être visible à différents emplacements dans différents navigateurs et types d’appareils. Certains navigateurs peuvent masquer l’icône d’installation dans la barre de menus des options.

## Approvisionnement en bloc de Cloud Player {#bulk-provisioning}

Pour effectuer l’approvisionnement en bloc de Cloud Player sur plusieurs appareils :

1. Choisissez une solution MDM qui prend en charge l’exécution d’un navigateur avec une URL en mode kiosque.
1. Vous pouvez appliquer les mêmes configurations à tous les appareils en procédant comme suit :

   1. Hébergez config.json sur un serveur de sorte qu’il soit accessible, par exemple : `https://<config_server_host>/config.json`
   1. Pour installer le lecteur cloud et appliquer les configurations hébergées, utilisez l’URL du lecteur cloud telle que : `https://player.adobescreens.com?playerConfigAddress=https://<config_server_host>`
   1. L’application Cloud Player recherche config.json à la racine de &lt;config_server_host>, analyse le fichier config.json pour obtenir les configurations personnalisées et appliquer ces configurations.
   1. Ces configurations sont appliquées à chaque rechargement du lecteur.

## Approvisionnement en bloc sur le système d’exploitation Chrome {#bulk-provisioning-chrome}

Pour en savoir plus sur la mise en service en bloc sur Chrome OS, voir [Installation de Cloud Player sur Chrome OS](https://main--screens-franklin-documentation--hlxscreens.hlx.page/updates/cloud-player/guides/chromeos-install-cloud-player).

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
Google a activement abandonné les applications Chrome au profit des applications PWA, avec une migration prévue jusqu’en janvier 2025. Par conséquent, l’application du lecteur AEM Screens sous Chrome OS ne fonctionne plus en fonction de la chronologie partagée. Adobe invite les utilisateurs qui utilisent actuellement le lecteur Chrome en production à planifier leur transition vers le lecteur cloud Screens.
>
1. Lecteur d’extension Chrome sous Mac, Windows et Linux® :
>
En raison du processus d’obsolescence de Google, à partir de Google Chrome version 114, le lecteur d’extension Chrome Screens n’est plus pris en charge. Adobe vous conseille d’effectuer la transition vers son lecteur cloud Screens pour répondre à toutes vos exigences en matière de développement et de test.

## Prise en charge hors ligne de la récupération de contenu externe {#offline-support}

Dans divers scénarios d’utilisation, les canaux peuvent nécessiter la récupération de contenu à partir d’une source externe (par exemple, des widgets météorologiques ou des applications d’une seule page intégrées à Commerce) qui ne peuvent pas, par nature, fournir une prise en charge hors ligne. Pour activer la fonctionnalité hors ligne pour ces cas d’utilisation spécifiques, le lecteur cloud prend en charge l’en-tête personnalisé.

Le lecteur cloud utilise une stratégie de mise en cache favorisant le réseau (Network First), ce qui signifie qu’il tente de récupérer du contenu du réseau (puis de mettre à jour le cache avec la dernière version), avant de revenir au contenu mis en cache s’il est disponible. Pour mettre en œuvre la prise en charge hors ligne de cette récupération de contenu, l’en-tête personnalisé doit être inclus dans la requête. Ensuite, la requête avec l’en-tête personnalisé est mise en cache sur le lecteur, ce qui facilite l’accès hors ligne au contenu tout en conservant la stratégie de mise en cache Réseau d’abord .

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

Adobe valorise vos commentaires. Partagez vos réflexions avec nous à travers ceci [formulaire](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4TFE0b_GjstOj6I1uGs9vLpURVdWWklQQTZZRTFVNEhRVlBWWldMWlJXOC4u).
