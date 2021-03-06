---
title: Sélectionner un paramètre d’exécution pour un test de charge dans Visual Studio | Microsoft Docs
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, run settings, active
ms.assetid: ed6ff546-acfa-4dd8-b3a2-6e7455930ca4
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: dc521cf8e0218fabd691493fdb65fb46471e05bd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-select-the-active-run-setting-for-a-load-test"></a>Comment : sélectionner le paramètre d'exécution active d'un test de charge

Après avoir créé votre test de charge avec l’**Assistant Nouveau test de charge**, vous pouvez utiliser l’**éditeur de test de charge** pour changer les propriétés des scénarios en fonction de vos besoins et objectifs.

Un test de charge peut contenir un ou plusieurs *paramètres d’exécution*, c’est-à-dire un ensemble de propriétés qui influencent la manière dont un test de charge est exécuté. Les paramètres d'exécution sont classés par catégories dans la fenêtre Propriétés. Lorsqu'un test de charge est exécuté, il utilise le paramètre d'exécution actuellement actif.

> [!NOTE]
> Pour obtenir une liste complète des propriétés des paramètres d’exécution et leurs descriptions, consultez [Propriétés des paramètres d’exécution pour le test de charge](../test/load-test-run-settings-properties.md).

Si votre test de charge contient un seul nœud de paramètre d’exécution sous le dossier **Paramètres d’exécution**, ce nœud est toujours le nœud actif. Si votre test de charge contient plusieurs nœuds Paramètres d'exécution, vous pouvez sélectionner celui à utiliser lors de l'exécution d'un test de charge. Consultez [Guide pratique pour ajouter des paramètres d’exécution supplémentaires à un test de charge](../test/how-to-add-additional-run-settings-to-a-load-test.md).

Dans l'Éditeur de test de charge, le paramètre d'exécution actif est identifié par le suffixe « [Actif] ».

## <a name="selecting-the-active-run-setting"></a>Sélection du paramètre d'exécution actif

### <a name="to-select-the-active-run-setting-in-a-load-test"></a>Pour sélectionner le paramètre d'exécution actif dans un test de charge

1.  Ouvrez un test de charge.

2.  Développez le dossier **Paramètres d’exécution**.

3.  Cliquez avec le bouton droit sur le nœud des paramètres d’exécution à définir en tant que nœud actif, puis choisissez **Définir comme actif**.

     Dans l’**éditeur de test de charge**, le nœud de paramètres d’exécution affecté est mis à jour avec le suffixe « [Actif] ».

     Le paramètre d'exécution sélectionné devient actif et le reste jusqu'à ce que vous sélectionniez un autre paramètre d'exécution pour le remplacer.

> [!NOTE]
>  Vous pouvez substituer le paramètre d'exécution actif en définissant une variable d'environnement nommée `Test.UseRunSetting=<run setting name>`. Cela est utile lorsque vous exécutez un test de charge à partir de la ligne de commande ou d'un fichier batch. Vous pouvez ainsi choisir des paramètres d'exécution différents sans ouvrir votre test de charge.

## <a name="specifying-the-run-setting-to-use-from-the-command-line"></a>Spécification du paramètre d'exécution à utiliser à partir de la ligne de commande
 Vous pouvez remplacer les paramètres d'exécution par défaut dans votre test de charge en définissant une variable d'environnement à partir de la ligne de commande :

 **Définissez Test.UseRunSetting=PreProdEnvironment**

 Ensuite, exécutez le test :

 **mstest /testcontainer:loadtest1.loadtest**

## <a name="see-also"></a>Voir aussi

- [Configuration des paramètres d’exécution des tests de charge](../test/configure-load-test-run-settings.md)
- [Spécification des ensembles de compteurs et des règles de seuil pour les ordinateurs dans un test de charge](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Guide pratique pour ajouter des paramètres d’exécution supplémentaires à un test de charge](../test/how-to-add-additional-run-settings-to-a-load-test.md)