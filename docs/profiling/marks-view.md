---
title: Marques, vue | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.marks
helpviewer_keywords:
- profiling tools, Marks view
- profiling tools reports, Marks view
ms.assetid: b2773344-8081-4116-85a1-58f770448f6a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1008f09e7511a26613b6cb5984513c1d049f61ba
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="marks-view"></a>Marques, vue
La vue Marques affiche l’échantillonnage et les événements ETW qui ont été insérés dans l’application.  
  
 Les marques par défaut qui sont préremplies dans le rapport indiquent le démarrage du programme et la fin du programme.  
  
 Les données des compteurs Windows provenant de marques générées automatiquement sont également présentées dans cette vue. Pour plus d’informations, consultez [Guide pratique pour collecter les données des compteurs Windows](../profiling/how-to-collect-windows-counter-data.md).  
  
 Pour créer un filtre entre deux marques, sélectionnez les marques, cliquez avec le bouton droit puis cliquez sur **Ajouter un filtre par marques** ou **Ajouter un filtre par horodatage**.  
  
 Le tableau suivant contient les définitions des colonnes qui sont disponibles dans la vue Marques.  
  
 **ID de marque**  
 Identificateur unique de la marque de profilage.  
  
 **Nom de la marque**  
 Nom de l'événement.  
  
 **Horodatage**  
 Durée entre l’heure du début du profilage et l’heure à laquelle l’événement est enregistré.  
  
 Données des compteurs de performances Windows  
 Quand des données de compteurs de performances Windows sont collectées, les valeurs sont affichées dans une colonne portant le même nom que le compteur.  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du rapport Performances](../profiling/performance-report-overview.md)   
 [Guide pratique pour collecter les données des compteurs Windows](../profiling/how-to-collect-windows-counter-data.md)   
 [&#91;NIB&#93; Fenêtre de contrôle de la collecte de données](http://msdn.microsoft.com/en-us/98d740d8-459f-4605-bf04-fb17aafaaa8f)