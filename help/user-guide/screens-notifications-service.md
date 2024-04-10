---
title: Service de notifications AEM Screens
description: En savoir plus sur la manière de surveiller l’activité des appareils pour AEM Screens.
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/SCREENS
topic-tags: authoring
feature: Authoring Screens
role: Admin, Developer
level: Intermediate
exl-id: 205235d7-e621-4134-975c-257ae60939bc
source-git-commit: c0fa0717034e5094108eb1e23d4e9f1f16aeb57e
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 16%

---

# Service de notifications AEM Screens{#aem-screens-notifications-service}

<!--removed from metadata: admitteddomains: @adobe.com;@caesars.com-->

***Service de notifications AEM Screens*** décrit l’activité du moniteur d’appareil.

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
>To get access to this Feature Pack, you must contact Adobe Support and request access. Once you have permissions you can download it from Package Share. -->

## Vue d’ensemble {#overview}

***Service de notifications AEM Screens*** permet aux administrateurs de recevoir un e-mail si un lecteur AEM Screens n’exécute pas de ping pendant une période configurable.

Ce service peut être configuré dans la console web OSGi.

## Configuration des paramètres d’e-mail {#configuring-email-settings}

Pour configurer les paramètres de notification par e-mail, procédez comme suit :

1. Ouvrez le gestionnaire de **configuration de la console Web d’Adobe Experience Manager**.
1. Ouvrez le **Service de surveillance par e-mail des appareils Screens**.

   ![screen_shot_2018-04-26at44602pm](assets/screen_shot_2018-04-26at44602pm.png)

1. Définissez les champs suivants afin de pouvoir configurer les paramètres de l’e-mail :

   **Chemin d’accès aux appareils** Saisissez le chemin d’accès aux projets Screens que vous souhaitez surveiller. Le chemin est habituellement `/home/users/screens/<Name of your project>`.

   Par exemple, si votre projet est **`We.Retail`**, utilisez le chemin d’accès du projet comme ***/home/users/screens/we-retail***.

   >[!NOTE]
   >
   >Spécifiez le chemin du projet, où se trouvent les utilisateurs de l’appareil.

   **Fréquence de planification** - Spécifiez une heure (par exemple, 17 h ou 17 h) ou une fréquence en heures (par exemple, 1) à laquelle ce moniteur doit envoyer des e-mails.

   **Délai d’expiration du ping** - Indique l’intervalle en minutes après lequel un appareil doit être considéré comme inaccessible.

   **Serveur SMTP** - Spécifie le serveur SMTP utilisé pour envoyer des e-mails.

   **Port SMTP** - Saisissez le port SMTP.

   **Utiliser TLS** - TLS (Transport Layer Security) permet d’utiliser une communication sécurisée avec le serveur SMTP.

   Adobe recommande d’utiliser TLS pour une connexion sécurisée aux serveurs de messagerie d’entreprise. Vérifiez auprès de votre administrateur de messagerie les valeurs appropriées.

   **nom d&#39;utilisateur** - Spécifiez le nom d’utilisateur pour l’envoi des e-mails.

   **password** - Indiquez le mot de passe pour l’envoi des e-mails.

   **Destinataire** - Indiquez l’adresse e-mail du destinataire.

   >[!NOTE]
   >
   >Vous ne pouvez saisir qu’une seule adresse e-mail. Pour envoyer un e-mail en bloc, créez un groupe ou une liste de distribution avec les utilisateurs concernés.

1. Sélectionner **Enregistrer** pour configurer l’activité de surveillance par le biais d’un e-mail pour votre appareil AEM Screens.

## Notification par e-mail {#email-notification}

Après avoir défini la configuration de vos notifications par e-mail, vous recevez une notification par e-mail contenant le lien vers l’appareil réel qui est signalé comme étant inactif.

Accéder à ce lien vous permet d’accéder directement au tableau de bord de l’appareil.

Les e-mails ne sont envoyés que s’il existe au moins un appareil qui n’a pas envoyé de ping pendant le délai d’expiration du ping donné et qui n’envoie toujours pas de ping au moment de la génération de l’e-mail.

### Exemples de cas d’utilisation {#example-use-cases}

L’exemple suivant décrit quelques scénarios à titre de référence pour configurer les propriétés à partir du service de surveillance par e-mail des appareils Screens.

**Scénario 1**

Vous définissez la fréquence de planification sur 1 h du matin et le délai d’expiration du ping sur 60. Ensuite, si votre appareil AEM Screens n’exécute pas de ping entre 12 h 00 et 13 h 00, vous recevez une notification par e-mail qui confirme l’inactivité de l’appareil.

**Scénario 2**

Vous définissez la fréquence de planification sur 1 et le délai d’expiration du ping sur 60. Ensuite, si votre appareil AEM Screens n’effectue pas de ping entre une fois à un moment donné de la journée, vous recevez une notification par e-mail qui confirme l’inactivité de l’appareil.
