---
title: ProjectItemFile (élément) | Documents Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFile element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 67d1ed00ef4781e0419d1fceda5f95a8c0c710fb
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2018
---
# <a name="projectitemfile-element"></a>ProjectItemFile, élément
  Représente un fichier de SharePoint, comme fichier d’élément de fonctionnalité, à inclure avec l’élément de projet lorsqu’il est déployé dans SharePoint.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<ProjectItemFile Source = "Name of the file"  
    Target = "Deployment path of the file"  
    Type = "Type of deployment for the file" />  
```  
  
## <a name="type"></a>Type  
 **ProjectItemFileType**  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|**Source**|Requis **xs : String** attribut.<br /><br /> Le nom du fichier à déployer avec l’élément de projet.|  
|**Target**|Facultatif **xs : String** attribut.<br /><br /> Le chemin d’accès où le fichier sera déployé dans SharePoint, relatif au dossier racine de déploiement. Dossier racine de déploiement est déterminé par le type de déploiement spécifié par le **Type** attribut. Si le **cible** attribut n’est pas spécifié, le fichier sera déployé dans un dossier portant le nom spécifié dans le **Source** attribut.<br /><br /> Pour plus d’informations, consultez les descriptions pour le **le chemin de déploiement** et **racine du déploiement** propriétés de SharePoint dans les éléments de projet [développement de Solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Requis **xs : String** attribut.<br /><br /> Le type de déploiement pour le fichier. Pour plus d’informations sur les valeurs possibles, consultez la description de la **Type de déploiement** propriété des éléments de projet SharePoint dans [développement de Solutions SharePoint](../sharepoint/developing-sharepoint-solutions.md).|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Fichiers](../sharepoint/files-element.md)|Spécifie les fichiers à inclure avec l’élément de projet SharePoint lorsqu’elle est déployée vers SharePoint.|  
  
## <a name="remarks"></a>Notes  
 Les fichiers SharePoint généralement référencés dans **ProjectItemFile** éléments incluent des fichiers d’éléments de fonctionnalité (Elements.xml), des fichiers de schéma pour les définitions de listes (Schema.xml) et des fichiers de définition de composant WebPart des composants WebPart (.webpart).  
  
## <a name="element-information"></a>Informations sur les éléments  
  
|||  
|-|-|  
|**Espace de noms**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Nom du schéma**|Schéma d’élément de projet SharePoint|  
|**Fichier de validation**|ProjectItemModelSchema.xsd|  
|**Peut être vide.**|Non|  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur le schéma d’élément de projet SharePoint](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  