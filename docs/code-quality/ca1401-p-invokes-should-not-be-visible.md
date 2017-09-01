---
title: 'CA1401: P-Invokes should not be visible | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PInvokesShouldNotBeVisible
- CA1401
helpviewer_keywords:
- CA1401
- PInvokesShouldNotBeVisible
ms.assetid: 0f4d96c1-f9de-414e-b223-4dc7f691bee3
caps.latest.revision: 17
author: stevehoag
ms.author: shoag
manager: wpickett
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 5a1cbda877a8472860b3dfcb3dad80eae91eaa49
ms.contentlocale: fr-fr
ms.lasthandoff: 08/30/2017

---
# <a name="ca1401-pinvokes-should-not-be-visible"></a>CA1401: P/Invokes should not be visible
|||  
|-|-|  
|TypeName|PInvokesShouldNotBeVisible|  
|CheckId|CA1401|  
|Category|Microsoft.Interoperability|  
|Breaking Change|Breaking|  
  
## <a name="cause"></a>Cause  
 A public or protected method in a public type has the <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> attribute (also implemented by the `Declare` keyword in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).  
  
## <a name="rule-description"></a>Rule Description  
 Methods that are marked with the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute (or methods that are defined by using the `Declare` keyword in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) use Platform Invocation Services to access unmanaged code. Such methods should not be exposed. By keeping these methods private or internal, you make sure that your library cannot be used to breach security by allowing callers access to unmanaged APIs that they could not call otherwise.  
  
## <a name="how-to-fix-violations"></a>How to Fix Violations  
 To fix a violation of this rule, change the access level of the method.  
  
## <a name="when-to-suppress-warnings"></a>When to Suppress Warnings  
 Do not suppress a warning from this rule.  
  
## <a name="example"></a>Example  
 The following example declares a method that violates this rule.  
  
 [!code-vb[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/VisualBasic/ca1401-p-invokes-should-not-be-visible_1.vb)] [!code-csharp[FxCop.Interoperability.DllImports#1](../code-quality/codesnippet/CSharp/ca1401-p-invokes-should-not-be-visible_1.cs)]