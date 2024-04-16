---
title: Enregistrement automatique des lecteurs
description: Consultez cette page pour en savoir plus sur l’enregistrement automatique des lecteurs avec AMS/On-Prem Screens.
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 28449523-a44d-4260-9771-f1987686cbb6
source-git-commit: fff2df02661fc3fb3098be40e090b8bc6925bcc2
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 45%

---

# Enregistrement automatique des lecteurs {#auto-registration}

L’enregistrement en masse de milliers de lecteurs manuellement peut devenir encombrant et ajouter du temps et des coûts. Pour simplifier ce processus, la fonction d’enregistrement en bloc vous permet de spécifier une clé pré-partagée dans AEM qui peut être configurée dans un lecteur via un fichier de configuration ou une solution de gestion des périphériques mobiles (MDM).

## Mise en œuvre de l’enregistrement automatique des lecteurs {#bulk-registering-implementation}

Suivez les étapes ci-dessous pour mettre en œuvre l’enregistrement automatique des lecteurs :

1. Connectez-vous à votre instance AEM et cliquez sur votre projet AEM Screens, puis sur **Propriétés** dans la barre d’actions.
1. Cliquez sur le bouton **Avancé** afin que vous puissiez afficher la **Enregistrement de périphériques** .

1. Spécifiez un code d’enregistrement automatique dans le champ **Code d’enregistrement en bloc** et un affichage par défaut facultatif dans **Affectation d’affichage par défaut** pour les assigner au lecteur qui est enregistré automatiquement.

   >[!NOTE]
   >Saisissez le code de votre choix et cliquez sur un affichage par défaut, le cas échéant.

   ![image](/help/user-guide/assets/auto-registration/auto-register1.png)
1. Configurez vos lecteurs avec l’URL de serveur et le code d’enregistrement appropriés à l’aide d’un fichier MDM ou JSON de configuration.

   >[!NOTE]
   >Pour plus d’informations, consultez la page de mise en oeuvre du lecteur spécifique à votre système d’exploitation. Vous pouvez également utiliser l’interface utilisateur d’administration pour saisir le code d’enregistrement.

1. Si la variable `registrationKey` correspond à celui configuré dans AEM, le lecteur s’enregistre automatiquement et, si un affichage par défaut est configuré, ce contenu est téléchargé et lu.

   ![image](/help/user-guide/assets/auto-registration/auto-register2.png)

## Bonnes pratiques en matière de sécurité {#security-best-practices}

Consultez la section ci-dessous pour connaître certaines des bonnes pratiques en matière de sécurité :

* Assurez-vous que le code d’enregistrement n’est pas compromis. Configurez le code dans AEM juste avant de commencer l’enregistrement en masse. Une fois l’opération terminée, effacez ce champ et enregistrez-le dans AEM.

* Si possible, vous pouvez configurer le chemin `/bin/screens/registration` pour qu’il soit accessible uniquement à partir de plages d’adresses IP connues.

* Pensez à utiliser une solution MDM pour approvisionner le lecteur avec la configuration.

* Utilisez toujours `HTTPS` et non `HTTP` pour la communication du lecteur avec AEM.

  >[!NOTE]
  >Actuellement, l’affectation d’affichage par défaut ne fonctionne que pour l’enregistrement en bloc et non pour l’enregistrement manuel sans code d’enregistrement.
