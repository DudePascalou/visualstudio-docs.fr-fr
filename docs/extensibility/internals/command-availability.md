---
title: Commande disponibilité | Documents Microsoft
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, context
- menu items, visibility contexts
ms.assetid: c74e3ccf-d771-48c8-a2f9-df323b166784
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 08f6ceb6c57eccf359b4aa23db7d693df3b86453
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="command-availability"></a>Disponibilité de la commande

Le contexte de Visual Studio détermine les commandes qui sont disponibles. Le contexte peut changer selon le projet en cours, l’éditeur actuel, les VSPackages sont chargés et autres aspects de l’environnement de développement intégré (IDE).

## <a name="command-contexts"></a>Contextes de commande

Les contextes de commande suivants sont les plus courantes.

-   **IDE** commandes fournies par l’IDE sont toujours disponibles.

-   **VSPackage** VSPackages peuvent définir quand les commandes sont à être affiché ou masqué.

-   **Projet** commandes projet s’affichent uniquement pour le projet sélectionné actuellement.

-   **Éditeur de** qu’un seul éditeur peut être actif à la fois. Les commandes à partir de l’éditeur actif sont disponibles. Un éditeur travaille en étroite collaboration avec un service de langage. Le service de langage doit traiter ses commandes dans le contexte de l’éditeur associé.

-   **Type de fichier** un éditeur peut charger plusieurs types de fichier. Les commandes disponibles peuvent varier selon le type de fichier.

-   **La fenêtre active** la dernière fenêtre de document actif définit le contexte d’interface utilisateur utilisateur pour les combinaisons de touches. Toutefois, une fenêtre outil qui a une table de liaisons de clés qui ressemble à du navigateur Web interne peut également définir le contexte de l’interface utilisateur. Pour les fenêtres de document d’à plusieurs onglets tels que l’éditeur HTML, chaque onglet possède un contexte de commande différents GUID. Après avoir enregistré une fenêtre outil, il est toujours disponible sur le **vue** menu.

-   **Contexte de l’interface utilisateur** contextes d’interface utilisateur sont identifiés par les valeurs de la <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> de classe, par exemple, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid> lorsque la solution est en cours de génération, ou <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid> lorsque le débogueur est actif. Plusieurs contextes d’interface utilisateur peuvent être actives à la fois.

## <a name="defining-custom-context-guids"></a>Définition des GUID de contexte personnalisé

Si un contexte de la commande appropriée que GUID n’est pas déjà défini, vous pouvez définir un dans votre VSPackage et puis qu’il soit actif ou inactif afin de contrôler la visibilité des commandes de votre programme.

1.  Enregistrez les GUID de contexte en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> (méthode).

2.  Obtenir l’état d’un GUID de contexte en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> (méthode).

3.  Activer et désactiver les GUID de contexte en appelant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> (méthode).

    > [!CAUTION]
    > Assurez-vous que votre VSPackage n’affecte pas les GUID de contexte existant, car d’autres packages VS dépendent les.

## <a name="see-also"></a>Voir aussi

- [Objets de contexte de sélection](../../extensibility/internals/selection-context-objects.md)
- [Comment VSPackages ajoute des éléments de l’interface utilisateur](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)