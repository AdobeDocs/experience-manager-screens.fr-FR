---
title: Enregistrement en masse des joueurs
seo-title: Enregistrement en masse des joueurs
description: Suivez cette page pour en savoir plus sur l'enregistrement en masse des joueurs avec AMS/On-Prem Screens.
translation-type: tm+mt
source-git-commit: a00c761297b80239b741e68ef6f2ac611d3559f2
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---


# Enregistrement en masse des joueurs {#bulk-registration}

L&#39;enregistrement en masse de milliers de joueurs manuellement peut devenir très lourd et ajouter du temps et des coûts. Pour simplifier ce processus, la fonction d&#39;enregistrement en masse vous permet de spécifier une clé pré-partagée dans AEM qui peut être configurée dans un lecteur soit par le biais d&#39;un fichier de configuration, soit par une solution MDM (Mobile Device Management).

## Mise en oeuvre de l&#39;enregistrement en masse des joueurs {#bulk-registering-implementation}

Suivez les étapes ci-dessous pour mettre en oeuvre l&#39;enregistrement en masse des lecteurs :

1. Connectez-vous à votre instance AEM et sélectionnez votre projet AEM écrans, puis cliquez sur propriétés et sur l’onglet Avancé.
1. Vous devriez voir une section d&#39;enregistrement en masse dans laquelle vous pouvez spécifier un code d&#39;enregistrement en masse et un affichage par défaut facultatif à affecter au lecteur enregistré en masse.
1. Entrez le code de votre choix et sélectionnez un affichage par défaut si nécessaire.
1. Configurez vos lecteurs avec l’URL de serveur et le code d’enregistrement appropriés à l’aide d’un fichier MDM ou JSON de configuration. Pour plus d&#39;informations, reportez-vous à la page de mise en oeuvre du lecteur spécifique de votre système d&#39;exploitation. Vous pouvez également utiliser l’interface utilisateur d’administration pour saisir le code d’enregistrement.
1. Si l&#39;attribut `registrationKey` correspond à celui configuré en AEM, le lecteur s&#39;enregistre automatiquement et si un affichage par défaut est configuré, ce contenu est téléchargé et lu.

## Bonnes pratiques en matière de sécurité {#security-best-practices}

Suivez la section ci-dessous pour examiner certaines des meilleures pratiques en matière de sécurité :

* Pour vous assurer que le code d&#39;enregistrement n&#39;est pas compromis, configurez le code dans AEM juste avant de commencer l&#39;enregistrement en masse et, une fois terminé, effacez ce champ et enregistrez-le dans AEM.

* Vous pouvez configurer que l&#39;inscription `/bin/screens/`du chemin d&#39;accès n&#39;est accessible qu&#39;à partir de plages d&#39;adresses IP connues si possible.

* Pensez à utiliser un MDM pour configurer le lecteur avec la configuration.

* Utilisez toujours `HTTPS` et non `HTTP` pour la communication du lecteur avec AEM.

   >[!NOTE]
   >Actuellement, l&#39;affectation d&#39;affichage par défaut ne fonctionne que pour l&#39;enregistrement en masse et non pour l&#39;enregistrement manuel sans code d&#39;enregistrement.