---
title: Concepteur de flux de travail - boîte de dialogue initialiser la corrélation
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- InitializeCorrelation.UI
ms.assetid: 2a0a1cd3-7b9e-493e-9264-fcf85289ffcf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93ce95c7a821d243af842170ba30ec82647933ab
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="initialize-correlation-dialog-box"></a>Boîte de dialogue Initialiser la corrélation

Le **initialiser la corrélation** boîte de dialogue est utilisée dans le Concepteur de flux de travail Windows pour modifier la <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> propriété d’un <xref:System.ServiceModel.Activities.InitializeCorrelation> activité. Pour plus d’informations, consultez la [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md) rubrique.

 Le tableau suivant décrit les éléments d’interface utilisateur utilisateur de la **initialiser la corrélation** boîte de dialogue.

|Élément d'interface utilisateur|Description|
|----------------|-----------------|
|**Corrélation**|Objet <xref:System.ServiceModel.Activities.CorrelationHandle> de la corrélation à initialiser.|
|**Initialiser sur**|Paire clé/valeur qui contient les données à initialiser. Cette valeur correspond à la propriété <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Un exemple d’une paire clé/valeur valide est une clé nommée « OrderID » associée à une variable nommée OrderID.|

## <a name="to-launch-the-initialize-correlation-dialog-box"></a>Pour lancer la boîte de dialogue Initialiser la corrélation

-   Cliquez sur **vue** sur la **InitializeCorrelation** activité concepteur ou sélectionnez un <xref:System.ServiceModel.Activities.InitializeCorrelation> activité dans Workflow Designer puis cliquez sur le bouton de sélection situé en regard du <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> propriété dans le grille des propriétés.

## <a name="see-also"></a>Voir aussi

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)