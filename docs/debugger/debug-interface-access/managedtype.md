---
title: ManagedType | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SymTagManagedType symbol
- managed type symbol
- ManagedType symbol
ms.assetid: 5db99e2a-4f2e-4796-89b7-b401b151826f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: d7f9058c207ff7830a6e3580e0a5bc66759973ef
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="managedtype"></a>ManagedType
Un type managé (n’importe quel symbole défini par les métadonnées ou du format natif vers la fonctionnalité de gestion de mémoire et de ressources de langages tels que c#) est identifié par un `SymTagManagedType` symbole.  
  
## <a name="properties"></a>Propriétés  
 Le tableau suivant montre des propriétés supplémentaires valides pour ce type de symbole.  
  
|Propriété|Type de données|Description|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nom du symbole managé.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID d’index du symbole.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Retourne `SymTagManagedType` (parmi les [symtagenum, énumération](../../debugger/debug-interface-access/symtagenum.md) valeurs).|  
  
## <a name="see-also"></a>Voir aussi  
 [Hiérarchie de classes des types de symboles](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)