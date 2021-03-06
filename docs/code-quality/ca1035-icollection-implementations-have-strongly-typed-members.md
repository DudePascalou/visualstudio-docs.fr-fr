---
title: 'CA1035 : Les implémentations ICollection possèdent des membres fortement typés'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ICollectionImplementationsHaveStronglyTypedMembers
- CA1035
helpviewer_keywords:
- CA1035
- ICollectionImplementationsHaveStronglyTypedMembers
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f9cda0790128bb279d30a15f75080c375ec68aa1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035 : Les implémentations ICollection possèdent des membres fortement typés
|||
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type public ou protégé implémente <xref:System.Collections.ICollection?displayProperty=fullName> mais ne fournit ne pas de méthode fortement typée pour <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>. La version fortement typée de <xref:System.Collections.ICollection.CopyTo%2A> doit accepter deux paramètres et ne peut pas avoir un <xref:System.Array?displayProperty=fullName> ou un tableau de <xref:System.Object?displayProperty=fullName> comme premier paramètre.

## <a name="rule-description"></a>Description de la règle
 Cette règle requiert <xref:System.Collections.ICollection> fournir fortement les implémentations des membres typés afin que les utilisateurs ne doivent pas effectuer un cast d’arguments à la <xref:System.Object> lorsqu’ils utilisent les fonctionnalités fournies par l’interface de type. Cette règle suppose que le type qui implémente <xref:System.Collections.ICollection> a par conséquent, pour gérer une collection d’instances d’un type plus fort que <xref:System.Object>.

 <xref:System.Collections.ICollection> implémente l'interface <xref:System.Collections.IEnumerable?displayProperty=fullName>. Si les objets dans la collection étendent <xref:System.ValueType?displayProperty=fullName>, vous devez fournir un membre fortement typé pour <xref:System.Collections.IEnumerable.GetEnumerator%2A> afin d’éviter la baisse de performances est provoquée par le boxing. Cela n’est pas nécessaire lorsque les objets de la collection sont un type référence.

 Pour implémenter une version fortement typée d’un membre d’interface, implémentez les membres d’interface explicitement à l’aide de noms sous la forme `InterfaceName.InterfaceMemberName`, tel que <xref:System.Collections.ICollection.CopyTo%2A>. Les membres d’interface explicites utilisent les types de données qui sont déclarés par l’interface. Implémenter des membres fortement typés à l’aide du nom de membre d’interface, tel que <xref:System.Collections.ICollection.CopyTo%2A>. Déclarer des membres fortement typés comme publics et déclarer des paramètres et retournent des valeurs de type fort géré par la collection. Les types forts remplacent les types plus faibles telles que <xref:System.Object> et <xref:System.Array> qui sont déclarés par l’interface.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, implémentez le membre d’interface explicitement (déclarez-le en tant que <xref:System.Collections.ICollection.CopyTo%2A>). Ajouter le membre fortement typé public, déclaré comme `CopyTo`, et qu’il procède à un tableau fortement typé en tant que premier paramètre.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimer un avertissement de cette règle si vous implémentez une nouvelle collection orientée objet, par exemple un arbre binaire, où des types qui étendent la nouvelle collection déterminent le type fort. Ces types doivent être compatible avec cette règle et exposer des membres fortement typés.

## <a name="example"></a>Exemple
 L’exemple suivant illustre la façon correcte d’implémenter <xref:System.Collections.ICollection>.

 [!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]

## <a name="related-rules"></a>Règles associées
 [CA1038 : Les énumérateurs doivent être fortement typés](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

 [CA1039 : Les listes sont fortement typées](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Voir aussi
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.IEnumerable?displayProperty=fullName> <xref:System.Collections.ICollection?displayProperty=fullName> <xref:System.Object?displayProperty=fullName>