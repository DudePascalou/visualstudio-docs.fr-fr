---
title: IDiaPropertyStorage::ReadPropertyNames | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a13ac0e3a1af8dc20fe63f832e7a19d7bf40c271
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
Récupère correspondant de noms de chaîne pour donné des identificateurs de propriété.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cpropid`  
 [in] Nombre d’ID de propriété dans `rgpropid`.  
  
 `rgpropid`  
 [in] Tableau d’ID de propriété pour laquelle obtenir les noms (`PROPID` est défini dans WTypes.h comme un `ULONG`).  
  
 `rglpwstrName`  
 [dans, out] Tableau des noms de propriété pour les ID de propriété spécifiée. Le tableau doit être alloué au préalable pour contenir le nombre de noms de propriété demandé et doit être en mesure de contenir au moins `cpropid``BSTR` chaînes.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 Les noms de propriétés retourné doivent être libérées (en appelant le `SysFreeString` fonction) lorsqu’ils ne sont plus nécessaires.  
  
## <a name="see-also"></a>Voir aussi  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)