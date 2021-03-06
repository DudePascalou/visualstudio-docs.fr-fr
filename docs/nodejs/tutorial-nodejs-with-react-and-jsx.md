---
title: Créer une application Node.js et React - Visual Studio | Microsoft Docs
description: Dans ce tutoriel, vous créez une application Node.js et React dans Visual Studio
ms.custom: mvc
ms.date: 02/19/2018
ms.technology: vs-nodejs
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 21debd24f69b79cb2dbbf9e9ceea928ac9dd851e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="tutorial-create-a-nodejs-and-react-app-in-visual-studio"></a>Tutoriel : Créer une application Node.js et React dans Visual Studio
Visual Studio vous permet de créer facilement un projet Node.js et de tirer parti d’IntelliSense et d’autres fonctionnalités intégrées prenant en charge Node.js. Dans ce tutoriel pour Visual Studio, vous créez un projet d’application web Node.js à partir d’un modèle Visual Studio. Vous créez ensuite une application simple avec React.

Dans ce didacticiel, vous apprendrez à :
> [!div class="checklist"]
> * Créer un projet Node.js
> * Ajouter des packages npm
> * Ajouter du code React à votre application
> * Transpiler du code JSX
> * Attacher le débogueur

## <a name="prerequisites"></a>Prérequis

