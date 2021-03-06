---
title: 'Comment : mettre en forme le texte dans des Documents par programmation | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- documents [Office development in Visual Studio], formatting text
- text [Office development in Visual Studio], formatting in documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a4f356da47a91e0f86f36594ff4254ca0d6ea3e5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-format-text-in-documents"></a>Comment : mettre en forme du texte dans des documents par programmation
  Vous pouvez utiliser l'objet <xref:Microsoft.Office.Interop.Word.Range> pour mettre en forme le texte dans un document Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 L'exemple suivant sélectionne le premier paragraphe du document et modifie la taille de la police, le nom de la police et l'alignement. Ensuite, il sélectionne la plage et affiche un message d'interruption avant l'exécution de la section de code suivante. La section suivante appelle la méthode d’annulation de la <xref:Microsoft.Office.Tools.Word.Document> élément hôte (pour une personnalisation au niveau du document) ou la <xref:Microsoft.Office.Interop.Word.Document> classe (pour un complément VSTO) trois fois. Il applique le style Retrait normal et affiche un message permettant de suspendre le code. Puis, le code appelle la méthode <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> une seule fois et affiche un message.  
  
## <a name="document-level-customization-example"></a>Exemple de personnalisation au niveau du document  
  
#### <a name="to-format-text-using-a-document-level-customization"></a>Pour mettre en forme un texte à l'aide d'une personnalisation au niveau du document  
  
1.  L'exemple suivant peut être utilisé dans une personnalisation au niveau du document. Pour utiliser ce code, exécutez-le à partir de la classe `ThisDocument` de votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#62)]  
  
## <a name="vsto-add-in-example"></a>Exemple de complément VSTO  
  
#### <a name="to-format-text-using-a-vsto-add-in"></a>Pour mettre en forme du texte avec un complément VSTO  
  
1.  L’exemple suivant peut être utilisé dans un complément VSTO. Cet exemple utilise le document actif. Pour utiliser ce code, exécutez-le à partir de la classe `ThisAddIn` de votre projet.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#62)]  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : définir par programme et sélectionner des plages dans des Documents](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Comment : insérer du texte dans des Documents Word par programmation](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Guide pratique pour rechercher et remplacer du texte dans les documents par programmation](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)  
  
  