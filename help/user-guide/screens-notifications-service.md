---
title: Service de notifications AEM Screens
description: Découvrez comment surveiller l’activité des périphériques pour AEM Screens.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 205235d7-e621-4134-975c-257ae60939bc
source-git-commit: 6643f4162c8f0ee7bcdb0fd3305d3978234f5cfd
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 19%

---

# Service de notifications AEM Screens{#aem-screens-notifications-service}

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

***Service de notifications AEM Screens*** décrit l’activité du moniteur de périphérique.

Cette section couvre les sujets suivants :

* **Présentation**
* **Configuration des paramètres d’e-mail**
* **Notification par e-mail**
* **Exemple de cas d’utilisation**

<!-- OBSOLETE NOTE>
>[!CAUTION]
>
>This AEM Screens functionality is only available, if you have installed AEM 6.3.2 Feature Pack 3 or AEM 6.4.1 Screens Feature Pack 1.
>
>To get access to this Feature Pack, contact Adobe Support and request access. After you have permissions you can download it from Package Share. -->

## Vue d’ensemble {#overview}

***Service de notifications AEM Screens*** permet aux administrateurs de recevoir un e-mail si un lecteur AEM Screens ne effectue pas de test ping pendant une période configurable.

Ce service peut être configuré dans la console web OSGi.

## Configuration des paramètres d’e-mail {#configuring-email-settings}

Suivez les étapes ci-dessous pour configurer les paramètres de notification électronique :

1. Ouvrez le gestionnaire de **configuration de la console Web d’Adobe Experience Manager**.
1. Ouvrez le **Service de surveillance par e-mail des appareils Screens**.

   ![screen_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. Définissez les champs suivants afin de pouvoir configurer vos paramètres pour l&#39;email :

   **Chemin des périphériques** Saisissez le chemin d’accès aux projets Screens que vous souhaitez surveiller. Le chemin est habituellement `/home/users/screens/<Name of your project>`.

   Par exemple, si votre projet est **`We.Retail`**, utilisez le chemin du projet comme ***/home/users/screens/we-retail***.

   >[!NOTE]
   >
   >Spécifiez le chemin du projet, où se trouvent les utilisateurs de l’appareil.

   **Fréquence des planifications** - Spécifiez une heure (par exemple, 17 h 00 ou 17 h 00) ou une fréquence en heures (par exemple, 1) à laquelle ce moniteur doit envoyer des emails.

   **Délai d’expiration du ping** - Cela spécifie l’intervalle en minutes après lequel un appareil doit être considéré comme inaccessible.

   **Serveur SMTP** - Spécifie le serveur SMTP utilisé pour envoyer des emails.

   **Port SMTP** - Saisissez le port SMTP.

   **Utiliser TLS** - Transport Layer Security (TLS) vous permet d’utiliser une communication sécurisée avec le serveur SMTP.

   Adobe vous recommande d’utiliser TLS pour établir une connexion sécurisée aux serveurs de messagerie d’entreprise. Vérifiez auprès de votre administrateur de messagerie les valeurs appropriées.

   **username** - Indiquez le nom d’utilisateur pour l’envoi des emails.

   **password** - Indiquez le mot de passe d’envoi des emails.

   **Destinataire** - Indiquez l&#39;adresse email du destinataire.

   >[!NOTE]
   >
   >Vous ne pouvez saisir qu’une seule adresse e-mail. Pour envoyer un email en bloc, créez un groupe ou une liste de distribution avec les utilisateurs concernés.

1. Cliquez sur **Enregistrer** pour configurer l’activité du moniteur par e-mail pour votre appareil AEM Screens.

## Notification par e-mail {#email-notification}

Une fois la configuration définie pour vos notifications par e-mail, vous recevez une notification par e-mail contenant le lien vers le périphérique réel signalé comme inactif.

Ce lien vous permet d’accéder directement au tableau de bord du périphérique.

Les emails ne sont envoyés que si au moins un appareil n’a pas envoyé de ping pendant le délai d’expiration du ping donné et n’a toujours pas envoyé de ping au moment de la génération de l’email.

### Exemples de cas d’utilisation {#example-use-cases}

L’exemple suivant décrit quelques scénarios à titre de référence pour configurer les propriétés à partir du service de surveillance des emails des périphériques Screens.

**Scénario 1**

Définissez la fréquence de planification sur 1:00 et le délai d’expiration du ping sur 60. Ensuite, si votre appareil AEM Screens ne fait pas l’objet d’un ping entre 12h00 et 13h00, vous recevez une notification par e-mail qui confirme l’inactivité de l’appareil.

**Scénario 2**

Vous définissez la fréquence de planification sur 1 et le délai d’expiration du ping sur 60. Ensuite, si votre appareil AEM Screens ne fait pas l’objet d’un ping une fois à un moment donné de la journée, vous recevez une notification par e-mail qui confirme l’inactivité de l’appareil.
