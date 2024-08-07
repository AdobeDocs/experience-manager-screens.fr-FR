---
title: Configurations de Dispatcher pour AEM Screens
description: Cette page décrit les instructions de configuration de Dispatcher pour un projet AEM Screens.
feature: Administering Screens
role: Developer, User
level: Intermediate
exl-id: 8b281488-f54d-4f8a-acef-ca60fa2315ed
source-git-commit: df41a8794683e241b6f12b58d39c01e069187435
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 100%

---

# Configurations de Dispatcher pour AEM Screens{#dispatcher-configurations-for-aem-screens}

Dispatcher est l’outil de mise en cache d’Adobe Experience Manager ou de répartition de charge, ou les deux.

La page suivante décrit les instructions de configuration de Dispatcher pour un projet AEM Screens.

>[!NOTE]
>
>Si un Dispatcher est disponible, il est possible d’empêcher les connexions à la servlet d’enregistrement en filtrant les règles du Dispatcher.
>
>En l’absence de Dispatcher, désactivez la servlet d’enregistrement dans la liste des composants OSGi.

Avant de configurer Dispatcher pour un projet AEM Screens, vous devez le connaître au préalable.
Pour en savoir plus, voir [Configuration de Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration?lang=fr).

## Configuration de Dispatcher pour Manifest version v2 {#configuring-dispatcher}

