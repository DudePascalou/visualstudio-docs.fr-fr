---
title: FindInList, tâche | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindInList task [MSBuild]
- MSBuild, FindInList task
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 85d45bb5494f3cf3a4bd06103e05fb17d6f1d00b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="findinlist-task"></a>FindInList, tâche
Dans une liste spécifiée, recherche un élément associé à la spécification d’éléments (itemspec) correspondante.  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la [tâche FindInList](../msbuild/findinlist-task.md).  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`CaseSensitive`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, la recherche respecte la casse ; sinon, elle ne la respecte pas. La valeur par défaut est `true`.|  
|`FindLastMatch`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, retourne la dernière correspondance ; sinon, retourne la première correspondance. La valeur par défaut est `false`.|  
|`ItemFound`|Paramètre de sortie en lecture seule <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Premier élément correspondant trouvé dans la liste, le cas échéant.|  
|`ItemSpecToFind`|Paramètre `String` requis.<br /><br /> Spécification d’éléments (itemspec) à rechercher.|  
|`List`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Liste dans laquelle rechercher la spécification d’éléments (itemspec).|  
|`MatchFileNameOnly`|Paramètre `Boolean` facultatif.<br /><br /> Si `true`, effectue une comparaison avec uniquement la partie de nom de fichier de l’itemspec ; sinon, effectue une comparaison avec l’intégralité de l’itemspec. La valeur par défaut est `true`.|  
  
## <a name="remarks"></a>Notes  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.TaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.Task>. Pour obtenir la liste de ces paramètres supplémentaires et leurs descriptions, consultez [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)