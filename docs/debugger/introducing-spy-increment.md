---
title: "Pr&#233;sentation de Spy++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Spy++"
ms.assetid: 733b514b-63a9-402d-89aa-4f0416766655
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Pr&#233;sentation de Spy++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Spy\+\+ vous permet d’effectuer les tâches suivantes :  
  
-   Afficher une arborescence graphique des relations entre les objets système. Il s’agit notamment des [processus](../debugger/processes-view.md), [threads](../debugger/threads-view.md) et [fenêtres](../debugger/windows-view.md).  
  
-   Rechercher des [fenêtres](../debugger/how-to-search-for-a-window-in-windows-view.md), [threads](../debugger/how-to-search-for-a-thread-in-threads-view.md), [processus](../debugger/how-to-search-for-a-process-in-processes-view.md), ou [messages](../Topic/How%20to:%20Search%20for%20a%20Message%20in%20Messages%20View.md) spécifiés.  
  
-   Afficher les propriétés des [fenêtres](../debugger/how-to-display-window-properties.md), [threads](../Topic/How%20to:%20Display%20Thread%20Properties.md), [processus](../debugger/how-to-display-process-properties.md) ou [messages](../debugger/how-to-display-message-properties.md) sélectionnés.  
  
-   Sélectionne une fenêtre, un thread, un processus ou un message directement dans la vue.  
  
-   Utilisez l’[Outil Recherche](../Topic/How%20to:%20Use%20the%20Finder%20Tool.md) pour sélectionner une fenêtre grâce au positionnement du pointeur de la souris.  
  
-   Définir des [options de messages](_asug_choosing_message_options) à l’aide de paramètres de sélection de journaux de messages complexes.  
  
 Spy\+\+ propose une barre d’outils et des liens hypertexte pour vous aider à travailler plus rapidement. Il offre également une commande **Actualiser** pour mettre à jour la vue active, un **Outil Recherche de fenêtres** pour simplifier l’espionnage, et une boîte de dialogue **Police** pour personnaliser les fenêtres d’affichage. En outre, Spy\+\+ vous permet d’enregistrer et de restaurer les préférences de l’utilisateur.  
  
 Dans plusieurs fenêtres Spy\+\+, vous pouvez cliquer avec le bouton droit pour afficher un menu contextuel de commandes fréquemment utilisées. Les commandes affichées dépendent de l’emplacement du pointeur. Par exemple, si vous cliquez avec le bouton droit sur une entrée dans la vue Fenêtre et que la fenêtre sélectionnée est visible, un clic sur **Surbrillance** dans le menu contextuel fait clignoter la bordure de la fenêtre sélectionnée pour que vous puissiez l’identifier facilement.  
  
> [!NOTE]
>  Il existe deux autres utilitaires qui ressemblent à Spy\+\+ : PView, qui affiche des détails sur les processus et les threads, et DDESPY. EXE, qui vous permet d’analyser les messages DDE \(Dynamic Data Exchange\).  
  
## Systèmes d’exploitation 64 bits  
 Il existe deux versions de Spy\+\+. La première, nommée Spy\+\+ \(spyxx.exe\), est conçue pour afficher les messages envoyés à une fenêtre qui s’exécute dans un processus 32 bits. Par exemple, Visual Studio s’exécute dans un processus 32 bits. Ainsi, vous pouvez utiliser Spy\+\+ pour afficher les messages envoyés à l’**Explorateur de solutions**. La configuration par défaut pour la plupart des builds dans Visual Studio consistant à s’exécuter dans un processus 32 bits, cette première version de Spy\+\+ est celle disponible dans le menu **Outils** de Visual Studio.  
  
 La deuxième version, nommée Spy\+\+ \(64 bits\) \(spyxx\_amd64.exe\), est conçue pour afficher les messages envoyés à une fenêtre qui s’exécute dans un processus 64 bits. Par exemple, sur un système d’exploitation 64 bits, le Bloc\-notes s’exécute dans un processus 64 bits. Ainsi, vous pouvez utiliser Spy\+\+ \(64 bits\) pour afficher les messages envoyés au Bloc\-notes. Spy\+\+ \(64 bits\) se trouve généralement dans  
  
 .. \\*dossier\_d’installation\_de\_Visual\_Studio*\\Common7\\Tools\\spyxx\_amd64.exe.  
  
 Vous pouvez exécuter l’une ou l’autre version de Spy\+\+ directement à partir de la ligne de commande.  
  
> [!NOTE]
>  Bien que le nom de fichier Spy\+\+ \(64 bits\) contienne « amd », il s’exécute sur n’importe quel système d’exploitation Windows x64.  
  
## Voir aussi  
 [Using Spy\+\+](../debugger/using-spy-increment.md)   
 [Spy\+\+ Views](../debugger/spy-increment-views.md)   
 [Spy\+\+ Reference](../debugger/spy-increment-reference.md)