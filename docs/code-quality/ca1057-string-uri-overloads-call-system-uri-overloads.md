---
title: "CA1057 : Les surcharges d'uri de chaîne appellent les surcharges de System.Uri"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1057
- StringUriOverloadsCallSystemUriOverloads
helpviewer_keywords:
- StringUriOverloadsCallSystemUriOverloads
- CA1057
ms.assetid: ef1e983e-9ca7-404b-82d7-65740ba0ce20
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 63386e73cee4d2e0c1c34f31f0042312fef4869f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1057-string-uri-overloads-call-systemuri-overloads"></a>CA1057 : Les surcharges d'uri de chaîne appellent les surcharges de System.Uri
|||
|-|-|
|TypeName|StringUriOverloadsCallSystemUriOverloads|
|CheckId|CA1057|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type déclare des surcharges de méthode qui diffèrent uniquement par le remplacement d’un paramètre de chaîne avec un <xref:System.Uri?displayProperty=fullName> paramètre et la surcharge qui accepte le paramètre de chaîne n’appelle pas la surcharge qui accepte le <xref:System.Uri> paramètre.

## <a name="rule-description"></a>Description de la règle
 Étant donné que les surcharges diffèrent uniquement par la chaîne /<xref:System.Uri> paramètre, la chaîne est censée pour représenter un identificateur de ressource uniforme (URI). Une représentation sous forme de chaîne d'un URI est sujette aux erreurs d'analyse et d'encodage, et peut entraîner des failles de sécurité. La <xref:System.Uri> classe fournit ces services de manière sûre et sécurisée. Pour profiter des avantages de la <xref:System.Uri> (classe), la surcharge de chaîne doit appeler la <xref:System.Uri> à l’aide de l’argument de chaîne de surcharge.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Ré-implémenter la méthode qui utilise la représentation sous forme de chaîne de l’URI, afin qu’il crée une instance de la <xref:System.Uri> à l’aide de l’argument de chaîne de la classe, puis passe le <xref:System.Uri> objet à la surcharge qui a le <xref:System.Uri> paramètre.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si le paramètre de chaîne ne représente pas un URI.

## <a name="example"></a>Exemple
 L’exemple suivant montre une surcharge string correctement implémentée.

 [!code-csharp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CSharp/ca1057-string-uri-overloads-call-system-uri-overloads_1.cs)]
 [!code-cpp[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/CPP/ca1057-string-uri-overloads-call-system-uri-overloads_1.cpp)]
 [!code-vb[FxCop.Design.CallUriOverload#1](../code-quality/codesnippet/VisualBasic/ca1057-string-uri-overloads-call-system-uri-overloads_1.vb)]

## <a name="related-rules"></a>Règles associées
 [CA2234 : Passez des objets System.Uri au lieu de chaînes](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)

 [CA1056 : Les propriétés d’URI ne doivent pas être des chaînes](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054 : Les paramètres d’URI ne doivent pas être des chaînes](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055 : Les valeurs de retour d’URI ne doivent pas être des chaînes](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)