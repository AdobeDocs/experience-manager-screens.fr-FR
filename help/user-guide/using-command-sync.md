---
title: Utilisation de la synchronisation des commandes
seo-title: Utilisation de la synchronisation des commandes
description: Suivez cette page pour en savoir plus sur l’utilisation de la synchronisation des commandes.
seo-description: Suivez cette page pour en savoir plus sur l’utilisation de la synchronisation des commandes.
translation-type: tm+mt
source-git-commit: 8f9ede8681c8c23cefa66c1177e2761ed8aae2fd

---


# Utilisation de la synchronisation des commandes {#using-command-sync}

La page suivante décrit l’utilisation de la synchronisation des commandes. La synchronisation des commandes permet une lecture synchronisée sur différents lecteurs. Les lecteurs peuvent lire un contenu différent, mais chaque fichier doit avoir la même durée.

## Présentation {#overview}

Les solutions de signalisation numérique doivent prendre en charge les murs vidéo et la lecture synchronisée pour prendre en charge des scénarios tels que les comptes à rebours du Nouvel An ou les vidéos volumineuses découpées pour être lues sur plusieurs écrans. C’est là que la synchronisation de contenu entre en jeu.

Pour utiliser Content Sync, un lecteur agit comme *maître* et envoie une commande et tous les autres lecteurs agissent comme *clients* et jouent quand ils reçoivent la commande. Le *maître* envoie une commande à tous les clients enregistrés lorsqu’il est sur le point de démarrer la lecture d’un élément. La charge utile peut être l’index de l’élément à lire et/ou le code html externe de l’élément à lire.



