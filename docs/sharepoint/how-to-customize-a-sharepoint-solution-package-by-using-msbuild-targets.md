---
title: 'Comment : personnaliser un Package de Solution SharePoint à l’aide de cibles de MSBuild | Documents Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 90358624f5de8fc7c90e3424f04617acab4388a4
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
---
# <a name="how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets"></a>Comment : personnaliser un package de solution SharePoint à l'aide de cibles de MSBuild
  À l’aide de cibles de MSBuild à une invite de commandes, vous pouvez personnaliser la façon dont Visual Studio crée les fichiers de package SharePoint (.wsp). Par exemple, vous pouvez personnaliser les propriétés MSBuild pour modifier le répertoire intermédiaire d’empaquetage et les groupes d’éléments MSBuild qui spécifient les fichiers énumérés.  
  
## <a name="customizing-and-running-msbuild-targets"></a>Personnalisation et exécution des cibles de MSBuild  
 Si vous personnalisez les cibles BeforeLayout et AfterLayout, vous pouvez effectuer des tâches avant la mise en page du package, telles que l’ajout, la suppression ou la modification des fichiers sont empaquetés.  
  
#### <a name="to-customize-the-beforelayout-target"></a>Pour personnaliser la cible BeforeLayout  
  
1.  Ouvrez un éditeur, tel que le bloc-notes et puis ajoutez le code suivant.  
  
    ```xml  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <Target Name="BeforeLayout">  
        <Message Importance="high" Text="In the BeforeLayout Target"></Message>  
      </Target>  
    </Project>  
    ```  
  
     Cet exemple affiche un message avant la création de package de cette cible.  
  
2.  Nommez le fichier **CustomLayout.SharePoint.targets**, puis enregistrez-le dans le dossier du projet SharePoint.  
  
3.  Ouvrez le projet, ouvrez le menu contextuel, puis choisissez **décharger le projet**.  
  
4.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel du projet, puis choisissez **modifier***nom_projet***.vbproj** ou **modifier***nom_projet*** .csproj**.  
  
5.  Après le `Import` ligne vers la fin du fichier projet, ajoutez la ligne suivante.  
  
    ```xml  
    <Import Project="CustomLayout.SharePoint.targets" />  
    ```  
  
6.  Enregistrez et fermez le fichier de projet.  
  
7.  Dans **l’Explorateur de solutions**, ouvrez le menu contextuel du projet, puis choisissez **recharger le projet**.  
  
 Lorsque vous publiez le projet, le message s’affiche dans la sortie avant le début de l’empaquetage.  
  
#### <a name="to-customize-the-afterlayout-target"></a>Pour personnaliser la cible AfterLayout  
  
1.  Dans la barre de menus, choisissez **fichier**, **ouvrir**, **fichier**.  
  
2.  Dans le **ouvrir le fichier** boîte de dialogue, accédez au dossier du projet, choisissez le fichier CustomLayout.target, puis choisissez le **ouvrir** bouton.  
  
3.  Juste avant la `</Project>` , ajoutez le code suivant :  
  
    ```xml  
    <Target Name="AfterLayout">  
      <Message Importance="high" Text="In the AfterLayout Target"></Message>  
    </Target>  
    ```  
  
     Cet exemple affiche un message une fois que cette cible est empaquetée.  
  
4.  Enregistrez et fermez le fichier de cibles.  
  
5.  Redémarrez Visual Studio et ouvrez le projet.  
  
 Lorsque vous publiez le projet, le message BeforeLayout apparaît avant le début de l’empaquetage et le message AfterLayout s’affiche à l’issue de l’exécution d’empaquetage.  
  
## <a name="see-also"></a>Voir aussi  
 [Empaquetage et déploiement de solutions SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  