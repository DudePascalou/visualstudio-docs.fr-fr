---
title: Extraire une méthode dans Visual Studio
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: b4b5a818a75399fc4ce29fb7f2bec6332dac0585
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="extract-a-method-refactoring"></a>Extraire une méthode (refactorisation)

Cette refactorisation s’applique à :

- C#

- Visual Basic

**Quoi :** vous permet de transformer un fragment de code dans sa propre méthode.

**Quand :** vous avez un fragment de code existant dans une méthode qui doit être appelée à partir d’une autre méthode.

**Pourquoi :** vous pouvez copier/coller ce code, mais cela entraîne une duplication. Une meilleure solution consiste à refactoriser ce fragment dans sa propre méthode pouvant être appelée librement par toute autre méthode.

## <a name="how-to"></a>Procédure

1. Mettez en surbrillance le code à extraire :

   - C# :

    ![Code mis en surbrillance (C#)](media/extractmethod-highlight-cs.png)

   - Visual Basic :

    ![Code mis en surbrillance (Visual Basic)](media/extractmethod-highlight-vb.png)

1. Effectuez ensuite l'une des opérations suivantes :

   - **Clavier**
     - Appuyez sur **Ctrl+R**, puis **Ctrl+M**. (Notez que le raccourci clavier peut varier en fonction du profil que vous avez sélectionné.)
     - Appuyez sur **Ctrl**+**.** pour afficher le menu **Actions rapides et refactorisations**, puis sélectionnez **Extraire la méthode** dans la fenêtre contextuelle d’aperçu.
   - **Souris**
     - Sélectionnez **Modifier > Refactoriser > Extraire la méthode**.
     - Cliquez avec le bouton droit sur le code, puis sélectionnez **Refactoriser > Extraire > Extraire la méthode**.
     - Cliquez avec le bouton droit sur le code et choisissez le menu **Actions rapides et refactorisations**, puis sélectionnez **Extraire la méthode** dans la fenêtre contextuelle d’aperçu.

   La méthode sera immédiatement créée. À partir d’ici, il vous suffit de taper le nouveau nom de la méthode pour la renommer.

   > [!TIP]
   > Vous pouvez également mettre à jour les commentaires et autres chaînes afin d’utiliser ce nouveau nom, et [afficher un aperçu des modifications](../../ide/preview-changes.md) avant de les enregistrer, à l’aide des cases à cocher de la boîte de dialogue **Renommer** qui apparaît en haut à droite de votre IDE.

   - C# :

    ![Renommer la méthode (C#)](media/extractmethod-rename-cs.png)

   - Visual Basic :

    ![Renommer la méthode (Visual Basic)](media/extractmethod-rename-vb.png)

1. Quand vous êtes satisfait du changement, appuyez sur le bouton **Appliquer** ou sur la touche **Entrée** pour valider les changements.

## <a name="see-also"></a>Voir aussi

- [Refactorisation](../refactoring-in-visual-studio.md)
- [Aperçu des modifications](../../ide/preview-changes.md)