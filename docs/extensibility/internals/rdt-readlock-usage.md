---
title: L’utilisation de RDT_ReadLock | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- RDT_ReadLock
- visible
- RDT_EditLock
- invisible
ms.assetid: b935fc82-9d6b-4a8d-9b70-e9a5c5ad4a55
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7fda2fbb4a4b03dff9d677d9c7581a4138d9fcf7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="rdtreadlock-usage"></a>Utilisation de RDT_ReadLock

<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> est un indicateur qui fournit la logique pour le verrouillage d’un document dans l’exécution Document Table d’exécution, qui est la liste de tous les documents actuellement ouverts dans l’IDE de Visual Studio. Cet indicateur détermine quand les documents sont ouverts, et si le document est visible dans l’interface utilisateur ou stockées de manière invisible en mémoire.

En règle générale, vous utiliseriez <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> lorsque une des valeurs suivantes est remplie :

- Lorsque vous souhaitez ouvrir un document de manière invisible et en lecture seule, mais il n’est pas encore établi qui <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> il doit appartenir.

- Lorsque vous souhaitez que l’utilisateur à être invité à enregistrer un document qui a été ouvert de façon invisible avant l’affichage dans l’interface utilisateur de l’utilisateur et puis a tenté de fermer.

## <a name="how-to-manage-visible-and-invisible-documents"></a>Comment gérer des Documents visibles et invisibles

Lorsqu’un utilisateur ouvre un document dans l’interface utilisateur, un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> propriétaire pour le document doit être établie et un <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> indicateur doit être défini. Si aucun <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> propriétaire peut être établi, puis le document n’est pas enregistré lorsque l’utilisateur clique sur **Enregistrer tout** ou ferme l’IDE. Cela signifie que si un document est ouvert de manière invisible où il est modifié dans la mémoire, et l’utilisateur est invité à enregistrer le document lors de l’arrêt ou enregistré si **Enregistrer tout** est choisie, alors un `RDT_ReadLock` ne peut pas être utilisé. Au lieu de cela, vous devez utiliser un `RDT_EditLock` et inscrire un <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> lorsqu’un <xref:Microsoft.VisualStudio.Shell.Interop.__VSREGDOCLOCKHOLDER> indicateur.

## <a name="rdteditlock-and-document-modification"></a>RDT_EditLock et Modification de documents

L’indicateur de précédente mentionné indique que l’invisible lors de l’ouverture du document génère son `RDT_EditLock` lorsque le document est ouvert par l’utilisateur dans un visible **DocumentWindow**. Lorsque cela se produit, l’utilisateur est présenté avec un **enregistrer** invite lorsque le texte visible **DocumentWindow** est fermé. `Microsoft.VisualStudio.Package.Automation.OAProject.CodeModel` les implémentations qui utilisent la <xref:Microsoft.VisualStudio.Shell.Interop.IVsInvisibleEditorManager> service fonctionne initialement lorsque seul un `RDT_ReadLock` est effectuée (par exemple, lorsque le document est ouvert de manière invisible pour analyser les informations). Ultérieurement, si le document doit être modifié, puis le verrou est mis à niveau vers un faible **RDT_EditLock**. Si l’utilisateur ouvre ensuite le document dans un visible **DocumentWindow**, le `CodeModel`de faible `RDT_EditLock` est libérée.

Si l’utilisateur puis ferme le **DocumentWindow** et choisit **non** lorsque vous êtes invité à enregistrer le document ouvert, puis le `CodeModel` implémentation supprime toutes les informations dans le document et en rouvre le document à partir du disque de manière invisible la prochaine fois que des informations supplémentaires sont requises pour le document. Le plusieurs de ce comportement est une instance où l’utilisateur ouvre le **DocumentWindow** du document ouvert invisible, modifie, ferme et choisit ensuite **non** lorsque vous êtes invité à enregistrer le document. Dans ce cas, si le document a un `RDT_ReadLock`, le document ne sera pas réellement fermé, puis le document modifié reste ouvert de manière invisible en mémoire, même si l’utilisateur choisi de ne pas enregistrer le document.

Si l’ouverture invisible du document utilise un faible `RDT_EditLock`, puis il donne son verrou lorsque l’utilisateur ouvre le document visiblement et aucun verrou n’est maintenu. Lorsque l’utilisateur ferme le **DocumentWindow** et choisit **non** lorsque vous êtes invité à enregistrer le document, le document doit être fermé à partir de la mémoire. Cela signifie que le client invisible doit écouter les événements de r & DT suivre cette occurrence. La prochaine fois que le document est requis, le document doit être rouvert.