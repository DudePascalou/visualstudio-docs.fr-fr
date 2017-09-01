---
title: "Publication d’une application Python sur Azure App Service à partir de Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 7/13/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 85031f91-3a65-463b-a678-1e69f1b843e6
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: 9bce1901cc86eea29638d4a715c18c6367fa6dc6
ms.contentlocale: fr-fr
ms.lasthandoff: 07/18/2017

---

# <a name="publishing-to-azure-app-service"></a>Publication sur Azure App Service

Cet article décrit la procédure à suivre pour générer rapidement un site web Python dans Visual Studio, puis pour le publier sur Azure App Service :

- [Créer un abonnement Azure](#create-an-azure-subscription)
- [Créer et tester le projet initial](#create-and-test-the-initial-project)
- [Publier sur Azure App Service](#publish-to-azure-app-service)

Une brève procédure pas à pas de ce processus est présentée dans la vidéo [Visual Studio Python Tutorial: Building a Website](https://www.youtube.com/watch?v=FJx5mutt1uk&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=6) Didacticiel Python Visual Studio : Génération d’un site web), (youtube.com, 3 mn 10 s). 

> [!VIDEO https://www.youtube.com/embed/FJx5mutt1uk] 

## <a name="create-an-azure-subscription"></a>Créer un abonnement Azure

La publication sur Azure nécessite un abonnement Azure. Si vous n’avez pas d’abonnement, vous pouvez utiliser un site temporaire.

Pour les abonnements, démarrez avec un [compte Azure complet gratuit](https://azure.microsoft.com/en-us/free/), qui comprend de généreux crédits pour les services Azure. Envisagez également de vous inscrire à [Visual Studio Dev Essentials](https://azure.microsoft.com/en-us/pricing/member-offers/vs-dev-essentials/), qui vous offre 25 $ de crédit par mois pendant un an.

Pour créer un site temporaire dans Azure App Service sans souscrire un abonnement Azure :

1. Ouvrez votre navigateur au niveau du site [try.azurewebsites.net](https://try.azurewebsites.net).
1. Sélectionnez **Application web** pour le type d’application, puis sélectionnez **Suivant**.
1. Sélectionnez **Site vide** pour le modèle, puis sélectionnez **Créer >**.
1. Connectez-vous à l’aide de la connexion de réseau social de votre choix. Après un bref instant, votre site est prêt à l’adresse URL affichée.
1. Sélectionnez **Télécharger le profil de publication**, puis enregistrez le fichier `.publishsettings`, que vous utiliserez par la suite.

## <a name="create-and-test-the-initial-project"></a>Créer et tester le projet initial

1. Dans Visual Studio, sélectionnez **Fichier > Nouveau > Projet**, recherchez « Bottle », sélectionnez **Bottle Web Project** (Projet Web Bottle), puis cliquez sur **OK**.    

1. Lorsque vous êtes invité à installer les packages externes, sélectionnez **Install into a virtual environment** (Installer dans un environnement virtuel). Notez le contrôle **Afficher les packages nécessaires** au bas de la boîte de dialogue qui indique les packages qui seront installés :

  ![Installation des packages requis](media/tutorials-common-external-packages.png)

1. Sélectionnez votre interpréteur de base favori pour l’environnement virtuel (par exemple, **Python 2.7** ou **Python 3.4**), puis cliquez sur **Créer** :

  ![Ajout d’un environnement virtuel lors de la création d’un projet](media/tutorials-common-add-virtual-environment.png)

1. Une fois le projet créé, testez-le localement en sélectionnant **Débogage > Démarrer le débogage** ou en appuyant sur F5. Par défaut, l’application utilise un référentiel en mémoire qui ne requiert aucune configuration. Lorsque le serveur web sera arrêté, toutes les données seront perdues.

1. Cliquez sur les différentes zones de l’application pour tester son fonctionnement.

1. Lorsque vous avez terminé, arrêtez le débogueur (**Débogage > Arrêter le débogage** ou Maj+F5).

## <a name="publish-to-azure-app-service"></a>Publier sur Azure App Service

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Publier**. 

1. Dans la boîte de dialogue **Publier**, sélectionnez **Microsoft Azure App Service** :

  ![Publication sur Azure, étape 1](media/tutorials-common-publish-1.png)

1. Sélectionnez une cible :

    - Si vous disposez d’un abonnement Azure, sélectionnez **Microsoft Azure App Service** comme cible de publication, puis dans la boîte de dialogue suivante, sélectionnez un App Service existant ou sélectionnez **Nouveau** pour en créer un.
    - Si vous utilisez un site temporaire à partir de try.azurewebsites.net, sélectionnez **Importer** comme cible de publication, recherchez le fichier `.publishsettings` téléchargé à partir du site, puis sélectionnez **OK**.

1. Les détails d’App Service apparaissent dans l’onglet **Connexion** ci-dessous de la boîte de dialogue **Publier**.

  ![Publication sur Azure, étape 2](media/tutorials-common-publish-2.png)

1. Sélectionnez **Suivant >** autant de fois que nécessaire pour examiner les paramètres supplémentaires. Si vous prévoyez de [déboguer à distance votre code Python sur Azure](debugging-azure-remote.md), vous devez définir **Configuration** sur **Débogage**.
1. Sélectionnez **Publier**. Une fois votre application déployée sur Azure, votre navigateur par défaut s’ouvre au niveau de ce site. 