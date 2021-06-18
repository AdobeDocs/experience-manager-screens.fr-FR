---
title: Enregistrement automatique des lecteurs
seo-title: Enregistrement automatique des lecteurs
description: Consultez cette page pour en savoir plus sur l’enregistrement automatique des lecteurs avec Screens sur AMS/On-Premise.
feature: Administration de Screens, lecteurs
role: Administrator
level: Intermediate
source-git-commit: 4611dd40153ccd09d3a0796093157cd09a8e5b80
workflow-type: ht
source-wordcount: '342'
ht-degree: 100%

---


# Enregistrement automatique des lecteurs {#auto-registration}

L’enregistrement manuel en bloc de milliers de lecteurs peut devenir très lourd, chronophage et coûteux. Pour simplifier ce processus, la fonction d’enregistrement en bloc vous permet de spécifier une clé prépartagée dans AEM qui peut être configurée dans un lecteur soit par le biais d’un fichier de configuration, soit par une solution MDM (Mobile Device Management).

## Mise en œuvre de l’enregistrement automatique des lecteurs {#bulk-registering-implementation}

Suivez les étapes ci-dessous pour mettre en œuvre l’enregistrement automatique des lecteurs :

1. Connectez-vous à votre instance AEM et sélectionnez votre projet AEM Screens, puis cliquez sur **Propriétés** dans la barre d’actions.
1. Sélectionnez l’onglet **Avancé** pour afficher la section **Enregistrement de périphérique**.

1. Spécifiez un code d’enregistrement automatique dans le champ **Code d’enregistrement en bloc** et un affichage par défaut facultatif dans **Affectation d’affichage par défaut** pour les assigner au lecteur qui est enregistré automatiquement.
   >[!NOTE]
   >Entrez le code de votre choix et sélectionnez un affichage par défaut si nécessaire.

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
   >Actuellement, l’affectation d’affichage par défaut ne fonctionne que pour l’enregistrement en bloc et non pour l’enregistrement manuel sans code d’enregistrement.