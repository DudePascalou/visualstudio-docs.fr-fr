---
title: Boîte de dialogue Options de clavier Microsoft Office Word, paramètres du clavier Microsoft Office, | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Word.Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Word_Keyboard
- VST.WordOptions.KeyboardMappingScheme
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- keyboard shortcuts, Office development in Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d8747485ced6309bf9e63ecf864c67a111ce6c47
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Clavier Microsoft Office Word, Paramètres du clavier Microsoft Office, boîte de dialogue Options
  Microsoft Office Word et Visual Studio prennent en charge les touches de raccourci. La même combinaison de touches de raccourci peut correspondre à des commandes différentes dans Word et dans Visual Studio. Lorsque Word est ouvert dans un projet au niveau du document dans Visual Studio, une seule application à la fois reçoit les commandes de touches de raccourci. Par défaut, Visual Studio reçoit toutes les commandes de touches de raccourci, mais vous pouvez utiliser Word les reçoive lorsque le document a le focus en sélectionnant **schéma de clavier dynamique**.  
  
 Si vous utilisez la touche de raccourci qui n’est pas affectée à une commande dans l’application qui gère les touches de raccourci actuellement, la touche de raccourci est passée à l’autre application.  
  
 L’option que vous sélectionnez reste en vigueur pour les projets Word jusqu'à ce que vous la changiez. La sélection n’affecte pas les projets Microsoft Office Excel ; Vous devez vous une modification dans Excel en utilisant les options du clavier Microsoft Office Excel.  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
 **Schéma de clavier Visual Studio**  
 Visual Studio reçoit toutes les commandes de touches de raccourci, même si le document Word a le focus. Par exemple, si vous appuyez sur la touche de fonction F5 pendant que le document a le focus, Visual Studio commence à déboguer votre solution.  
  
 **Schéma de clavier dynamique**  
 Visual Studio reçoit les commandes de touches de raccourci uniquement lorsqu’il a le focus. Lorsque le document Word a le focus, Word reçoit toutes les commandes de touches de raccourci. Par exemple, si vous appuyez sur la touche de fonction F5 pendant que le document Word a le focus, Word ouvre le **rechercher et remplacer** boîte de dialogue avec le **atteindre** onglet sélectionné. Si vous appuyez sur F5 pendant que Visual Studio a le focus, Visual Studio démarre le débogage de votre solution.  
  
## <a name="see-also"></a>Voir aussi  
 [Clavier Microsoft Office Excel, Paramètres du clavier Microsoft Office, boîte de dialogue Options](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  