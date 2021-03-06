---
title: Page Déboguer, Concepteur de projets
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesDebug
helpviewer_keywords:
- Project Designer, Debug page
- Debug page in Project Designer
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5288005ad79b0455174292625bde9b5dbe4e584f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="debug-page-project-designer"></a>Page Déboguer, Concepteur de projets

> [!NOTE]
> Cette rubrique ne s’applique pas aux applications UWP. Consultez [Démarrer une session de débogage (VB, C#, C++ et XAML)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) dans le Centre de développement Windows.

 Utilisez la page **Déboguer** du **Concepteur de projets** afin de définir des propriétés pour le comportement de débogage dans un projet Visual Basic ou C#.

 Pour accéder à la page **Déboguer**, sélectionnez un nœud de projet dans **l’Explorateur de solutions**. Dans le menu **Projet**, choisissez *NomProjet***Propriétés**. Quand le **Concepteur de projets** s’affiche, cliquez sur l’onglet **Déboguer**.

## <a name="configuration-and-platform"></a>Configuration et Plateforme
 Les options suivantes vous permettent de sélectionner la configuration et la plateforme à afficher ou à modifier.

 **Configuration**

 Spécifie les paramètres de configuration à afficher ou à modifier. Les paramètres peuvent être **Debug** (valeur par défaut), **Release** ou **Toutes les configurations**.

 **Plateforme**

 Spécifie les paramètres de plateforme à afficher ou à modifier. Les choix possibles sont **Any CPU** (valeur par défaut), **x64** et **x86**.

## <a name="start-action"></a>Action de démarrage
 **Action de démarrage** indique à l’élément de démarrer quand l’application est déboguée : le projet, un programme personnalisé, une URL ou rien. Par défaut, la valeur affectée à cette option est **Démarrer le projet**. Le paramètre **Action de démarrage** dans la page **Déboguer** détermine la valeur de la propriété `StartAction`.

 **Démarrer le projet**

 Sélectionnez cette option pour spécifier que le fichier exécutable (pour les projets d’application Windows et d’application console) doit être démarré quand l’application est déboguée. Cette option est activée par défaut.

 **Démarrer le programme externe**

 Choisissez cette option pour indiquer qu’un programme spécifique doit démarrer quand l’application est déboguée.

 **Démarrer le navigateur avec l’URL**

 Choisissez cette option pour spécifier qu’une URL particulière doit être accessible quand l’application est déboguée.

## <a name="start-options"></a>Options de démarrage
 **Arguments de la ligne de commande**

 Dans cette zone de texte, entrez les arguments de la ligne de commande à utiliser pour le débogage.

 **Répertoire de travail**

 Dans cette zone de texte, entrez le répertoire à partir duquel le projet sera lancé. Vous pouvez aussi cliquer sur le bouton Parcourir (**...**) pour sélectionner un répertoire.

 **Utiliser l’ordinateur distant**

 Pour déboguer l’application à partir d’un ordinateur distant, cochez cette case, puis entrez le chemin d’accès à l’ordinateur distant dans la zone de texte.

## <a name="enable-debuggers"></a>Activer les débogueurs
 **Activer le débogage de code non managé**

 Cette option spécifie si le débogage de code natif est pris en charge. Cochez cette case si vous effectuez des appels vers les objets COM ou si vous démarrez un programme personnalisé écrit en code natif qui appelle votre projet et que vous devez déboguer le code natif. Décochez cette case pour désactiver le débogage de code non managé. Elle est désactivée par défaut.

 **Activer le débogage SQL Server**

 Cochez ou décochez cette case pour activer ou désactiver le débogage des procédures SQL de votre application Visual Basic. Elle est désactivée par défaut.

 **Activer le processus d’hébergement Visual Studio**

 Cochez cette case pour activer le processus d’hébergement Visual Studio. Elle est activée par défaut. Pour plus d’informations, consultez [Processus d’hébergement (vshost.exe)](../../ide/hosting-process-vshost-exe.md).

 Pour déboguer dans une zone de sécurité, vous devez activer cette option et **Déboguer cette application à l’aide du jeu d’autorisations sélectionné** dans la [boîte de dialogue Paramètres de sécurité avancés](../../ide/reference/advanced-security-settings-dialog-box.md).

## <a name="see-also"></a>Voir aussi

- [Débogage dans Visual Studio](../../debugger/debugging-in-visual-studio.md)
- [Paramètres de projet pour des configurations de débogage C#](../../debugger/project-settings-for-csharp-debug-configurations.md)
- [Paramètres de projet pour une configuration Debug Visual Basic](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Guide pratique pour déboguer une application ClickOnce avec des autorisations restreintes](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)
- [Guide pratique pour créer et modifier des configurations](../../ide/how-to-create-and-edit-configurations.md)