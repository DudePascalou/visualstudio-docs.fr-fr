---
title: 'Comment : valider des données lorsqu’une nouvelle ligne est ajoutée à un contrôle ListObject'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], validating data
- ListObject control, new row
- ListObject control, validating data
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 55dc8852952482914bc57a41579163c90672d1db
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control"></a>Comment : valider des données lorsqu’une nouvelle ligne est ajoutée à un contrôle ListObject
  Les utilisateurs peuvent ajouter de nouvelles lignes à un contrôle <xref:Microsoft.Office.Tools.Excel.ListObject> qui est lié aux données. Vous pouvez valider les données de l’utilisateur avant d’approuver les modifications apportées à la source de données.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="data-validation"></a>Validation des données  
 Chaque fois qu’une ligne est ajoutée à un <xref:Microsoft.Office.Tools.Excel.ListObject> qui est lié aux données, l’événement <xref:Microsoft.Office.Tools.Excel.ListObject.BeforeAddDataBoundRow> est déclenché. Vous pouvez gérer cet événement pour effectuer la validation de vos données. Par exemple, si votre application requiert que seuls les employés âgés de 18 à 65 ans peuvent être ajoutés à la source de données, vérifiez que l’âge entré est compris dans cette plage avant la ligne est ajoutée.  
  
> [!NOTE]  
>  Vous devez toujours vérifier l’entrée d’utilisateur sur le client, mais aussi sur le serveur. Pour plus d’informations, consultez [sécuriser les applications clientes](/dotnet/framework/data/adonet/secure-client-applications).  
  
### <a name="to-validate-data-when-a-new-row-is-added-to-data-bound-listobject"></a>Pour valider des données lorsqu’une nouvelle ligne est ajoutée à un ListObject lié aux données  
  
1.  Créez des variables pour l’ID et <xref:System.Data.DataTable> au niveau de la classe.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#8)]
     [!code-vb[Trin_VstcoreHostControlsExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#8)]  
  
2.  Créer un nouveau <xref:System.Data.DataTable> et ajoutez des exemples de colonnes et les données dans le `Startup` Gestionnaire d’événements de la `Sheet1` classe (dans un projet au niveau du document) ou `ThisAddIn` classe (dans un projet de complément VSTO).  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#9)]
     [!code-vb[Trin_VstcoreHostControlsExcel#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#9)]  
  
3.  Ajoutez du code au gestionnaire d’événements `list1_BeforeAddDataBoundRow` pour vérifier si l’âge entré est compris dans la plage autorisée.  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreHostControlsExcelCS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreHostControlsExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsExcelVB/Sheet1.vb#10)]  
  
## <a name="compile-the-code"></a>Compiler le code  
 Cet exemple de code suppose qu’un <xref:Microsoft.Office.Tools.Excel.ListObject> nommé `list1` existe dans la feuille de calcul dans laquelle ce code apparaît.  
  
## <a name="see-also"></a>Voir aussi  
 [Étendre des documents Word et classeurs Excel dans des Compléments VSTO lors de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Contrôles sur des documents Office](../vsto/controls-on-office-documents.md)   
 [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [ListObject (contrôle)](../vsto/listobject-control.md)   
 [Automatisation d’Excel à l’aide d’objets étendus](../vsto/automating-excel-by-using-extended-objects.md)   
 [Comment : colonnes ListObject de mappage de données](../vsto/how-to-map-listobject-columns-to-data.md)  
  
  