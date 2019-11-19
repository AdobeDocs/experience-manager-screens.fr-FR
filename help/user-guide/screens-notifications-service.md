---
title: Service de notifications AEM Screens
seo-title: Service de notifications AEM Screens
description: Suivez cette page pour en savoir plus sur la manière de surveiller l’activité des périphériques.
seo-description: Suivez cette page pour en savoir plus sur la manière de surveiller l’activité des périphériques.
uuid: 9843219d-ed39-4e4f-bef4-e500528ff9f1
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
discoiquuid: 8879e510-4f0e-46da-87d2-77c5aaacb26e
translation-type: tm+mt
source-git-commit: ad7f18b99b45ed51f0393a0f608a75e5a5dfca30

---


# Service de notifications AEM Screens{#aem-screens-notifications-service}

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

***Le service*** de notifications d’AEM Screens décrit la fonctionnalité permettant de surveiller l’activité des périphériques.

Cette section traite des sujets suivants :

* **Présentation**
* **Configuration des paramètres de courrier électronique**
* **Email Notification**
* **Exemple de cas d'utilisation**

>[!CAUTION]
>
>Cette fonctionnalité d’AEM Screens est disponible uniquement si vous avez installé AEM 6.3.2 Feature Pack 3 ou AEM 6.4.1 Screens Feature Pack 1.
>
>Pour accéder à ce Feature Pack, vous devez contacter l’assistance d’Adobe et demander à y accéder. Une fois que vous disposez des autorisations, vous pouvez le télécharger à partir de Package Share.

## Présentation {#overview}

***Le service*** de notifications d’AEM Screens permet aux administrateurs de recevoir un courrier électronique si le lecteur d’écrans AEM ne effectue pas de test ping pendant une période configurable.

Ce service peut être configuré dans la console Web OSGi.

## Configuring Email Settings {#configuring-email-settings}

Pour configurer les paramètres de notification par courrier électronique, procédez comme suit :

1. Open **Adobe Experience Manager Web Console Configuration**.
1. Ouvrez **Screens Device Email Monitoring Service**.

   ![screen_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. Définissez les champs suivants pour configurer les paramètres du courrier électronique :

   **Chemin** d'accès aux périphériques Entrez le chemin d'accès aux projets d'écrans que vous souhaitez surveiller. Le chemin est habituellement `/home/users/screens/<Name of your project>`.

   Par exemple, si votre projet est **We.Retail**, vous utiliserez le chemin du projet comme ***/home/users/screens/we-détaillant***.

   >[!NOTE]
   >
   >Spécifiez le chemin du projet, où se trouvent les utilisateurs du périphérique.

   **Fréquence** de planification Indiquez une heure (p. ex., 17 h ou 17 h) ou une fréquence en heures (p. ex., 1) à laquelle ce moniteur doit envoyer des courriels.

   **Délai d'expiration** du ping Indique l'intervalle en minutes après lequel un périphérique doit être considéré comme inaccessible.

   **Serveur** SMTP Spécifie le serveur SMTP utilisé pour envoyer des courriers électroniques.

   **Port** SMTP : entrez le port SMTP.

   **L'utilisation de TLS** Transport Layer Security (TLS) vous permet d'utiliser une communication sécurisée avec le serveur SMTP.

   Il est recommandé d’utiliser TLS pour établir une connexion sécurisée aux serveurs de messagerie d’entreprise. Vérifiez auprès de votre administrateur de messagerie les valeurs appropriées.

   **nom d’utilisateur** Indiquez le nom d’utilisateur pour l’envoi de courriers électroniques.

   **mot de passe** Indiquez le mot de passe d’envoi des courriers électroniques.

   **Destinataire** Indiquez l’adresse électronique du destinataire.

   >[!NOTE]
   >
   >Vous ne pouvez saisir qu’une seule adresse électronique. Pour envoyer un courrier électronique en masse, créez une liste de groupe ou de distribution avec les utilisateurs concernés.

1. Cliquez sur **Enregistrer** pour configurer l’activité du moniteur par courrier électronique pour votre périphérique AEM Screens.

## Email Notification {#email-notification}

Une fois la configuration définie pour vos notifications par courrier électronique, vous recevrez une notification par courrier électronique qui contiendra le lien vers le périphérique réel signalé comme inactif.

L'accès à ce lien vous mènera directement au tableau de bord du périphérique.

Les courriers électroniques ne sont envoyés que s’il existe au moins un périphérique qui n’a pas fait de sonnerie pendant le délai d’expiration du ping donné et qui ne fait toujours pas de sonnerie au moment de la génération du courrier électronique.

### Exemples de cas d’utilisation {#example-use-cases}

L'exemple suivant décrit quelques scénarios à titre de référence pour configurer les propriétés à partir du service de surveillance des courriers électroniques des écrans.

**Scénario 1**:

Si vous définissez la fréquence de planification sur 1:00 et le délai d’expiration du ping sur 60, si votre périphérique Screens ne effectue pas de test ping entre 12:00 et 13:00, vous recevrez une notification par courrier électronique confirmant l’inactivité du périphérique.

**Scénario 2**:

Si vous définissez la fréquence de planification sur 1 et le délai d’expiration du ping sur 60, si votre périphérique d’écran ne effectue pas de ping entre une fois à un moment donné de la journée, vous recevrez une notification par courrier électronique confirmant l’inactivité du périphérique.
