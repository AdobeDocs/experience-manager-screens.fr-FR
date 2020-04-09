---
title: Liste de contrôle de sécurité pour les écrans AEM
seo-title: Liste de contrôle de sécurité pour les écrans AEM
description: La page décrit la liste de contrôle de sécurité pour les écrans AEM
seo-description: La page décrit la liste de contrôle de sécurité pour les écrans AEM
translation-type: tm+mt
source-git-commit: 72551a4b56d1db851cad71abd2ce8c0b02bbbc30

---


# Considérations relatives à la sécurité du système pour les écrans AEM {#security-checklist}

Cette page présente les points à prendre en compte pour la sécurité du système pour les écrans AEM.


## Livre blanc sur la sécurité des écrans AEM {#white-paper}

Cette section décrit le livre blanc. (Pièce jointe au Livre blanc en attente)


## FAQ sur la sécurité des écrans AEM {#faqs-screens}

Les FAQ suivantes supposent une architecture de lecteur enregistrée authentifiée utilisant HTTPS comme protocole de communication entre le lecteur et le serveur AEM.

### FAQ 1 {#faq1}

Le trafic du lecteur peut-il être redirigé vers un serveur malveillant et être chargé de télécharger et de lire du contenu multimédia malveillant ?

**Réponse**

Ce n&#39;est pas possible car la connexion HTTP identifie les deux extrémités de la connexion et la chiffre. Si vous essayez d&#39;être au milieu et de l&#39;intercepter, vous ne verrez que du contenu chiffré, et si vous essayez d&#39;usurper le serveur, le lecteur vous refusera parce que votre certificat est différent.


### FAQ 2 {#faq2}

Dois-je utiliser HTTP ou HTTP ?

**Réponse**

Utilisez HTTP. C&#39;est une obligation si vous êtes inquiet pour la sécurité. Avec les HTTP, la communication est chiffrée entre le lecteur et le serveur, et l&#39;interception ou la modification du contenu sera pratiquement impossible.


### FAQ 3 {#faq3}

Lors d’un téléchargement de contenu, existe-t-il une sorte de signature du contenu ou de hachage ?

**Réponse**

Chaque fichier est signé (SHA) par le serveur, puis validé par le lecteur pour le même hachage afin de garantir son intégrité.
Si le hachage ne correspond pas, nous essayons de revalider 3 fois. Après 3 tentatives, la commande de téléchargement est considérée comme non valide.


### FAQ 4 {#faq4}

Le serveur AEM est-il sécurisé ?

**Réponse**

Ans 4. En supposant que vous soyez sur AMS, nous nous occupons de toute la sécurité du serveur en utilisant les mêmes fonctionnalités que Sites ou Ressources.


### FAQ 5 {#faq5}

Le périphérique est-il sécurisé ?

**Réponse**

Un lecteur physiquement compromis peut théoriquement être manipulé pour lire n’importe quel contenu. Vous pouvez également brancher le lecteur et brancher une clé USB/HDMI.

Il est donc recommandé de mettre les périphériques hors de portée, de préférence dans un sécurisé, avec un câblage sécurisé également. Désactivez également les ports distants IR.

Si le système d&#39;exploitation du périphérique n&#39;est pas mis à jour régulièrement, il se peut que le système d&#39;exploitation soit exposé à des failles de sécurité et autorise des attaques à distance sur le réseau.
>[!NOTE]
>Il est recommandé d&#39;instrumenter les périphériques avec des capacités de mise à jour et de contrôle à distance correctes (bureau distant, solution MDM, etc.). Il est également recommandé d&#39;utiliser un réseau privé, non exposé au WIFI public par exemple.


### FAQ 6 {#faq6}

Comment un pirate essaierait-il de compromettre un joueur ?

**Réponse**

La seule façon de compromettre un lecteur est de :

1. compromettez le DNS afin d’incarner le serveur sur son nom d’hôte, et
1. compromis
   1. du certificat côté serveur pour incarner le serveur
   1. périphérique et personnalisation du certificat côté client

>[!IMPORTANT]
>Même si un périphérique est compromis, vous pouvez toujours facilement révoquer ses informations d’identification afin qu’il ne puisse plus se connecter à AEM.





