---
title: Mark | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4c27d6ba2e5041596b171d1a2538c154c0fad8d8
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2018
---
# <a name="mark"></a>Marque
L’option **Mark** de VSPerfCmd.exe insère les informations spécifiées dans le fichier de données de profilage. Une marque peut apparaître dans un rapport VSPerfReport distinct ou dans la vue Rapport de marques de l’interface utilisateur du profileur. L’option **Mark** peut être utilisée pour spécifier des points de début et fin dans les filtres des rapports et des vues.  
  
 L’option **Mark** doit être la seule option spécifiée sur la ligne de commande.  
  
## <a name="syntax"></a>Syntaxe  
  
```cmd  
VSPerfCmd.exe /Mark:MarkID,[MarkName]  
```  
  
#### <a name="parameters"></a>Paramètres  
 `MarkID`  
 Entier défini par l’utilisateur, qui apparaît comme ID de marque dans les vues et les rapports de profileur. `MarkID` ne doit pas nécessairement être unique.  
  
 `MarkName`  
 (Facultatif) Chaîne définie par l’utilisateur, qui apparaît comme Nom de marque dans les vues et les rapports de profileur. Si `MarkName` n’est pas spécifié, le champ Nom de marque de la liste des marques est vide. Placez entre guillemets les chaînes qui contiennent des espaces ou des barres obliques (« / »).  
  
## <a name="example"></a>Exemple  
 Cet exemple insère une marque avec l’ID 123 et le nom de marque « TestMark ».  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
VSPerfCmd.exe /Mark:123,TestMark  
```  
  
## <a name="see-also"></a>Voir aussi  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilage d’applications autonomes](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilage d’applications web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilage de services](../profiling/command-line-profiling-of-services.md)