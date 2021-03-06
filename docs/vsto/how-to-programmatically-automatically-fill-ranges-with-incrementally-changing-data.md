---
title: 'Comment : remplir par programme automatiquement des plages avec des données soumises à modification incrémentielle | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Autofill method [Excel]
- filling ranges automatically
- ranges, automatically filling
- workbooks, filling ranges
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e358869dea101d0c0ca012acd46b7822e6cf5873
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-automatically-fill-ranges-with-incrementally-changing-data"></a>Comment : remplir automatiquement des plages avec des données soumises à modification incrémentielle par programmation
  Le <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> méthode de la <xref:Microsoft.Office.Interop.Excel.Range> objet permet de remplir automatiquement une plage dans une feuille de calcul avec des valeurs. En règle générale, le <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> méthode est utilisée pour stocker de façon incrémentielle valeurs croissantes ou décroissantes dans une plage. Vous pouvez spécifier le comportement en fournissant une constante facultative à partir de la <xref:Microsoft.Office.Interop.Excel.XlAutoFillType> énumération.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 Vous devez spécifier deux plages lors de l’utilisation <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A>:  
  
-   La plage qui appelle le <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> méthode, qui spécifie le point de départ du remplissage et contient une valeur initiale.  
  
-   La plage que vous souhaitez remplir, passée comme paramètre à la <xref:Microsoft.Office.Interop.Excel.Range.AutoFill%2A> (méthode). Cette plage de destination doit inclure la plage qui contient la valeur initiale.  
  
    > [!NOTE]  
    >  Vous ne pouvez pas passer un <xref:Microsoft.Office.Tools.Excel.NamedRange> contrôler à la place de la <xref:Microsoft.Office.Interop.Excel.Range>. Pour plus d'informations, consultez [Limitations de programmation des éléments hôtes et des contrôles hôtes](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
## <a name="example"></a>Exemple  
 [!code-csharp[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#49)]
 [!code-vb[Trin_VstcoreExcelAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#49)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 La première cellule de la plage que vous souhaitez remplir doit contenir une valeur initiale.  
  
 L’exemple requiert que vous remplissez les trois régions :  
  
-   La colonne B consiste à inclure les cinq jours de la semaine. Pour la valeur initiale, tapez **lundi** dans la cellule B1.  
  
-   La colonne C consiste à inclure les cinq derniers mois. Pour la valeur initiale, tapez **janvier** dans la cellule C1.  
  
-   La colonne D doit inclure une série de nombres, l’incrémentation par deux pour chaque ligne. Pour les valeurs initiales, tapez **4** dans la cellule D1 et **6** dans la cellule D2.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des plages](../vsto/working-with-ranges.md)   
 [Comment : faire référence par programmation aux plages de feuille de calcul dans le Code](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)   
 [Comment : appliquer des Styles à des plages dans les classeurs par programmation](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Comment : exécuter des calculs Excel par programmation](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)   
 [Vue d'ensemble des éléments hôtes et des contrôles hôtes](../vsto/host-items-and-host-controls-overview.md)   
 [Paramètres optionnels dans les solutions Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  