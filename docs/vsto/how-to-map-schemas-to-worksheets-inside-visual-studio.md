---
title: 'Comment : mapper des schémas à des feuilles de calcul à l’intérieur de Visual Studio | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Excel worksheets
- Excel [Office development in Visual Studio], XML schemas
- worksheets [Office development in Visual Studio], XML schemas
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b2d0caadfc08d7fa1d2ea29d04e84a5d954a42fd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-map-schemas-to-worksheets-inside-visual-studio"></a>Comment : mapper des schémas à des feuilles de calcul dans Visual Studio
  Lorsque la feuille de calcul est ouverte dans Visual Studio, vous pouvez mapper un schéma XML à une feuille de calcul. Vous utilisez les mêmes outils Microsoft Office Excel que vous utilisez lorsque le classeur est ouvert en dehors de Visual Studio. Le projet Office crée les mêmes objets que vous mappiez le schéma à la feuille de calcul avant ou après avoir créé votre solution Excel.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Vous ne pouvez pas utiliser les schémas XML en plusieurs parties dans les solutions Excel.  
  
### <a name="to-map-an-xml-schema-to-an-excel-worksheet-in-visual-studio"></a>Pour mapper un schéma XML à une feuille de calcul Excel dans Visual Studio  
  
1.  Ouvrez le projet de classeur ou de modèle Excel dans Visual Studio.  
  
2.  Cliquez dans la feuille de calcul pour déplacer le focus vers le concepteur.  
  
3.  Dans le ruban, cliquez sur l'onglet **Développeur** .  
  
    > [!NOTE]  
    >  Si l'onglet **Développeur** n'est pas visible, vous devez tout d'abord l'afficher. Pour plus d'informations, consultez [Comment : afficher l'onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  Dans le **XML** , cliquez sur **Source**.  
  
     Le **Source XML** fenêtre s’ouvre.  
  
5.  Dans le **Source XML** fenêtre, cliquez sur **mappages XML**.  
  
     Le **mappages XML** boîte de dialogue s’ouvre.  
  
6.  Dans le **mappages XML** boîte de dialogue, cliquez sur **ajouter**.  
  
7.  Accédez à votre fichier de schéma, sélectionnez-le, puis cliquez sur **ouvrir**.  
  
8.  Cliquez sur **OK**.  
  
     Le schéma est représenté dans le **Source XML** fenêtre. Dans votre projet, un typé <xref:System.Data.DataSet> est généré en fonction du schéma et un <xref:System.Windows.Forms.BindingSource> est créé.  
  
9. Faire glisser des éléments à partir de la **Source XML** fenêtre aux endroits de votre feuille de calcul où vous souhaitez que les contrôles correspondants à créer.  
  
     Si vous faites glisser un élément de schéma non répétés, le projet Office génère une <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> contrôle qui est automatiquement lié à la <xref:System.Windows.Forms.BindingSource>.  
  
     Si vous faites glisser un élément de schéma répétitif, le projet Office génère un <xref:Microsoft.Office.Tools.Excel.ListObject> contrôle qui n’est pas lié automatiquement à une source de données. Pour plus d’informations, consultez [schémas et données dans les personnalisations au niveau du Document XML](../vsto/xml-schemas-and-data-in-document-level-customizations.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : mapper des schémas à des Documents Word dans Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Schémas et données XML dans les personnalisations au niveau du document](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  