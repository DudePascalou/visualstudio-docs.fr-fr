---
title: Prise en charge des éditions de Visual Studio pour visualisation &amp; Modeling SDK
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 004a6b75bb66ebf3c1797abac9c1cc6f7faa6eb9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="supported-visual-studio-editions-for-visualization-amp-modeling-sdk"></a>Prise en charge des éditions de Visual Studio pour visualisation &amp; Modeling SDK
Les éléments suivants sont des listes des éditions de Visual Studio qui sont prises en charge avec [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] dans les environnements de création et le déploiement. Pour plus d’informations sur ces éditions, consultez Microsoft [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [centre de développement](http://go.microsoft.com/fwlink/?LinkId=75628).

## <a name="authoring-edition"></a>Édition de création
 Pour définir un DSL, vous devez avoir installé les composants suivants :

|||
|-|-|
|[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|
|SDK Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|
|Kit de développement logiciel (SDK) Visual Studio Visualization and Modeling|[http://go.microsoft.com/fwlink/?LinkID=186128](http://go.microsoft.com/fwlink/?LinkID=186128)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>Éditions de déploiement
 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] prend en charge les configurations suivantes pour déployer les langages spécifiques à un domaine que vous créez :

-   Visual Studio Enterprise

-   Visual Studio Professional

-   Package redistribuable Visual Studio Shell (mode intégré) redistributable package

-   Package redistribuable Visual Studio Shell (mode isolé) package redistribuable

> [!NOTE]
>  Pour rendre une DSL puissent s’exécuter sur un produit de l’interpréteur de commandes, vous devez affecter la **pris en charge une édition de Visual Studio** champ dans le manifeste d’Extension. Pour plus d’informations, consultez [déploiement de Solutions de langage spécifique à un domaine](../modeling/deploying-domain-specific-language-solutions.md).

## <a name="see-also"></a>Voir aussi

- [Glossaire des outils de langage spécifique à un domaine](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
