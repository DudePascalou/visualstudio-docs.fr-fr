---
title: IActiveScriptSite::OnStateChange | Documents Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptSite.OnStateChange
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_OnStateChange
ms.assetid: 3e9c5cbe-ca8e-426a-84fd-04e9c2daac7e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fae7782d713ab226e57e687cda8eb4ccdb54cf20
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteonstatechange"></a>IActiveScriptSite::OnStateChange
Informe l’hôte que le moteur de script a modifié les États.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OnStateChange(  
    SCRIPTSTATE ssScriptState  // new state of engine  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ssScriptState`  
 [in] Valeur qui indique le nouvel état de script. Consultez le [IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md) méthode pour obtenir une description des États.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `S_OK` en cas de réussite.  
  
## <a name="see-also"></a>Voir aussi  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)