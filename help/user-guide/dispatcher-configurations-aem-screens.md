---
title: Configurations du Dispatcher pour AEM Screens
description: Cette page met en évidence les instructions de configuration de Dispatcher pour un projet AEM Screens.
feature: Administering Screens
role: Developer, User
level: Intermediate
exl-id: 8b281488-f54d-4f8a-acef-ca60fa2315ed
source-git-commit: 67560ae17646424985032c81f33c937c6eeb5957
workflow-type: tm+mt
source-wordcount: '624'
ht-degree: 27%

---

# Configurations du Dispatcher pour AEM Screens {#dispatcher-configurations-for-aem-screens}

Dispatcher est un outil de mise en cache et/ou d’équilibrage de charge Adobe Experience Manager.

La page suivante fournit des instructions pour la configuration de Dispatcher pour un projet AEM Screens.

>[!NOTE]
>
>Si un Dispatcher est disponible, les connexions au servlet d’enregistrement peuvent être bloquées en filtrant les règles du Dispatcher.
>
>S’il n’existe pas de Dispatcher, désactivez le servlet d’enregistrement dans la liste des composants OSGi.

Avant de configurer Dispatcher pour un projet AEM Screens, vous devez connaître Dispatcher au préalable.
Voir [Configuration de Dispatcher](https://experienceleague.adobe.com/en/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration) pour plus d’informations.

## Configuration de Dispatcher pour Manifest version v2 {#configuring-dispatcher}

>[!IMPORTANT]
>Les configurations de Dispatcher suivantes s’appliquent uniquement à la version v2 de Manifest. Voir [Configurations de Dispatcher pour Manifest version v3](#configuring-dispatcherv3) pour manifest version v3.

Les lecteurs ou appareils AEM Screens utilisent une session authentifiée pour accéder aux ressources dans les instances de publication. Ainsi, lorsque vous disposez de plusieurs instances de publication, les requêtes doivent toujours aller vers la même instance de publication afin que la session authentifiée soit valide pour toutes les requêtes provenant des lecteurs/appareils AEM Screens.

Suivez les étapes ci-dessous pour configurer Dispatcher pour un projet AEM Screens.

### Activation des sessions persistantes {#enable-sticky-session}

Si vous souhaitez utiliser plusieurs instances de publication devant un seul Dispatcher, mettez à jour la variable `dispatcher.any` pour activer l’attractivité.

```xml
/stickyConnections {
  /paths
  {
    "/"
  }
 }
```

Si vous disposez d’une instance de publication devant un Dispatcher, l’activation de l’affinité au niveau de Dispatcher n’aide pas, car l’équilibreur de charge peut envoyer chaque requête à Dispatcher. Dans ce cas, sélectionnez **Activer** in **Attractivité** pour l’activer au niveau de l’équilibreur de charge, comme illustré dans la figure ci-dessous :

![image](/help/user-guide/assets/dispatcher/dispatcher-enable.png)

Par exemple, si vous utilisez AWS ALB, voir [Groupes cibles pour vos équilibreurs de charge d’application](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-target-groups.html) pour activer l’attractivité au niveau de l’ALB. Activez l’attractivité pour une journée.

### Étape 1 : configuration des en-têtes du client {#step-configuring-client-headers}

Ajoutez ce qui suit à la section `/clientheaders` :

**X-Requested-With**

**X-SET-HEARTBEAT**

**X-REQUEST-COMMAND**

### Étape 2 : configuration des filtres Screens {#step-configure-screens-filters}

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

Désactiver la mise en cache de Dispatcher pour ***Chemin /content/screens***.

Les lecteurs Screens utilisent des sessions authentifiées, de sorte que Dispatcher ne met en cache aucune des demandes de lecteurs Screens pour `channels/assets`.

Pour activer le cache des ressources afin qu’elles soient diffusées à partir du cache de Dispatcher, vous devez :

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

Veillez à autoriser ces filtres et règles de mise en cache dans les Dispatchers qui frontent les instances de publication pour le fonctionnement de Screens.

### Conditions préalables pour Manifest version v3 {#prerequisites3}

Suivez ces deux conditions préalables avant de configurer Dispatcher (manifest version v3) pour AEM Screens :

* Vérifiez que vous utilisez `v3 manifests`. Accédez à `https://<server:port>/system/console/configMgr/com.adobe.cq.screens.offlinecontent.impl.ContentSyncCacheFeatureFlag` et assurez-vous que `Enable ContentSync Cache` n’est pas coché.

* Assurez-vous que l’agent de vidage de Dispatcher est configuré à l’adresse `/etc/replication/agents.publish/dispatcher1useast1Agent` dans l’instance de publication.

  ![image](/help/user-guide/assets/dispatcher/dispatcher-1.png)

  ![image](/help/user-guide/assets/dispatcher/dispatcher-3.png)

### Filtres  {#filter-v3}

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

* Tous les lecteurs AEM Screens utilisent une session authentifiée pour se connecter à AEM (auteur/publication). Dispatcher prêt à l’emploi ne met pas en cache ces URL. Vous devez donc les activer.

* Ajouter `statfileslevel "10"` to `/cache` dans `publish_farm.any`
Cela prend en charge la mise en cache de jusqu’à dix niveaux à partir de la docroot de cache et invalidez en conséquence lorsque le contenu est publié plutôt que d’invalider tout. N’hésitez pas à modifier ce niveau en fonction de la profondeur de votre structure de contenu.

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

Si vous utilisez des campagnes ciblées avec AEM Screens, la variable `segments.js file` Les segments diffusés par Dispatcher doivent être invalidés, car vous ajoutez et publiez de nouveaux segments sur AEM. Sans cette règle d’invalidation, les nouvelles campagnes ciblées ne fonctionnent pas sur le lecteur AEM Screens (le contenu par défaut s’affiche à la place).

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
