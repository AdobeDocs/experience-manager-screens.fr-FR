---
title: API REST
seo-title: API REST
description: AEM Screens fournit une API RESTful simple conforme à la spécification Siren. Consultez cette page pour savoir comment parcourir la structure de contenu et envoyer des commandes aux périphériques au sein de l’environnement.
seo-description: AEM Screens fournit une API RESTful simple conforme à la spécification Siren. Consultez cette page pour savoir comment parcourir la structure de contenu et envoyer des commandes aux périphériques au sein de l’environnement.
uuid: 5988fdcb-cda5-4d3e-a2ab-f9ee4179e568
contentOwner: Jyotika Syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: developing
discoiquuid: c07b6e4f-c0a4-4151-a543-76dabd6d5146
feature: Développement dans Screens
role: Développeur
level: Intermédiaire
translation-type: ht
source-git-commit: 9d36c0ebc985b815ab41d3f3ef44baefa22db915
workflow-type: ht
source-wordcount: '243'
ht-degree: 100%

---


# API REST {#rest-apis}

AEM Screens fournit une API RESTful simple conforme à la spécification [Siren](https://github.com/kevinswiber/siren). Elle vous permet de parcourir la structure de contenu et d’envoyer des commandes aux périphériques au sein de l’environnement.

L’API est accessible à l’adresse suivante : [*http://localhost:4502/api/screens.json*](http://localhost:4502/api/screens.json).

## Exploration de la structure de contenu {#navigating-content-structure}

Le code JSON renvoyé par les appels d’API répertorie les entités associées à la ressource en cours. En suivant le lien vers lui-même (self-link) répertorié, chacune de ces entités est de nouveau accessible sous la forme d’une ressource REST.

Par exemple, pour accéder aux écrans de notre emplacement de démonstration, vous pouvez appeler :

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship.json HTTP/1.1
Host: http://localhost:4502
```

Ou à l’aide de curl :

```xml
curl -u admin:admin http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship.json
```

Le résultat ressemble à ceci :

```xml
{
  "class": [
    "aem-io/screens/location"
  ],
  "links": [
    {
      "rel": [
        "self"
      ],
      "href": "http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship.json"
    },
    {
      "rel": [
        "parent"
      ],
      "href": "http://localhost:4502/api/screens/content/screens/we-retail/locations/demo.json"
    }
  ],
  "properties": {…},
  "entities": [
    {
      "class": [
        "aem-io/screens/display"
      ],
      "links": [
        {
          "rel": [
            "self"
          ],
          "href": "http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json"
        }
      ],
      "rel": [
        "child"
      ],
      "properties": {
        "title": "Single Screen Display",
        "height": 1440,
        "description": "Demo location of a single screen display.",
        "name": "single",
        "width": 2560,
        "idletimeout": 300,
        "layoutrows": 1,
        "layoutcols": 1
      }
    },
    …
  ]
}
```

Et ensuite, pour accéder à l’affichage sur un seul écran, vous pouvez appeler :

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502
```

## Exécution d’actions sur la ressource {#executing-actions-on-the-resource}

Le code JSON renvoyé par les appels d’API peut contenir la liste des actions disponibles sur la ressource.

L’affichage, par exemple, répertorie une action *broadcast-command* qui permet d’envoyer une commande à tous les périphériques qui lui sont affectés.

```xml
GET /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502
```

Ou à l’aide de curl :

```xml
curl -u admin:admin http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json
```

***Résultat :***

```xml
{
  "class": [
    "aem-io/screens/display"
  ],
  "links": […],
  "properties": {…},
  "entities": […],
  "actions": [
    {
      "title": "",
      "name": "broadcast-command",
      "method": "POST",
      "href": "/api/screens/content/screens/we-retail/locations/demo/flagship/single",
      "fields": [
        {
          "name": ":operation",
          "value": "broadcast-command",
          "type": "hidden"
        },
        {
          "name": "msg",
          "type": "text"
        }
      ]
    }
  ]
}
```

Pour déclencher cette action, vous pouvez appeler :

```xml
POST /api/screens/content/screens/we-retail/locations/demo/flagship/single.json HTTP/1.1
Host: http://localhost:4502

:operation=broadcast-command&msg=reboot
```

Ou à l’aide de curl :

```xml
curl -u admin:admin -X POST -d ':operation=broadcast-command&msg=reboot' http://localhost:4502/api/screens/content/screens/we-retail/locations/demo/flagship/single.json
```