* Au préalable, vous devez avoir installé Visual Studio et la charge de travail de développement Node.js.

    Si vous n’avez pas encore installé Visual Studio, installez-le gratuitement [ici](http://www.visualstudio.com).

    Si vous devez installer la charge de travail mais que vous avez déjà Visual Studio, cliquez sur le lien **Ouvrir Visual Studio Installer** dans le volet gauche de la boîte de dialogue **Nouveau projet**. Visual Studio Installer est lancé. Choisissez la charge de travail **Développement Node.js**, puis choisissez **Modifier**.

* Le runtime Node.js doit être installé.

    Si vous ne l’avez pas déjà fait, installez la version LTS à partir du site web [Node.js](https://nodejs.org/en/download/). En règle générale, Visual Studio détecte automatiquement le runtime Node.js installé. S’il ne détecte aucun runtime installé, vous pouvez configurer votre projet pour référencer le runtime installé dans la page de propriétés (après avoir créé un projet, cliquez avec le bouton droit sur le nœud de projet, puis choisissez **Propriétés**).

    Ce tutoriel a été testé avec la version 8.9.4.

## <a name="create-a-project"></a>Créer un projet
Commencez par créer un projet d’application web Node.js.

1. Ouvrez Visual Studio 2017.

1. Dans la barre de menus supérieure, choisissez **Fichier** > **Nouveau** > **Projet...**.

1. Dans la boîte de dialogue **Nouveau projet**, dans le volet gauche, développez **JavaScript**, puis choisissez **Node.js**. Dans le volet central, choisissez **Application web Node.js vide**, tapez le nom **NodejsWebAppBlank**, puis choisissez **OK**.

     Si vous ne voyez pas le modèle de projet **Application web Node.js vide**, vous devez d’abord installer la charge de travail Développement Node.js.

    Visual Studio crée la solution et ouvre votre projet.

    ![Projet Node.js dans l’Explorateur de solutions](../nodejs/media/tutorial-nodejs-react-project-structure.png)

    - Votre projet mis en gras, avec le nom que vous avez donné dans la boîte de dialogue **Nouveau projet**. Dans le système de fichiers, ce projet est représenté par un fichier *.njsproj* au sein de votre dossier de projet. Vous pouvez définir les propriétés et les variables d’environnement associées au projet en cliquant avec le bouton droit sur le projet et en choisissant **Propriétés**. Vous pouvez effectuer des allers-retours avec d’autres outils de développement, car le fichier projet n’apporte pas de changements personnalisés à la source de projet Node.js.

    - Au niveau le plus élevé figure une solution, qui a par défaut le même nom que votre projet. Une solution, représentée par un fichier *.sln* sur le disque, est un conteneur pour un ou plusieurs projets connexes.

    - Le nœud npm montre tous les packages npm installés. Vous pouvez cliquer avec le bouton droit sur le nœud npm pour rechercher et installer des packages npm à l’aide d’une boîte de dialogue.

    - Les fichiers projet tels que *server.js* s’affichent sous le nœud de projet. *server.js* est le fichier de démarrage du projet.

## <a name="add-npm-packages"></a>Ajouter des packages npm

Cette application nécessite un certain nombre de modules npm pour s’exécuter correctement.

* react
* react-dom
* express
* path
* ts-loader
* typescript
* webpack
* webpack-cli

1. Dans l’Explorateur de solutions (volet droit), cliquez avec le bouton droit sur le nœud **npm** du projet, puis choisissez **Installer de nouveaux packages npm**.

    Dans la boîte de dialogue **Installer de nouveaux packages npm**, vous pouvez choisir d’installer la version de package la plus récente ou une version spécifique. Si vous choisissez d’installer la version actuelle de ces packages, mais que vous rencontrez plus tard des erreurs inattendues, vous devrez peut-être installer les mêmes versions de package que celles décrites plus loin au cours de ces étapes.

1. Dans la boîte de dialogue **Installer de nouveaux packages npm**, recherchez le package react, puis cliquez sur **Installer le package** pour installer ce dernier.

    ![Installer des packages npm](../nodejs/media/tutorial-nodejs-react-install-packages.png)

    La fenêtre **Sortie** indique la progression de l’installation du package. Une fois installé, le package apparaît sous le nœud **npm**.

    Le fichier *package.json* du projet est mis à jour à l’aide des informations relatives au nouveau package, notamment sa version.

1. Au lieu d’utiliser l’IU pour rechercher et ajouter les packages restants, un par un, collez le code suivant dans le fichier package.json. Remplacez la section `dependencies` par ce code :

    ```js
    "dependencies": {
      "express": "4.16.2",
      "path": "0.12.7",
      "react": "16.2.0",
      "react-dom": "16.2.0",
      "ts-loader": "4.0.1",
      "typescript": "2.7.2",
      "webpack": "4.1.1",
      "webpack-cli": "2.0.11"
    }
    ```

1. Cliquez avec le bouton droit sur le nœud **npm** de votre projet, puis choisissez **Installer les packages npm manquants**.

    La fenêtre **Sortie** indique la progression de l’installation des packages.

    Voici les modules npm tels qu’ils apparaissent dans l’Explorateur de solutions après leur installation.

    ![packages npm](../nodejs/media/tutorial-nodejs-react-npm-modules.png)

    > [!NOTE]
    > Si vous préférez installer les packages npm à l’aide de la ligne de commande, cliquez avec le bouton droit sur le nœud de projet, puis choisissez **Ouvrir l’invite de commandes ici**. Utilisez les commandes Node.js standard pour installer les packages.

## <a name="add-project-files"></a>Ajouter des fichiers projet

Au cours de ces étapes, vous devez ajouter quatre nouveaux fichiers à votre projet.

* *app.tsx*
* *webpack-config.js*
* *index.html*
* *tsconfig.json*

Pour cette application simple, vous ajoutez les nouveaux fichiers projet à la racine du projet. (Dans la plupart des applications, vous ajoutez généralement les fichiers aux sous-dossiers, et vous changez ensuite les références de chemin relatives correspondantes.)

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet **NodejsWebAppBlank**, puis choisissez **Ajouter** > **Nouvel élément**.

1. Dans la boîte de dialogue **Ajouter un nouvel élément**, choisissez **Fichier TypeScript JSX**, tapez le nom *app.tsx*, puis cliquez sur **OK**.

1. Répétez ces étapes pour ajouter *webpack-config.js*.

1. Répétez les mêmes étapes pour ajouter *index.html* au projet. Au lieu d’un fichier JavaScript, choisissez **Fichier HTML**.

1. Répétez les mêmes étapes pour ajouter *tsconfig.json* au projet. Au lieu d’un fichier JavaScript, choisissez **Fichier config JSON TypeScript**.

## <a name="add-app-code"></a>Ajouter du code d’application

1. Ouvrez *server.js* et remplacez le code par le code suivant :

    ```javascript
    'use strict';
    var path = require('path');
    var express = require('express');

    var app = express();

    var staticPath = path.join(__dirname, '/');
    app.use(express.static(staticPath));

    // Allows you to set port in the project properties.
    app.set('port', process.env.PORT || 3000);

    var server = app.listen(app.get('port'), function() {
        console.log('listening');
    });
    ```

   Le code précédent utilise Express pour démarrer Node.js en tant que serveur d’applications web. Ce code permet d’affecter au port le numéro de port configuré dans les propriétés du projet (par défaut, le port 1337 est configuré dans les propriétés). Pour ouvrir les propriétés du projet, cliquez avec le bouton droit sur le projet dans l’Explorateur de solutions, puis choisissez **Propriétés**.

1. Ouvrez *app.tsx*, puis ajoutez le code suivant :

    ```javascript
    declare var require: any

    var React = require('react');
    var ReactDOM = require('react-dom');

    class Hello extends React.Component {
        render() {
            return (
                <h1>Welcome to React!!</h1>
            );
        }
    }

    ReactDOM.render(<Hello />, document.getElementById('root'));
    ```

    Le code précédent utilise la syntaxe JSX et React pour afficher un message simple.

1. Ouvrez *index.html* et remplacez la section **body** par le code suivant :

    ```html
    <body>
        <div id="root"></div>
        <!-- scripts -->
        <script src="./dist/app-bundle.js"></script>
    </body>
    ```

    Cette page HTML charge *app-bundle.js*, qui contient le code JSX et React transpilé en JavaScript brut. Pour le moment, *app-bundle.js* est un fichier vide. Dans la section suivante, vous allez configurer les options de transpilation du code.

## <a name="configure-webpack-and-typescript-compiler-options"></a>Configurer webpack et les options du compilateur TypeScript

Au cours des étapes précédentes, vous avez ajouté *webpack-config.js* au projet. Vous devez ajouter ensuite le code de configuration de webpack. Vous allez ajouter une configuration de webpack simple qui spécifie un fichier d’entrée (*app.tsx*) et un fichier de sortie (*app-bundle.js*) pour permettre le regroupement et la transpilation du code JSX en JavaScript brut. Pour la transpilation, vous pouvez également configurer certaines options du compilateur TypeScript. Ce code est une configuration de base conçue comme une introduction à webpack et au compilateur TypeScript.

1. Dans l’Explorateur de solutions, ouvrez *webpack-config.js* et ajoutez le code suivant.

    ```json
    module.exports = {
        devtool: 'source-map',
        entry: "./app.tsx",
        mode: "development",
        output: {
            filename: "./app-bundle.js"
        },
        resolve: {
            extensions: ['.Webpack.js', '.web.js', '.ts', '.js', '.jsx', '.tsx']
        },
        module: {
            rules: [
                {
                    test: /\.tsx$/,
                    exclude: /(node_modules|bower_components)/,
                    use: {
                        loader: 'ts-loader'
                    }
                }
            ]
        }
    }
    ```

    Le code de configuration de webpack indique à Webpack d’utiliser le chargeur TypeScript pour transpiler le code JSX.

1. Ouvrez tsconfig.json et ajoutez le code suivant pour spécifier les options du compilateur TypeScript :

    ```json
    {
      "compilerOptions": {
        "noImplicitAny": false,
        "module": "commonjs",
        "noEmitOnError": true,
        "removeComments": false,
        "sourceMap": true,
        "target": "es5",
        "jsx": "react"
      },
      "exclude": [
        "node_modules"
      ],
      "files": [
        "app.tsx"
      ]
    }
    ```

    app.tsx est spécifié en tant que fichier source.

## <a name="transpile-the-jsx"></a>Transpiler le code JSX

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le nœud de projet, puis choisissez **Ouvrir l’invite de commandes ici**.

1. À l’invite de commandes, tapez la commande suivante :

    `node_modules\.bin\webpack app.tsx --config webpack-config.js`

    La fenêtre d’invite de commandes affiche le résultat.

    ![Exécuter webpack](../nodejs/media/tutorial-nodejs-react-run-webpack.png)

    Si vous voyez des erreurs à la place de la sortie précédente, vous devez les corriger pour permettre à votre application de fonctionner correctement. Si les versions de votre package npm sont différentes de celles présentées dans ce tutoriel, cela peut constituer une source d’erreurs. Vous pouvez éventuellement corriger les erreurs en utilisant les versions exactes indiquées au cours des étapes précédentes. De plus, si une ou plusieurs de ces versions de package sont dépréciées et génèrent des erreurs, vous devrez peut-être installer une version plus récente pour corriger ces erreurs.

1. Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le nœud de projet. Choisissez **Ajouter** > **Dossier existant**, choisissez le dossier *dist*, puis cliquez sur **Sélectionner un dossier**.

    Visual Studio ajoute le dossier *dist* au projet, lequel contient *app-bundle.js* et *app-bundle.js.map*.

1. Ouvrez *app-bundle.js* pour voir le code JavaScript transpilé.

1. Si vous êtes invité à recharger des fichiers modifiés de façon externe, cliquez sur **Oui pour tout**.

    ![Charger des fichiers modifiés](../nodejs/media/tutorial-nodejs-react-reload-files.png)

Chaque fois que vous apportez des changements à *app.tsx*, vous devez réexécuter la commande webpack.

## <a name="run-the-app"></a>Exécuter l'application

1. Vérifiez que Chrome est sélectionné en tant que cible de débogage actuelle.

    ![Sélectionner Chrome en tant que cible de débogage](../nodejs/media/tutorial-nodejs-react-debug-target.png)

1. Pour exécuter l’application, appuyez sur **F5** (**Déboguer** > **Démarrer le débogage**) ou sur le bouton fléché vert.

    Une fenêtre de console Node.js s’ouvre et affiche le port sur lequel le débogueur est à l’écoute.

    Visual Studio démarre l’application en lançant le fichier de démarrage, *server.js*.

    ![Exécuter React dans le navigateur](../nodejs/media/tutorial-nodejs-react-running-react.png)

1. Fermez la fenêtre du navigateur.

1. Fermez la fenêtre de console.

## <a name="set-a-breakpoint-and-run-the-app"></a>Définir un point d’arrêt et exécuter l’application

1. Dans *server.js*, cliquez dans la marge située à gauche de la déclaration de `staticPath` pour définir un point d’arrêt :

    ![Définir un point d’arrêt](../nodejs/media/tutorial-nodejs-react-set-breakpoint.png)

    Les points d'arrêt constituent une fonctionnalité élémentaire et essentielle de toute procédure de débogage fiable. Quand vous définissez un point d'arrêt, Visual Studio interrompt l'exécution du code à l'emplacement du point d'arrêt pour vous permettre d'examiner les valeurs des variables, le comportement de la mémoire ou encore la bonne exécution ou non d'une branche de code.

1. Pour exécuter l’application, appuyez sur **F5** (**Déboguer** > **Démarrer le débogage**).

    Le débogueur s’arrête au point d’arrêt que vous avez défini (l’instruction active est marquée en jaune). Vous pouvez maintenant inspecter l’état de votre application en pointant sur les variables situées dans la portée et en utilisant les fenêtres du débogueur, notamment les fenêtres **Variables locales** et **Espion**.

1. Appuyez sur **F5** pour continuer l’exécution de l’application.

1. Pour utiliser les outils de développement Chrome, appuyez sur **F12**. Vous pouvez utiliser ces outils pour examiner le DOM et interagir avec l’application à l’aide de la console JavaScript.

1. Fermez le navigateur web et la console.

## <a name="set-and-hit-a-breakpoint-in-the-client-side-react-code"></a>Définir et atteindre un point d’arrêt dans le code React côté client

Dans la section précédente, vous avez attaché le débogueur au code Node.js côté serveur. Pour attacher le débogueur depuis Visual Studio et atteindre des points d’arrêt dans du code React côté client, vous devez aider le débogueur à identifier le processus approprié. Voici une façon d’y parvenir.

1. Fermez toutes les fenêtres de Chrome.

1. Ouvrez la commande **Exécuter** à partir du bouton **Démarrer** de Windows (cliquez avec le bouton droit de la souris et choisissez **Exécuter**), puis entrez la commande suivante :

    `chrome.exe --remote-debugging-port=9222`

    Chrome démarre avec l’activation du débogage.

1. Passez à Visual Studio et définissez un point d’arrêt dans le code d’*app-bundle.js*, dans la fonction `render()`, comme indiqué dans l’illustration suivante :

    ![Définir un point d’arrêt](../nodejs/media/tutorial-nodejs-react-set-breakpoint-client-code.png)

1. Chrome étant sélectionné comme cible de débogage dans Visual Studio, appuyez sur **Ctrl + F5** (**Déboguer** > **Exécuter sans débogage**) pour exécuter l’application dans le navigateur.

    L’application s’ouvre dans un nouvel onglet du navigateur.

1. Choisissez **Déboguer** > **Attacher au processus**.

1. Dans la boîte de dialogue **Attacher au processus**, choisissez **Code WebKit** dans le champ **Attacher à**, puis tapez **chrome** dans la zone de filtre pour filtrer les résultats de la recherche.

1. Sélectionnez le processus Chrome et le port d’hôte approprié (1337 dans cet exemple), puis cliquez sur **Attacher**.

    ![Attacher au processus](../nodejs/media/tutorial-nodejs-react-attach-to-process.png)

    Vous savez que le débogueur est correctement attaché quand l’Explorateur DOM et la console JavaScript s’ouvrent dans Visual Studio. Ces outils de débogage sont similaires aux outils de développement Chrome et aux outils F12 pour Edge.

    > [!NOTE]
    > Si le débogueur ne s’attache pas et que vous voyez le message « Impossible de s’attacher au processus. Une opération n’est pas légale dans l’état actuel. », utilisez le Gestionnaire des tâches pour fermer toutes les instances de Chrome avant de démarrer Chrome en mode débogage. Les extensions Chrome peuvent être en cours d’exécution et empêcher le mode débogage complet.

1. Dans la mesure où le code avec le point d’arrêt s’est déjà exécuté, actualisez la page de votre navigateur pour atteindre le point d’arrêt.

    Pendant que l’exécution du débogueur est en pause, vous pouvez examiner l’état de votre application en pointant sur les variables et en utilisant les fenêtres du débogueur. Vous pouvez faire avancer le débogueur en exécutant pas à pas le code (**F5**, **F10** et **F11**).

    Vous pouvez éventuellement atteindre le point d’arrêt dans *app-bundle.js* ou son emplacement mappé dans *app.tsx*, en fonction de votre environnement et de l’état du navigateur. De toute façon, vous pouvez exécuter pas à pas le code et examiner les variables.

    * Si vous devez arrêter l’exécution du code dans *app.tsx* et que vous n’y parvenez pas, utilisez **Attacher au processus** comme décrit dans la procédure précédente pour attacher le débogueur. Ouvrez ensuite le fichier *app.tsx* généré dynamiquement à partir de l’Explorateur de solutions en ouvrant **Documents de script** > **app.tsx**, définissez un point d’arrêt et actualisez la page dans votre navigateur.

        Sinon, si vous devez arrêter l’exécution du code dans *app.tsx* et que vous n’y parvenez pas, essayez d’utiliser l’instruction `debugger;` dans *app.tsx*, ou définissez des points d’arrêt dans les outils de développement Chrome à la place.

    * Si vous devez arrêter l’exécution du code dans *app-bundle.js* et que vous n’y parvenez pas, supprimez le fichier de mappage de source, *app-bundle.js.map*.

    > [!TIP]
    > Une fois que vous avez effectué l’attachement au processus la première fois en suivant ces étapes, vous pouvez rapidement effectuer un rattachement au même processus dans Visual Studio 2017 en choisissant **Déboguer** > **Rattacher au processus**.

## <a name="next-steps"></a>Étapes suivantes

Dans ce tutoriel, vous avez appris à créer une application Node.js et React, à transpiler du code JSX et à effectuer du débogage. Pour en savoir plus sur Node.js Tools pour Visual Studio, consultez la page de Wiki.

> [!div class="nextstepaction"]
> [Node.js Tools pour Visual Studio](https://github.com/Microsoft/nodejstools)
