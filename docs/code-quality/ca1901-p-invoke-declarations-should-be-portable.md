---
title: 'CA1901 : Les déclarations P-Invoke doivent être portables'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed9821d9b80309311a6fd108c4a29f52b2e882bf
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901 : Les déclarations P/Invoke doivent être portables
|||
|-|-|
|TypeName|PInvokeDeclarationsShouldBePortable|
|CheckId|CA1901|
|Category|Microsoft.Portability|
|Modification avec rupture|Avec rupture - Si P/Invoke est visible en dehors de l’assembly. Sans rupture - Si P/Invoke n’est pas visible à l’extérieur de l’assembly.|

## <a name="cause"></a>Cause
 Cette règle évalue la taille de chaque paramètre et la valeur de retour d’un P/Invoke et vérifie que leur taille, lorsqu’elle est marshalée au code non managé sur les plateformes 32 bits et 64 bits, est correcte. La violation la plus courante de cette règle consiste à passer à un entier de taille fixe d’où une variable dépendante de la plateforme, la taille du pointeur est requise.

## <a name="rule-description"></a>Description de la règle
 Un des scénarios suivants viole cette règle se produit :

-   La valeur de retour ou paramètre est typé comme un entier de taille fixe lorsqu’il doit être tapé comme un `IntPtr`.

-   La valeur de retour ou paramètre de type est un `IntPtr` quand il doit être tapé comme un entier de taille fixe.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Vous pouvez résoudre cette violation à l’aide de `IntPtr` ou `UIntPtr` pour représenter des handles au lieu de `Int32` ou `UInt32`.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Vous ne devez pas supprimer cet avertissement.

## <a name="example"></a>Exemple
 L’exemple suivant montre une violation de cette règle.

```csharp
internal class NativeMethods
{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, IntPtr nIconIndex);
}
```

 Dans cet exemple, le `nIconIndex` le paramètre est déclaré comme un `IntPtr`, qui est de 4 octets sur une plateforme 32 bits et 8 octets sur une plateforme 64 bits. Dans la déclaration non managée qui suit, vous pouvez voir que `nIconIndex` est un entier non signé de 4 octets sur toutes les plateformes.

```csharp
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,
    UINT nIconIndex);
```

## <a name="example"></a>Exemple
 Pour corriger la violation, modifiez la déclaration comme suit :

```csharp
internal class NativeMethods{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)] 
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, uint nIconIndex);
}
```

## <a name="see-also"></a>Voir aussi
 [Portability Warnings](../code-quality/portability-warnings.md)