>[!IMPORTANT]
>Les configurations de Dispatcher suivantes s’appliquent uniquement à la version v2 de Manifest. Voir [Configurations de Dispatcher pour la version v3 de Manifest](#configuring-dispatcherv3) pour la version v3 de Manifest.

Les lecteurs ou appareils AEM Screens utilisent une session authentifiée pour accéder aux ressources dans les instances de publication. Ainsi, lorsque vous disposez de plusieurs instances de publication, les requêtes doivent toujours être envoyées à la même instance de publication afin que la session authentifiée soit valide pour toutes les requêtes provenant des lecteurs et appareils AEM Screens.

Pour configurer Dispatcher pour un projet AEM Screens, suivez les étapes ci-dessous.

### Activation des sessions persistantes {#enable-sticky-session}

Si vous souhaitez utiliser plusieurs instances de publication sous l’égide d’un Dispatcher unique, mettez à jour le fichier `dispatcher.any` pour permettre la persistance.

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

Si une instance de publication est placée sous l’égide d’un Dispatcher, l’activation de la persistance dans le Dispatcher n’est pas efficace car il est possible que l’équilibreur de charge envoie chaque requête au Dispatcher. Dans ce cas, cliquez sur **Activer** dans le champ **Persistance** pour l’activer au niveau de la répartition de charge, comme indiqué dans la figure ci-dessous :

![image](/help/user-guide/assets/dispatcher/dispatcher-enable.png)

Par exemple, si vous utilisez AWS ALB, voir [Populations cibles de vos équilibreurs de charge d’application](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html) pour activer la persistance au niveau de l’équilibreur ALB. Activez la persistance pour une journée.

### Étape 1 : configuration des en-têtes du client {#step-configuring-client-headers}

Ajoutez ce qui suit à la section `/clientheaders` :

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### Étape 2 : configuration des filtres Screens {#step-configure-screens-filters}

Pour configurer les filtres Screens, ajoutez les éléments suivants à ***`/filter`***.

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

Désactivez la mise en cache de Dispatcher pour le chemin ***/content/screens path***.

Les lecteurs Screens utilisent une session authentifiée, de sorte que Dispatcher ne met en cache aucune de leurs demandes pour `channels/assets`.

Pour activer le cache des ressources afin qu’elles soient diffusées à partir du cache de Dispatcher, vous devez procéder comme suit :

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

## Configuration de Dispatcher pour Manifest version v3 {#configuring-dispatcherv3}

Veillez à autoriser ces filtres et règles de mise en cache dans les Dispatchers placés devant les instances de publication pour le fonctionnement de Screens.

### Conditions préalables pour Manifest version v3{#prerequisites3}

Respectez ces deux conditions préalables avant de configurer Dispatcher (Manifest version v3) pour AEM Screens :

* Vérifiez que vous utilisez `v3 manifests`. Accédez à `https://<server:port>/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag` et assurez-vous que `Enable ContentSync Cache` n’est pas coché.

* Assurez-vous que l’agent de vidage de Dispatcher est configuré dans le chemin `/etc/replication/agents.publish/dispatcher1useast1Agent` de l’instance de publication.

  ![image](/help/user-guide/assets/dispatcher/dispatcher-1.png)

  ![image](/help/user-guide/assets/dispatcher/dispatcher-3.png)

### Filtres {#filter-v3}

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
#/0221 { /type "allow" /method '(GET|HEAD)' /url "/content/experience-fragments/*" } ## uncomment this, if you're using experience-fragments
/0222 { /type "allow" /extension '(css|eot|gif|ico|jpeg|jpg|js|gif|pdf|png|svg|swf|ttf|woff|woff2|html|mp4|mov|m4v)' /path "/content/dam/*" } ## add any other formats required for your project here
 
## # Enable clientlibs proxy servlet
/0230 { /type "allow" /method "GET" /url "/etc.clientlibs/*" }
```

### Règles de cache {#cache-rules-v3}

* Ajoutez `/allowAuthorized "1"` à la section `/cache` dans `publish_farm.any`.

* Tous les lecteurs AEM Screens utilisent une session authentifiée pour se connecter à AEM (création/publication). Par défaut, Dispatcher ne met pas en cache ces URL. Vous devez donc les activer.

* Ajoutez `statfileslevel "10"` à la section `/cache` dans `publish_farm.any`.
Cela prend en charge la mise en cache de dix niveaux maximum à partir de la racine docroot du cache et invalide en conséquence lorsque le contenu est publié plutôt que de tout invalider. N’hésitez pas à modifier ce niveau en fonction de la profondeur de votre structure de contenu.

* Ajoutez le code suivant à `/invalidate section in publish_farm.any`

  ```
  /0003 {
      /glob "*.json"
      /type "allow"
  }
  ```

* Ajoutez les règles suivantes à la section `/rules` dans `/cache` dans `publish_farm.any` ou dans un fichier inclus à partir de `publish_farm.any` :

  ```
  ## Don't cache CSRF login tokens
  /0001
      {
      /glob "/libs/granite/csrf/token.json"
      /type "deny"
      }
  ## Allow Dispatcher Cache for Screens channels
  /0002
      {
          /glob "/content/screens/*.html"
          /type "allow"
      }
  ## Allow Dispatcher Cache for Screens offline manifests
  /0003
      {
      /glob "/content/screens/*.manifest.json"
      /type "allow"
      }
  ## Allow Dispatcher Cache for Assets
  /0004
      {
  
      /glob "/content/dam/*"
      /type "allow"
      }
  ## Disable Dispatcher Cache for Screens devices json
  /0005
      {
      /glob "/home/users/screens/*.json"
      /type "deny"
      }
  ## Disable Dispatcher Cache for Screens svc json
  /0006
      {
      /glob "/content/screens/svc.json"
      /type "deny"
      }
  ```

### Ajouter une règle d’invalidation pour segment.js {#invalidsegmentjs}

Si vous utilisez des campagnes ciblées avec AEM Screens, le `segments.js file` diffusé par Dispatcher doit être invalidé lorsque vous ajoutez et publiez de nouveaux segments sur AEM. Sans cette règle d’invalidation, les nouvelles campagnes ciblées ne fonctionnent pas sur le lecteur AEM Screens (le contenu par défaut s’affiche à la place).

* Ajoutez une règle d’invalidation à `/etc/httpd/conf.dispatcher.d/available_farms/999_ams_publish_farm.any`. Voici la règle à ajouter :

```
    /invalidate {
                        .
                        .
                        /0004 {
                               /glob "conf/<project-name>/settings/wcm/.js"
                               /type "allow"
                        }
                }
```

* Cette règle garantit que le fichier `segments.js` est invalidé et que la dernière version est récupérée en cas de modification.
