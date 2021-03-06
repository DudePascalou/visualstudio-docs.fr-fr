---
title: Déployer vers un dossier local
description: Déployer une application vers un dossier local
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: bd477fec033eb75f626401586abfd10c798601ef
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2018
---
1. Dans le **l’Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **publier** (pour Web Forms, **publier l’application Web**).

    Si vous avez déjà configuré des profils de publication, le **publier** volet s’affiche. Cliquez sur **nouveau profil**.

1. Dans le **publier** boîte de dialogue, sélectionnez **dossier**, cliquez sur **Parcourir**et créer un nouveau dossier, **C:\Publish**.

    ![RemoteDBG_Publish_Local](../media/remotedbg_publish_local.png "RemoteDBG_Publish_Local")

    Pour une application Web Forms, choisissez **personnalisé** dans la boîte de dialogue Publier, entrez un nom de profil, puis choisissez **OK**.

1. Cliquez sur **créer profil** dans la liste déroulante (**publier** est la valeur par défaut).

1. Dans le **publier** boîte de dialogue, cliquez sur le **paramètres** lier, puis sélectionnez le **paramètres** onglet.

1. La configuration de la valeur **déboguer**, sélectionnez **supprimer tous les fichiers existants avant de publier**, puis cliquez sur **enregistrer**.

    > [!NOTE]
    > Si vous utilisez une version Release, vous désactivez le débogage dans le fichier web.config lorsque vous publiez.

1. Cliquez sur **Publier**.

    ![RemoteDBG_Publish_Debug_Config](../media/remotedbg_publish_debug_config.png "RemoteDBG_Publish_Debug_Config")
    
    L’application publie un **déboguer** configuration du projet dans le dossier local. Progression s’affiche dans la fenêtre Sortie.

1. Copiez le répertoire du projet ASP.NET à partir de l’ordinateur Visual Studio dans le répertoire local est configuré pour l’application ASP.NET (dans cet exemple, **C:\Publish**) sur l’ordinateur Windows Server. Dans ce didacticiel, nous supposons que vous copiez manuellement, mais vous pouvez utiliser d’autres outils tels que PowerShell, Xcopy ou Robocopy.

    > [!CAUTION]
    >  Si vous devez apporter des modifications à du code ou la régénération, vous devez republier et répétez cette étape. Le fichier exécutable que vous avez copié sur l’ordinateur distant doit correspondre exactement à la source et aux symboles locaux.    Si vous ne le faites pas vous recevrez un `cannot find or open the PDB file` avertissement dans Visual Studio lorsque vous essayez de déboguer le processus.

1. Sur le serveur Windows, vérifiez que vous pouvez exécuter l’application correctement en ouvrant l’application dans votre navigateur.

    Si l’application ne s’exécute pas correctement, il peut y avoir une incompatibilité entre la version d’ASP.NET installés sur votre serveur et sur votre ordinateur Visual Studio, ou vous pouvez avoir un problème avec votre configuration d’IIS ou le site Web. Revérifier les étapes précédentes.
