---
title: Configurations du Dispatcher pour AEM Screens
seo-title: Configurations du Dispatcher pour AEM Screens
description: Cette page décrit les instructions de configuration du Dispatcher pour un projet AEM Screens.
seo-description: Cette page décrit les instructions de configuration du Dispatcher pour un projet AEM Screens.
feature: Administering Screens
role: Developer, Business Practitioner
level: Intermediate
translation-type: ht
source-git-commit: 89c70e64ce1409888800af7c7edfbf92ab4b2c68
workflow-type: ht
source-wordcount: '397'
ht-degree: 100%

---


# Configurations du Dispatcher pour AEM Screens {#dispatcher-configurations-for-aem-screens}

Dispatcher est l’outil de mise en cache et/ou d’équilibrage de charge d’Adobe Experience Manager.

La page suivante décrit les instructions de configuration du Dispatcher pour un projet AEM Screens.

>[!NOTE]
>
>Si un Dispatcher est disponible, il est possible d’empêcher les connexions à la servlet d’enregistrement en filtrant les règles du Dispatcher.
>
>En l’absence de Dispatcher, désactivez la servlet d’enregistrement dans la liste des composants OSGi.

## Conditions préalables {#pre-requisites}

Avant de configurer le Dispatcher pour un projet AEM Screens, vous devez connaître le Dispatcher au préalable.

Pour en savoir plus, consultez [Configuration du Dispatcher](https://docs.adobe.com/content/help/fr-FR/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html).

## Configuration du Dispatcher {#configuring-dispatcher}

Les lecteurs/périphériques AEM Screens utilisent une session authentifiée pour accéder aux ressources dans les instances de publication. Ainsi, lorsque vous disposez de plusieurs instances de publication, les requêtes doivent toujours être envoyées à la même instance afin que la session authentifiée soit valide pour toutes les requêtes provenant des lecteurs/périphériques AEM Screens.

Suivez les étapes ci-dessous pour configurer le Dispatcher pour un projet AEM Screens.

### Activation des sessions persistantes {#enable-sticky-session}

Si vous souhaitez utiliser plusieurs instances de publication sous l’égide d’un Dispatcher unique, vous devez mettre à jour le fichier `dispatcher.any` pour permettre la persistance.

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

Si une instance de publication est placée sous l’égide d’un Dispatcher, l’activation de la persistance dans le Dispatcher n’est pas efficace car il est possible que l’équilibreur de charge envoie chaque requête au Dispatcher. Dans ce cas, cliquez sur **Activer** dans le champ **Persistance** pour l’activer au niveau de l’équilibreur de charge, comme indiqué dans la figure ci-dessous :

![image](/help/user-guide/assets/dispatcher/dispatcher-enable.png)

Par exemple, si vous utilisez AWS ALB, référez-vous à la section [Populations cibles de vos équilibreurs de charge d’application](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html) pour activer la persistance au niveau de l’équilibreur ALB. Activez la persistance pour une journée.

### Étape 1 : configuration des en-têtes du client {#step-configuring-client-headers}

Ajoutez ce qui suit à la section `/clientheaders` :

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
