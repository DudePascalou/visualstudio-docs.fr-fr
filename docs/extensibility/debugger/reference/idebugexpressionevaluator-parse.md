---
title: IDebugExpressionEvaluator::Parse | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluator::Parse
helpviewer_keywords:
- IDebugExpressionEvaluator::Parse method
ms.assetid: e6e31b3a-63a7-4293-bcda-267eb78dffb6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2a10a65564682b5c82350eb5c22af3f217a3a993
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpressionevaluatorparse"></a>IDebugExpressionEvaluator::Parse
Cette méthode convertit une chaîne d’expression à une expression analysée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Parse(   
   LPCOLESTR                upstrExpression,  
   PARSEFLAGS               dwFlags,  
   UINT                     nRadix,  
   BSTR*                    pbstrError,  
   UINT*                    pichError,  
   IDebugParsedExpression** ppParsedExpression  
);  
```  
  
```csharp  
int Parse(  
   string                     upstrExpression,   
   enum_PARSEFLAGS            dwFlags,   
   uint                       nRadix,   
   out string                 pbstrError,   
   out uint                   pichError,   
   out IDebugParsedExpression ppParsedExpression  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `upstrExpression`  
 [in] La chaîne d’expression à analyser.  
  
 `dwFlags`  
 [in] Une collection de [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) constantes qui déterminent comment l’expression doit être analysée.  
  
 `nRadix`  
 [in] Base à utiliser pour interpréter les informations numériques.  
  
 `pbstrError`  
 [out] Retourne l’erreur en tant que texte explicite.  
  
 `pichError`  
 [out] Retourne la position de caractère de début de l’erreur dans la chaîne d’expression.  
  
 `ppParsedExpression`  
 [out] Retourne l’expression analysée dans un [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) objet.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Cette méthode génère une expression analysée, pas une valeur réelle. Une expression analysée est prête à être évaluée, autrement dit, convertie en une valeur.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)   
 [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md)