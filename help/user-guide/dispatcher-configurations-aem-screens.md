---
title: Configurations du Dispatcher pour AEM Screens
seo-title: Configurations du Dispatcher pour AEM Screens
description: Cette page décrit les instructions de configuration du Dispatcher pour un projet AEM Screens.
seo-description: Cette page décrit les instructions de configuration du Dispatcher pour un projet AEM Screens.
translation-type: ht
source-git-commit: 4a1fb81fa343983093590c36ccb6a4fd110cdad2
workflow-type: ht
source-wordcount: '248'
ht-degree: 100%

---


# Configurations du Dispatcher pour AEM Screens{#dispatcher-configurations-for-aem-screens}

Dispatcher est l’outil de mise en cache et/ou d’équilibrage de charge d’Adobe Experience Manager.

La page suivante décrit les instructions de configuration du Dispatcher pour un projet AEM Screens.

>[!NOTE]
>
>Si un Dispatcher est disponible, il est possible d’empêcher les connexions à la servlet d’enregistrement en filtrant les règles du Dispatcher.
>
>En l’absence de Dispatcher, désactivez la servlet d’enregistrement dans la liste des composants OSGi.

## Conditions préalables {#pre-requisites}

Avant de configurer le Dispatcher pour un projet AEM Screens, vous devez connaître le Dispatcher au préalable.

Pour en savoir plus, consultez [Configuration du Dispatcher](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html).

## Configuration du Dispatcher {#configuring-dispatcher}

Suivez les étapes ci-dessous pour configurer le Dispatcher pour un projet AEM Screens.

### Activation des sessions persistantes{#enable-sticky-session}

Si vous souhaitez utiliser plusieurs instances de publication avec le Dispatcher, vous devez mettre à jour le fichier `dispatcher.any`.

```xml
/stickyConnections {
  /paths
  {
    "/content/screens"
    "/home/users/screens"
    "/libs/granite/csrf/token.json"
  }
}
```

### Étape 1 : configuration des en-têtes du client {#step-configuring-client-headers}

Ajoutez ce qui suit à la section`/clientheaders` :

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### Étape 2 : configuration des filtres Screens {#step-configuring-screens-filters}

Pour configurer les filtres Screens, ajoutez les éléments suivants à ***/filter***.

```
## AEM Screens Filters
## # Login, Ping and Device Configurations
/0200 { /type "allow" /method "POST" /url "/libs/granite/core/content/login.validate/j_security_check" }
/0201 { /type "allow" /method "GET" /url "/libs/granite/csrf/token.json" }
/0202 { /type "allow" /method "GET" /url "/content/screens/svc.json" }
/0203 { /type "allow" /method "GET" /url "/content/screens/svc.ping.json" }
/0204 { /type "allow" /method "GET" /url "/content/screens/svc.config.json" }
## # Device Dashboard Configurations
/0210 { /type "allow" /method '(GET|POST)' /url "/home/users/screens/*/devices/*/profile_screens.preferences.json" }
/0211 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.logs.json" }
/0212 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.statusinfo.json" }
/0213 { /type "allow" /method "POST" /url "/home/users/screens/*/devices/*/profile_screens.screenshot.json" }
## # Content Configurations
/0220 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*" }
/0221 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*/jcr:content/*/offline-config_*.zip" }
/0222 { /type "allow" /method '(GET|HEAD)' /url '/var/contentsync/content/screens/.+/jcr:content/.+/offline-config_.*\.[0-9]+\.zip' }
```

### Étape 3 : désactivation du cache du Dispatcher {#step-disabling-dispatcher-cache}

Désactivez la mise en cache du Dispatcher pour le chemin ***/content/screens***.

Les lecteurs Screens utilisent une session authentifiée, de sorte que le Dispatcher ne met en cache aucune de leurs demandes pour `channels/assets`.

Pour activer le cache des ressources afin qu’elles soient diffusées à partir du cache du Dispatcher, vous devez :

* ajouter `/allowAuthorization 1` dans la section `/cache` ;
* ajouter les règles ci-dessous à la section `/rules` de `/cache`.

```xml
/0000
    {
        /glob "*"
        /type "allow"
    }   

/0001
    {
        # Disable Dispatcher Cache for Screens channels
        /glob "/content/screens/*.html"
        /type "deny" 
    }

/0002
    {
    # Disable Dispatcher Cache for Screens offline manifests
    /glob "/content/screens/*.json"
    /type "deny"
    }

/0003
    { # Disable Dispatcher Cache for Screens devices json 
    /glob "/home/users/screens/*.json"
    /type "deny"
    }
```
