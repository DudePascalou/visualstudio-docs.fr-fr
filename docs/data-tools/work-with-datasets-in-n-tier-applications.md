---
title: Utiliser des jeux de données dans les applications multicouches
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], n-tier applications
- multi-tier database applications
- DataSet project [VS n-tier applications]
- distributed applications [VS n-tier applications]
- data [Visual Basic], n-tier applications
- TableAdapters, n-tier applications
- n-tier applications
- tiers, n-tier applications
- typed datasets, n-tier applications
- multiple tier applications
ms.assetid: f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f97e0d4c0cd16fd2bc7cc8bf140a59a800a254ac
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Utiliser des jeux de données dans les applications multicouches

*Applications de données multicouches* sont des applications orientées données sont divisées en plusieurs couches logiques (ou *niveaux*). En d'autres termes, une application de données multicouche est une application divisée en plusieurs projets, avec une couche d'accès aux données, une couche de logique métier et une couche Présentation dans son propre projet. Pour plus d’informations, consultez [vue d’ensemble des Applications de données multicouches](../data-tools/n-tier-data-applications-overview.md).

Les datasets typés ont été améliorés de sorte que les TableAdapters et les classes DataSet puissent être générés dans des projets distincts. Cela permet de rapidement séparer les couches de l'application et de générer des applications de données multicouches.

Prise en charge du multicouche dans les datasets typés permet le développement itératif de l’architecture d’application à une conception multicouche. Elle supprime également la nécessité de séparer manuellement le code en plusieurs projets. Commencez la conception de la couche données à l’aide de la **Concepteur de Dataset**. Lorsque vous êtes prêt à l’architecture d’application à une conception multicouche, définissez la **projet DataSet** propriété d’un dataset pour générer la classe dataset dans un projet séparé.

## <a name="reference"></a>Référence

- <xref:System.Data.DataSet>
- <xref:System.Data.TypedTableBase%601>

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des applications de données multiniveaux](../data-tools/n-tier-data-applications-overview.md)
- [Procédure pas à pas : création d’une application de données multiniveau](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Guide pratique pour ajouter du code aux TableAdapters dans des applications multiniveaux](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Guide pratique pour ajouter du code à des datasets dans des applications multiniveaux](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Guide pratique pour ajouter la validation à un dataset multiniveau](../data-tools/add-validation-to-an-n-tier-dataset.md)
- [Guide pratique pour séparer les datasets et les TableAdapters en différents projets](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)
- [Mise à jour hiérarchique](../data-tools/hierarchical-update.md)
- [Outils de dataset dans Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Accès aux données dans Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Créer et configurer des TableAdapters](../data-tools/create-and-configure-tableadapters.md)
- [Applications multicouches et distantes avec LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)