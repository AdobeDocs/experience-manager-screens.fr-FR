---
title: Configurations du dispatcher pour AEM Screens
seo-title: Configurations du dispatcher pour AEM Screens
description: 'null'
seo-description: 'null'
page-status-flag: never-activated
uuid: ea68ca72-bbe7-42d5-9043-97aea7edcd6e
contentOwner: jsyal
discoiquuid: 046ec5ae-600d-422f-aa59-c39f16cf71de
docset: aem65
translation-type: tm+mt
source-git-commit: dbc20693481e6f6f379eb93bbf40ed9961589d00

---


# Configurations du dispatcher pour AEM Screens{#dispatcher-configurations-for-aem-screens}

Dispatcher est l’outil de mise en cache et/ou d’équilibrage de charge d’Adobe Experience Manager.

La page suivante décrit les instructions de configuration du dispatcher pour un projet AEM Screens.

>[!NOTE]
>Si un répartiteur est disponible, il est possible d’empêcher les connexions à la servlet d’enregistrement en filtrant les règles du répartiteur.
>S’il n’existe aucun répartiteur, désactivez la servlet d’enregistrement dans la liste des composants OSGi.

## Conditions préalables {#pre-requisites}

Avant de configurer le dispatcher pour un projet AEM Screens, vous devez connaître le dispatcher au préalable.

Pour en savoir plus, consultez [Configuration du Dispatcher](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html).

## Configuration du Dispatcher {#configuring-dispatcher}

Suivez les étapes ci-dessous pour configurer le dispatcher pour un projet AEM Screens.

### Étape 1 : configuration des en-têtes du client {#step-configuring-client-headers}

Ajoutez ce qui suit à la section `/clientheaders`

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### Étape 2 : configuration des filtres Screens {#step-configuring-screens-filters}

Pour configurer les filtres Screens, ajoutez les éléments suivants à ***/filter ***.

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

### Étape 3 : désactivation du cache du dispatcher {#step-disabling-dispatcher-cache}

Désactivez la mise en cache du dispatcher pour le chemin ***/content/screens ***.
