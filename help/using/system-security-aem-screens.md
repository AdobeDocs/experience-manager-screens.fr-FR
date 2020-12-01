---
title: Liste de contrôle de sécurité d’AEM Screens
seo-title: Liste de contrôle de sécurité d’AEM Screens
description: Cette page décrit la liste de contrôle de sécurité d’AEM Screens
seo-description: Cette page décrit la liste de contrôle de sécurité d’AEM Screens
translation-type: tm+mt
source-git-commit: 54c5a2f2f3f755e4da4028d54042f4bd8f2df369
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 100%

---


# Considérations relatives à la sécurité des systèmes pour AEM Screens {#security-checklist}

>[!IMPORTANT]
>Il s’agit d’une ressource Git interne.

Cette page contient des considérations relatives à la sécurité des systèmes pour AEM Screens.


## Article technique relatif à la sécurité d’AEM Screens {#white-paper}

Cette section décrit l’article technique. (en attente d’un article technique en pièce jointe)


## Questions fréquentes sur la sécurité d’AEM Screens {#faqs-screens}

Les questions fréquentes suivantes supposent l’utilisation d’une architecture de lecteur enregistrée et authentifiée utilisant le protocole de communication HTTPS entre le lecteur et le serveur AEM.

### FAQ 1 {#faq1}

Le trafic du lecteur peut-il être redirigé vers un serveur malveillant qui le contraint à télécharger et lire du contenu multimédia malveillant ?

**Réponse**

C’est impossible, car la connexion HTTPS identifie les deux extrémités de la connexion et la chiffre. Si vous tentez d’intervenir entre les deux et d’intercepter le trafic, vous ne verrez que du contenu chiffré. De plus, si vous essayez d’usurper l’identité du serveur, le lecteur refusera, car votre certificat est différent.


### FAQ 2 {#faq2}

Dois-je utiliser le protocole HTTP ou HTTPS ?

**Réponse**

Utilisez le protocole HTTPS. C’est essentiel si vous vous préoccupez de sécurité. Avec le protocole HTTPS, la communication est chiffrée entre le lecteur et le serveur, et l’interception ou la modification du contenu est pratiquement impossible.


### FAQ 3 {#faq3}

Lors d’un téléchargement de contenu, existe-t-il une sorte de signature du contenu ou de hachage ?

**Réponse**

Chaque ressource est signée (SHA) par le serveur, puis validée par le lecteur en vérifiant que le hachage est le même, pour garantir son intégrité.
Si le hachage ne correspond pas, nous effectuons trois nouvelles tentatives de validation. Après trois tentatives, la commande de téléchargement est considérée comme non valide.


### FAQ 4 {#faq4}

Le serveur AEM est-il sécurisé ?

**Réponse**

Réponse 4. En supposant que vous soyez sur AMS, nous nous occupons de l’ensemble de la sécurité du serveur avec les mêmes fonctionnalités que Sites ou Assets.


### FAQ 5 {#faq5}

L’appareil est-il sécurisé ?

**Réponse**

Un lecteur compromis physiquement peut théoriquement être manipulé pour lire n’importe quel contenu. Vous pouvez également débrancher le lecteur et brancher une clé USB/HDMI.

Il est donc recommandé de mettre les appareils hors de portée, de préférence dans un boîtier sécurisé, doté d’un câblage également sécurisé. Désactivez aussi les ports de télécommande infrarouge.

Si le système d’exploitation n’est pas mis à jour régulièrement, il peut être exposé à des failles de sécurité et permettre des attaques à distance via le réseau.

>[!NOTE]
>
>Il est recommandé de doter les appareils de fonctionnalités suffisantes de mise à jour et de commande à distance (bureau distant, solution MDM, etc.). Nous vous recommandons également d’utiliser un réseau privé, par exemple non exposé au Wi-Fi public.


### FAQ 6 {#faq6}

Comment un pirate informatique peut-il tenter de compromettre un lecteur ?

**Réponse**

La seule façon de compromettre un appareil de lecture est la suivante :

1. compromettre le DNS pour emprunter l’identité du nom d’hôte du serveur, et
1. compromettre
   1. le certificat côté serveur pour emprunter l’identité de l’appareil du serveur
   1. et emprunter l’identité du certificat côté client

>[!IMPORTANT]
>Même si un appareil est compromis, vous pouvez toujours facilement révoquer ses informations d’identification afin qu’il ne puisse plus se connecter à AEM.





