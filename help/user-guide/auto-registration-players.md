---
title: Enregistrement automatique des lecteurs
description: Consultez cette page pour en savoir plus sur l’enregistrement automatique des lecteurs avec AMS/On-Prem Screens.
feature: Administering Screens, Players
role: Admin
level: Intermediate
exl-id: 28449523-a44d-4260-9771-f1987686cbb6
TQID: https://experienceleague.adobe.com/uvCRS49L6CQbah4AKFwRdhGN-pvKnTWtNMN8CnFojIQ
product_v2: id: a27b4747-2f72-4fb7-9936-be5d11dd2c4aid: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2: id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 6ffdfa02d948d50b544f6fa5164dc6dca8bff638
workflow-type: tm+mt
source-wordcount: 388
ht-degree: 88%

---

# Enregistrement automatique des lecteurs {#auto-registration}

>[!IMPORTANT]
>Ce contenu est valide pour AEM on-premise/AMS (AEM 6.5LTS et AEM 6.5). Pour le contenu AEM as a Cloud Service Screens, reportez-vous au guide [AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/screens-as-cloud-service/overview/introduction).

L’enregistrement manuel en bloc de milliers de lecteurs peut devenir lourd, chronophage et coûteux. Pour simplifier ce processus, la fonction d’enregistrement en bloc vous permet de spécifier une clé prépartagée dans AEM qui peut être configurée dans un lecteur soit par le biais d’un fichier de configuration, soit par une solution MDM (Mobile Device Management).

## Mise en œuvre de l’enregistrement automatique des lecteurs {#bulk-registering-implementation}

Pour mettre en œuvre l’enregistrement automatique des lecteurs, procédez comme suit :

1. Connectez-vous à votre instance AEM et sélectionnez votre projet AEM Screens, puis cliquez sur **Propriétés** dans la barre d’actions.
1. Cliquez sur l’onglet **Avancé** pour afficher la section **Enregistrement des appareils**.

1. Spécifiez un code d’enregistrement automatique dans le champ **Code d’enregistrement en bloc**. Ensuite, un affichage par défaut facultatif s’affiche dans l’**Affectation d’affichage par défaut** pour l’affecter au lecteur enregistré automatiquement.

   >[!NOTE]
   >Saisissez le code de votre choix et cliquez sur un affichage par défaut si nécessaire.

   ![image](/help/user-guide/assets/auto-registration/auto-register1.png)
1. Configurez vos lecteurs avec l’URL de serveur et le code d’enregistrement appropriés à l’aide d’un fichier MDM ou JSON de configuration.

   >[!NOTE]
   >Pour plus d’informations, reportez-vous à la page de mise en œuvre pour le lecteur spécifique de votre système d’exploitation. Vous pouvez également utiliser l’interface utilisateur d’administration pour saisir le code d’enregistrement.

1. Si l’attribut `registrationKey` correspond à celui configuré dans AEM, le lecteur s’enregistre automatiquement et, dans le cas où un affichage par défaut a été configuré, ce contenu est téléchargé et lu.

   ![image](/help/user-guide/assets/auto-registration/auto-register2.png)

## Bonnes pratiques en matière de sécurité {#security-best-practices}

Consultez la section ci-dessous pour connaître certaines des bonnes pratiques en matière de sécurité :

* Pour vous assurer que le code d’enregistrement n’est pas compromis, configurez le code dans AEM juste avant de commencer l’enregistrement en bloc et, une fois terminé, effacez ce champ et enregistrez-le dans AEM.

* Si possible, vous pouvez configurer le chemin `/bin/screens/registration` pour qu’il soit accessible uniquement à partir de plages d’adresses IP connues.

* Pensez à utiliser une solution MDM pour approvisionner le lecteur avec la configuration.

* Utilisez toujours `HTTPS` et non `HTTP` pour la communication du lecteur avec AEM.

  >[!NOTE]
  >Actuellement, l’affectation d’affichage par défaut ne fonctionne que pour l’enregistrement en masse. Celle-ci ne fonctionne pas pour les enregistrements manuels lorsque le code d’enregistrement n’est pas disponible.

