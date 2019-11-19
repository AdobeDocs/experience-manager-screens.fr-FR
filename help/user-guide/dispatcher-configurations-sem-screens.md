---
title: Configurations du répartiteur pour les écrans AEM
seo-title: Configurations du répartiteur pour les écrans AEM
description: 'null'
seo-description: 'null'
page-status-flag: never-activated
uuid: ea68ca72-bbe7-42d5-9043-97aea7edcd6e
contentOwner: jsyal
discoiquuid: 046ec5ae-600d-422f-aa59-c39f16cf71de
docset: aem65
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Configurations du répartiteur pour les écrans AEM{#dispatcher-configurations-for-aem-screens}

Dispatcher est l’outil de mise en cache et/ou d’équilibrage de charge d’Adobe Experience Manager.

La page suivante décrit les instructions de configuration du répartiteur pour un projet AEM Screens.

## Conditions préalables {#pre-requisites}

Avant de configurer le répartiteur pour un projet AEM Screens, vous devez connaître le répartiteur au préalable.

Refer to **[Configuring Dispatcher](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html)** for more details.

## Configuration de Dispatcher {#configuring-dispatcher}

Suivez les étapes ci-dessous pour configurer le répartiteur pour un projet AEM Screens.

### Étape 1 : Configuration des en-têtes du client {#step-configuring-client-headers}

Ajouter ce qui suit à la `/clientheaders` section

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### Étape 2 : Configuration des filtres d’écran {#step-configuring-screens-filters}

Pour configurer les filtres Ecrans, ajoutez les éléments suivants à ***/filtrer***.

```
## AEM Screens Filters
## # Login, Ping and Device Configurations
/0200 { /type "allow" /method "POST" /url "/libs/granite/core/content/login.validate/j_security_check" }
/0201 { /type "allow" /method "GET" /url "/content/screens/svc.json" }
/0202 { /type "allow" /method "GET" /url "/content/screens/svc.ping.json" }
/0203 { /type "allow" /method "GET" /url "/content/screens/svc.config.json" }
## # Device Dashboard Configurations
/0204 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.preferences.json" }
/0205 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.logs.json" }
/0206 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.statusinfo.json" }
/0207 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.screenshot.json" }
## # Content Configurations
/0208 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*" }
/0209 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*/jcr:content/*/offline-config_*.zip" }
/0210 { /type "allow" /method '(GET|HEAD)' /url '/var/contentsync/content/screens/.+/jcr:content/.+/offline-config_.*\.[0-9]+\.zip' }
```

### Étape 3 : Désactivation du cache du répartiteur {#step-disabling-dispatcher-cache}

Désactivez la mise en cache du répartiteur pour le chemin ******/contenu/écrans.
