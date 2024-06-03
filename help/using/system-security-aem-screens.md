---
title: Liste de contrôle de sécurité d’AEM Screens
description: En savoir plus sur la liste de contrôle de sécurité pour AEM Screens.
source-git-commit: 873e6ff8b506416bce8660f5eb2cbea75227a9c8
workflow-type: ht
source-wordcount: '460'
ht-degree: 100%

---


# Considérations relatives à la sécurité des systèmes pour AEM Screens {#security-checklist}

>[!IMPORTANT]
>Ressource Git interne.

Cette page contient des considérations relatives à la sécurité des systèmes pour AEM Screens.


## Article technique relatif à la sécurité d’AEM Screens {#white-paper}

Cette section décrit l’article technique. (en attente d’un article technique en pièce jointe)


## Questions fréquentes sur la sécurité d’AEM Screens {#faqs-screens}

Les questions fréquentes suivantes supposent que l’architecture du lecteur est authentifiée et enregistrée. Celle-ci utilise HTTPS comme protocole de communication entre le lecteur et le serveur AEM.

### Question fréquente 1 {#faq1}

Le trafic du lecteur peut-il être redirigé vers un serveur malveillant qui le contraint à télécharger et lire du contenu multimédia malveillant ?

**Réponse**

C’est impossible, car la connexion HTTPS identifie les deux extrémités de la connexion et la chiffre. Si vous essayez de vous mettre au milieu et de l’intercepter, vous ne voyez que du contenu chiffré. Si vous essayez d’emprunter l’identité du serveur, le lecteur vous refuse, car votre certificat est différent.


### Question fréquente 2 {#faq2}

Dois-je utiliser le protocole HTTP ou HTTPS ?

**Réponse**

Utilisez le protocole HTTPS. C’est un protocole essentiel si vous vous préoccupez de la sécurité. Avec le protocole HTTPS, la communication est chiffrée entre le lecteur et le serveur, et l’interception ou la modification du contenu est impossible.


### Question fréquente 3 {#faq3}

Lors d’un téléchargement de contenu, existe-t-il une sorte de signature du contenu ou de hachage ?

**Réponse**

Chaque ressource est signée (SHA) par le serveur. Le lecteur la valide ensuite avec le même hachage afin de garantir son intégrité.
Si le hachage ne correspond pas, le logiciel effectue trois tentatives de validation. Après trois tentatives, la commande de téléchargement est considérée comme non valide.


### Question fréquente 4 {#faq4}

Le serveur AEM est-il sécurisé ?

**Réponse**

En supposant que vous soyez sur AMS, nous nous occupons de l’ensemble de la sécurité du serveur avec les mêmes fonctionnalités que Sites ou Assets.


### Question fréquente 5 {#faq5}

L’appareil est-il sécurisé ?

**Réponse**

Un lecteur compromis physiquement peut théoriquement être manipulé pour lire n’importe quel contenu. Vous pouvez également débrancher le lecteur et brancher une clé USB/HDMI.

Mettez les appareils hors de portée, de préférence dans un boîtier sécurisé, doté d’un câblage également sécurisé. Désactivez aussi les ports de télécommande infrarouge.

Si le système d’exploitation de l’appareil n’est pas mis à jour régulièrement, il peut être exposé à des failles de sécurité et ainsi permettre des attaques à distance via le réseau.

>[!NOTE]
>
>Il est recommandé de doter les appareils de fonctionnalités suffisantes de mise à jour et de commande à distance (bureau distant, solution MDM, etc.). Nous vous recommandons également d’utiliser un réseau privé, par exemple non exposé au Wi-Fi public.


### Question fréquente 6 {#faq6}

Comment un pirate informatique peut-il tenter de compromettre un lecteur ?

**Réponse**

La seule façon de compromettre un appareil de lecture est la suivante :

1. Compromettre le DNS pour emprunter l’identité du nom d’hôte du serveur, et
1. compromettre
   1. le certificat côté serveur pour emprunter l’identité de l’appareil du serveur
   1. et emprunter l’identité du certificat côté client

>[!IMPORTANT]
>Même si un appareil est compromis, vous pouvez toujours facilement révoquer ses informations d’identification afin qu’il ne puisse plus se connecter à AEM.





