---
title: 'Le Concepteur de flux de travail - Comment : ajouter des activités à la boîte à outils'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4edb752ca64afd899ac9b3e463b9d29e4b3b68a1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-add-activities-to-the-toolbox"></a>Comment : ajouter des activités à la boîte à outils

Les activités peuvent être ajoutées à la **boîte à outils** dans votre solution de plusieurs façons différentes. Vous pouvez les ajouter à partir de votre projet en cours, les référencer à partir d'un autre projet ou les référencer à partir d'un autre assembly.

## <a name="to-add-an-activity-from-within-your-current-project"></a>Pour ajouter une activité à partir de votre projet en cours

1.  Ajoutez une nouvelle activité personnalisée à votre projet de workflow actif. Pour plus d’informations sur l’ajout d’une nouvelle activité personnalisée à votre projet, consultez [Comment : ajouter un nouvel élément à un projet de flux de travail](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md).

2.  Ajoutez une logique personnalisée à votre activité.

3.  Générez le projet. Si la génération a réussi, une nouvelle catégorie dans le **boîte à outils** nommé «\<*nom du projet*> » avec l’activité personnalisée incluse dans cette catégorie s’affiche.

    > [!NOTE]
    > Si la boîte à outils est réinitialisée, des activités personnalisées sont supprimées, même si la solution est générée à nouveau. Pour remplir de nouveau la boîte à outils avec des activités personnalisées après que qu’il a été réinitialisé, redémarrez Visual Studio 2010.

    > [!NOTE]
    > La boîte à outils ne peut afficher qu'une activité d'un nom donné. Si deux activités de différents assemblys ont le même nom de classe, une seule s'affiche.

    > [!NOTE]
    > Le domaine d'application est partagé entre des instances de l'éditeur ; si des variables statiques sont utilisées, elles sont également partagées par les instances de l'éditeur. S'il ne s'agit pas du comportement souhaité, un service doit être utilisé pour assurer le suivi des instances variables. Consultez [en utilisant le contexte d’édition ModelItem](/dotnet/framework/windows-workflow-foundation/using-the-modelitem-editing-context) pour plus d’informations sur l’utilisation de services dans le concepteur.

## <a name="to-add-an-activity-from-within-a-different-project"></a>Pour ajouter une activité à partir d'un autre projet

1.  Ouvrez une solution qui contient au moins un projet de workflow, ainsi qu'un projet de bibliothèque d'activités personnalisées ou un autre projet de workflow qui définit une activité personnalisée.

2.  Générez les deux projets. Si les builds sont réussies, une nouvelle catégorie dans le **boîte à outils** nommé «\<*nom du projet*> » avec l’activité personnalisée incluse dans cette catégorie s’affiche.

## <a name="to-add-an-activity-to-the-toolbox-from-an-assembly"></a>Pour ajouter une activité à la boîte à outils à partir d'un assembly

1.  Ouvrez une solution de workflow.

2.  À partir de la **outils** menu, sélectionnez **choisir des éléments de boîte à outils...** .

3.  Dans le **choisir des éléments de boîte à outils** boîte de dialogue, sélectionnez le **System.Activities Components** onglet, puis cliquez sur **Parcourir...**  pour accéder à l’assembly qui contient l’activité personnalisée que vous souhaitez ajouter.

4.  Sélectionnez l’assembly, puis cliquez sur **OK**. Le composant d'activité personnalisée est ajouté à la liste de composants et est automatiquement sélectionné.

    1.  Cliquez sur **OK** pour fermer la boîte de dialogue.

5.  Pour afficher la boîte à outils, sélectionnez **boîte à outils** à partir de la **vue** menu.

6.  L’activité personnalisée s’affiche dans le **boîte à outils** sous la catégorie qui avait le focus avant l’élément a été ajouté. Par exemple, si le **général** catégorie a été sélectionnée dans le **boîte à outils** avant d’ajouter l’élément de boîte à outils, l’activité apparaît sous le **général** catégorie.

## <a name="see-also"></a>Voir aussi

- [Utilisation du Concepteur de flux de travail](../workflow-designer/using-the-workflow-designer.md)