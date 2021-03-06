---
title: Barre d’outils Spy ++ | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Spy++ toolbar
ms.assetid: 949c18fb-bb25-42ed-9130-c4a47869f24d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f90c9f249ea0091d7cd5b899ffcd9b7cdadc5a7c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="spy-toolbar"></a>Barre d'outils Spy++
La barre d’outils s’affiche sous la barre de menus dans Spy ++. Pour afficher ou masquer la barre d’outils, sur le **vue** menu, cliquez sur **barre d’outils**.  
  
 Les contrôles suivants sont disponibles sur la barre d’outils.  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
  
|Bouton|Effet|  
|------------|------------|  
|![Spy&#43; &#43; bouton Windows](../debugger/media/icon_spy--_windows.gif "Icon_Spy ++ _Windows")|Affiche une arborescence des fenêtres et des contrôles dans le système. Pour plus d’informations, consultez [affichage Windows](../debugger/windows-view.md).|  
|![Spy&#43; &#43; traite bouton](../debugger/media/icon_spy--_processes.gif "Icon_Spy ++ _Processes")|Affiche une arborescence des processus du système. Pour plus d’informations, consultez [vue processus](../debugger/processes-view.md).|  
|![Spy&#43; &#43; Threads bouton](../debugger/media/icon_spy--_threads.gif "Icon_Spy ++ _Threads")|Affiche une arborescence des threads dans le système. Pour plus d’informations, consultez [vue Threads](../debugger/threads-view.md).|  
|![Spy&#43; &#43; Messages bouton](../debugger/media/icon_spy--_messages.gif "Icon_Spy ++ _Messages")|Crée une fenêtre pour afficher les messages de fenêtre et ouvre le **Options des messages** afin que vous puissiez sélectionner la fenêtre dont les messages seront affichés et sélectionner d’autres options de boîte de dialogue. Pour plus d’informations, consultez [vue Messages](../debugger/messages-view.md).|  
|![Spy&#43; &#43; bouton Démarrer le journal](../debugger/media/icon_spy--_startlog.gif "Icon_Spy ++ _StartLog")|Démarre la journalisation des messages et affiche le flux de message. Ce contrôle n’est disponible uniquement lorsqu’un **Messages** fenêtre est la fenêtre active. Pour plus d’informations, consultez [Comment : Démarrer et arrêter l’affichage du journal des messages](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Spy&#43; &#43; journal bouton Arrêter](../debugger/media/icon_spy--_stoplog.gif "Icon_Spy ++ _StopLog")|Journalisation et l’affichage du flux de messages des messages s’arrête. Ce contrôle n’est disponible uniquement lorsqu’un **Messages** fenêtre est la fenêtre active. Pour plus d’informations, consultez [Comment : Démarrer et arrêter l’affichage du journal des messages](../debugger/how-to-start-and-stop-the-message-log-display.md).|  
|![Spy&#43; &#43; connecter bouton Options](../debugger/media/icon_spy--_logoptions.gif "Icon_Spy ++ _LogOptions")|Affiche la [Options des messages](../debugger/message-options-dialog-box.md) boîte de dialogue. Utilisez cette boîte de dialogue pour sélectionner windows et de types pour l’affichage de messages. Ce contrôle n’est disponible uniquement lorsqu’un **Messages** fenêtre est la fenêtre active.|  
|![Spy&#43; &#43; journal bouton Effacer](../debugger/media/spy--_clearlog.gif "Spy ++ _ClearLog")|Efface le contenu de l’actif **Messages** fenêtre. Ce contrôle n’est disponible uniquement lorsqu’un **Messages** fenêtre est la fenêtre active.|  
|![Spy&#43; &#43; bouton de la fenêtre Rechercher](../debugger/media/icon_spy--_findwindow.gif "Icon_Spy ++ _FindWindow")|Ouvre le [rechercher une fenêtre](../debugger/find-window-dialog-box.md) boîte de dialogue qui vous permet de définir des critères de recherche de fenêtre et afficher les propriétés ou les messages. Pour plus d’informations, consultez [Comment : utiliser l’outil recherche](../debugger/how-to-use-the-finder-tool.md).|  
|![Spy&#43; &#43; rechercher le premier bouton de fenêtre](../debugger/media/icon_spy--_window.gif "Icon_Spy ++ _Window")|Recherche dans la vue actuelle pour une correspondance de la fenêtre, le processus, le thread ou le message.|  
|![Spy&#43; &#43; bouton de fenêtre suivant](../debugger/media/icon_spy--_nextwindow.gif "Icon_Spy ++ _NextWindow")|Recherche dans l’affichage actuel la fenêtre correspondante suivante, le processus, le thread ou le message. Ce contrôle (et la commande de menu connexe) sont disponibles uniquement s’il existe un résultat de recherche valide qui n’est pas unique. Par exemple, lorsque vous utilisez un handle de fenêtre comme critère de recherche dans l’arborescence de la fenêtre, il produit les résultats uniques étant donné qu’une seule fenêtre dans l’arborescence de la fenêtre qui a ce handle ; Dans ce cas, **suivant** n’est pas disponible.|  
|![Spy&#43; &#43; trouver le bouton de fenêtre précédent](../debugger/media/icon_spy--_prevwindow.gif "Icon_Spy ++ _PrevWindow")|Recherche dans l’affichage actuel la fenêtre correspondante précédente, le processus, le thread ou le message. Ce contrôle (et la commande de menu connexe) sont disponibles uniquement s’il existe un résultat de recherche valide qui n’est pas unique. Par exemple, lorsque vous utilisez un handle de fenêtre comme critère de recherche dans l’arborescence de la fenêtre, il produit les résultats uniques étant donné qu’une seule fenêtre dans l’arborescence de la fenêtre qui a ce handle ; Dans ce cas, **précédent** n’est pas disponible.|  
|![Spy&#43; &#43; bouton Explorateur des propriétés](../debugger/media/icon_spy--_propexp.gif "Icon_Spy ++ _PropExp")|Affiche les propriétés de la fenêtre qui est sélectionné dans l’affichage de Windows.|  
|![Spy&#43; &#43; bouton Actualiser](../debugger/media/icon_spy--_refresh.gif "Icon_Spy ++ _Refresh")|Actualise les vues système.|  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de Spy ++](../debugger/using-spy-increment.md)   
 [Vues Spy ++](../debugger/spy-increment-views.md)   
 [Informations de référence sur Spy++](../debugger/spy-increment-reference.md)