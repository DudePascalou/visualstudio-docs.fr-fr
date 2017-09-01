---
title: "IRemoteDebugApplication::DisconnectDebugger | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.DisconnectDebugger
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::DisconnectDebugger"
ms.assetid: 989e5a34-0267-4a2e-96b6-e1dcc2ffe883
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::DisconnectDebugger
Déconnecte le débogueur actuel de l'application.  
  
## Syntaxe  
  
```  
HRESULT DisconnectDebugger();  
```  
  
#### Paramètres  
 Cette méthode n'accepte pas de paramètres.  
  
## Valeur de retour  
 La méthode retourne `HRESULT`.  Les valeurs possibles incluent, mais ne sont pas limitées à, celles dans le tableau suivant.  
  
|Valeur|Description|  
|------------|-----------------|  
|`S_OK`|La méthode a réussi.|  
  
## Notes  
 Cette méthode déconnecte le débogueur actuel de l'application.  
  
## Voir aussi  
 [IRemoteDebugApplication, interface](../../winscript/reference/iremotedebugapplication-interface.md)