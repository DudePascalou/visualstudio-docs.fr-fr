---
title: "JSON.parse, fonction (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "JSON.parse"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JSON.parse (méthode)"
  - "parse JSON (méthode)"
ms.assetid: 20f00d31-5ab5-4c3c-ab49-2534fc39a9b4
caps.latest.revision: 41
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 41
---
# JSON.parse, fonction (JavaScript)
Convertit une chaîne JSON \(JavaScript Object Notation\) en objet.  
  
## Syntaxe  
  
```  
JSON.parse(text [, reviver])  
```  
  
## Paramètres  
 `text`  
 Obligatoire. Chaîne JSON valide.  
  
 `reviver`  
 Facultatif. Fonction qui transforme les résultats. Cette fonction est appelée pour chaque membre de l'objet. Si un membre contient des objets imbriqués, ces derniers sont transformés avant l'objet parent. Pour chaque membre, les événements suivants se produisent :  
  
-   Si `reviver` retourne une valeur valide, la valeur membre est remplacée par la valeur transformée.  
  
-   Si `reviver` retourne la même valeur que celle qu'il a reçue, la valeur membre n'est pas modifiée.  
  
-   Si `reviver` retourne `null` ou `undefined`, le membre est supprimé.  
  
## Valeur de retour  
 Objet ou tableau.  
  
## Exceptions  
 Si cette fonction provoque une erreur d'analyse [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] \(telle que « SCRIPT1014 : caractère non valide »\), le texte d'entrée ne respecte pas la syntaxe JSON. Pour corriger l'erreur, effectuez l'une des opérations suivantes :  
  
-   Modifiez l'argument `text` afin qu'il soit conforme à la syntaxe JSON. Pour plus d'informations, consultez la page relative à la [notation de la syntaxe BNF](http://go.microsoft.com/fwlink/?LinkId=125203) des objets JSON.  
  
     Par exemple, si la réponse est au format JSONP au lieu du format JSON pur, essayez le code suivant sur l'objet de réponse :  
  
    ```javascript  
    var fixedResponse = response.responseText.replace(/\\'/g, "'");  
    var jsonObj = JSON.parse(fixedResponse);  
    ```  
  
-   Assurez\-vous que l'argument de texte `text` a été sérialisé par une implémentation conforme à JSON, telle que `JSON.stringify`.  
  
-   Exécutez l'argument `text` dans un validateur JSON tel que [JSLint](http://www.jslint.com/) pour aider à identifier les erreurs de syntaxe.  
  
## Exemple  
 L'exemple suivant utilise `JSON.parse` pour convertir une chaîne JSON en un objet.  
  
```javascript  
var jsontext = '{"firstname":"Jesper","surname":"Aaberg","phone":["555-0100","555-0120"]}';  
var contact = JSON.parse(jsontext);  
document.write(contact.surname + ", " + contact.firstname);  
document.write(contact.phone[1]);  
// Output:  
// Aaberg, Jesper  
// 555-0100  
```  
  
## Exemple  
 L'exemple suivant convertit un tableau en une chaîne JSON à l'aide de `JSON.stringify`, puis reconvertit la chaîne en un tableau à l'aide de `JSON.parse`.  
  
```javascript  
var arr = ["a", "b", "c"];  
var str = JSON.stringify(arr);  
document.write(str);  
document.write ("<br/>");  
  
var newArr = JSON.parse(str);  
  
while (newArr.length > 0) {  
    document.write(newArr.pop() + "<br/>");  
}  
  
// Output:  
// ["a","b","c"]  
// c  
// b  
// a  
```  
  
## Exemple  
 La fonction `reviver` est souvent utilisée pour transformer la représentation JSON de chaînes de date ISO \(International Organization for Standardization\) en objets `Date` au format UTC \(Coordinated Universal Time\). L'exemple suivant utilise `JSON.parse` pour désérialiser une chaîne de date au format ISO. La fonction `dateReviver` retourne des objets `Date` pour les membres qui sont mis en forme comme des chaînes de date ISO.  
  
```javascript  
var jsontext = '{ "hiredate": "2008-01-01T12:00:00Z", "birthdate": "2008-12-25T12:00:00Z" }';  
var dates = JSON.parse(jsontext, dateReviver);  
document.write(dates.birthdate.toUTCString());  
  
function dateReviver(key, value) {  
    var a;  
    if (typeof value === 'string') {  
        a = /^(\d{4})-(\d{2})-(\d{2})T(\d{2}):(\d{2}):(\d{2}(?:\.\d*)?)Z$/.exec(value);  
        if (a) {  
            return new Date(Date.UTC(+a[1], +a[2] - 1, +a[3], +a[4],  
                            +a[5], +a[6]));  
        }  
    }  
    return value;  
};  
  
// Output:  
// Thu, 25 Dec 2008 12:00:00 UTC  
  
```  
  
## Configuration requise  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)]  
  
## Voir aussi  
 [JSON.stringify, fonction](../../javascript/reference/json-stringify-function-javascript.md)   
 [toJSON, méthode \(Date\)](../../javascript/reference/tojson-method-date-javascript.md)   
 [Exemple d’application du modèle de hub \(Windows Store\)](http://code.msdn.microsoft.com/Hub-template-sample-with-4b70002d)