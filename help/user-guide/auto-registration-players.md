---
title: Enregistrement automatique des lecteurs
description: Consultez cette page pour en savoir plus sur l’enregistrement automatique des lecteurs avec AMS/On-Prem Screens.
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 28449523-a44d-4260-9771-f1987686cbb6
source-git-commit: c0fa0717034e5094108eb1e23d4e9f1f16aeb57e
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 49%

---

# Enregistrement automatique des lecteurs {#auto-registration}

L’enregistrement en masse manuel de milliers de joueurs peut devenir fastidieux et augmenter le temps et les coûts. Pour simplifier ce processus, la fonction d’enregistrement en bloc vous permet de spécifier une clé prépartagée dans AEM qui peut être configurée dans un lecteur via un fichier de configuration ou une solution de gestion des appareils mobiles (MDM).

## Mise en œuvre de l’enregistrement automatique des lecteurs {#bulk-registering-implementation}

Suivez les étapes ci-dessous pour mettre en œuvre l’enregistrement automatique des lecteurs :

1. Connectez-vous à votre instance AEM, sélectionnez votre projet AEM Screens et cliquez sur **Propriétés** à partir de la barre d’actions.
1. Sélectionner le **Avancé** afin de pouvoir afficher le **Enregistrement d’appareil** section.

1. Spécifiez un code d’enregistrement automatique dans le champ **Code d’enregistrement en bloc** et un affichage par défaut facultatif dans **Affectation d’affichage par défaut** pour les assigner au lecteur qui est enregistré automatiquement.

   >[!NOTE]
   >Entrez le code de votre choix et sélectionnez un affichage par défaut si nécessaire.

   ![image](/help/user-guide/assets/auto-registration/auto-register1.png)
1. Configurez vos lecteurs avec l’URL de serveur et le code d’enregistrement appropriés à l’aide d’un fichier MDM ou JSON de configuration.

   >[!NOTE]
   >Pour plus d’informations, reportez-vous à la page de mise en œuvre du lecteur spécifique à votre système d’exploitation. Vous pouvez également utiliser l’interface utilisateur d’administration pour saisir le code d’enregistrement.

1. Si le `registrationKey` L’attribut correspond à celui configuré dans AEM, le lecteur s’enregistre automatiquement et, si un affichage par défaut est configuré, le contenu est téléchargé et lu.

   ![image](/help/user-guide/assets/auto-registration/auto-register2.png)

## Bonnes pratiques en matière de sécurité {#security-best-practices}

Consultez la section ci-dessous pour connaître certaines des bonnes pratiques en matière de sécurité :

* Assurez-vous que le code d’enregistrement n’est pas compromis : configurez le code dans AEM juste avant de commencer l’enregistrement en bloc et, une fois cette opération terminée, effacez ce champ et enregistrez-le dans AEM.

* Si possible, vous pouvez configurer le chemin `/bin/screens/registration` pour qu’il soit accessible uniquement à partir de plages d’adresses IP connues.

* Pensez à utiliser une solution MDM pour approvisionner le lecteur avec la configuration.

* Utilisez toujours `HTTPS` et non `HTTP` pour la communication du lecteur avec AEM.

  >[!NOTE]
  >Actuellement, l’affectation d’affichage par défaut ne fonctionne que pour l’enregistrement en bloc et non pour l’enregistrement manuel sans code d’enregistrement.
