---
title: Enregistrement automatique des lecteurs
seo-title: Enregistrement automatique des lecteurs
description: Suivez cette page pour en savoir plus sur l'enregistrement automatique des joueurs avec AMS/On-Prem Screens.
translation-type: tm+mt
source-git-commit: 56432654d0895b892223677c8a03f10181864271
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---


# Enregistrement automatique des joueurs {#auto-registration}

L&#39;enregistrement en masse de milliers de joueurs manuellement peut devenir très lourd et ajouter du temps et des coûts. Pour simplifier ce processus, la fonction d&#39;enregistrement en masse vous permet de spécifier une clé pré-partagée dans AEM qui peut être configurée dans un lecteur soit par le biais d&#39;un fichier de configuration, soit par une solution MDM (Mobile Device Management).

## Mise en oeuvre de l&#39;enregistrement automatique des joueurs {#bulk-registering-implementation}

Suivez les étapes ci-dessous pour mettre en oeuvre l’enregistrement automatique des lecteurs :

1. Connectez-vous à votre instance AEM et sélectionnez votre projet AEM écrans, puis cliquez sur **Propriétés** dans la barre d’actions.
1. Sélectionnez l&#39;onglet **Avancé** pour vue à la section **Enregistrement de périphérique**, comme illustré ci-dessous.

   ![image](/help/user-guide/assets/auto-registration/auto-register1.png)

1. Spécifiez un code d’enregistrement automatique dans le champ **Code d’enregistrement en bloc** et un affichage par défaut facultatif dans **Affectation d’affichage par défaut** à affecter au lecteur qui est enregistré automatiquement.
   >[!NOTE]
   >Entrez le code de votre choix et sélectionnez un affichage par défaut si nécessaire.
1. Configurez vos lecteurs avec l’URL de serveur et le code d’enregistrement appropriés à l’aide d’un fichier MDM ou JSON de configuration.

   >[!NOTE]
   >Pour plus d’informations, reportez-vous à la page de mise en oeuvre du lecteur spécifique de votre système d’exploitation. Vous pouvez également utiliser l’interface utilisateur d’administration pour saisir le code d’enregistrement.

1. Si l&#39;attribut `registrationKey` correspond à celui configuré en AEM, le lecteur s&#39;enregistre automatiquement et si un affichage par défaut est configuré, ce contenu est téléchargé et lu.

   ![image](/help/user-guide/assets/auto-registration/auto-register2.png)

## Bonnes pratiques en matière de sécurité {#security-best-practices}

Suivez la section ci-dessous pour examiner certaines des meilleures pratiques en matière de sécurité :

* Pour vous assurer que le code d&#39;enregistrement n&#39;est pas compromis, configurez le code dans AEM juste avant de commencer l&#39;enregistrement en masse et, une fois terminé, effacez ce champ et enregistrez-le dans AEM.

* Vous pouvez configurer que l&#39;inscription `/bin/screens/`du chemin d&#39;accès n&#39;est accessible qu&#39;à partir de plages d&#39;adresses IP connues si possible.

* Pensez à utiliser un MDM pour configurer le lecteur avec la configuration.

* Utilisez toujours `HTTPS` et non `HTTP` pour la communication du lecteur avec AEM.

   >[!NOTE]
   >Actuellement, l&#39;affectation d&#39;affichage par défaut ne fonctionne que pour l&#39;enregistrement en masse et non pour l&#39;enregistrement manuel sans code d&#39;enregistrement.