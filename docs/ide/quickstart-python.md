---
title: 'Démarrage rapide : utiliser Visual Studio pour créer une application web Python'
description: Ce guide de démarrage rapide utilise Visual Studio et le framework Flask pour générer une application web simple en Python.
ms.date: 05/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 9a62dfc6cfe5cef21cc2198dd90867a7960312f9
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="quickstart-create-your-first-python-web-app-using-visual-studio"></a>Démarrage rapide : créer votre première application web Python à l’aide de Visual Studio

Dans cette présentation de 5-10 minutes de Visual Studio en tant qu’environnement de développement intégré (IDE) Python, vous allez créer une application web Python simple à partir de l’infrastructure Flask. Les étapes distinctes que vous suivrez pour créer le projet vous renseigneront sur les fonctionnalités de base de Visual Studio.

Si vous n’avez pas encore installé Visual Studio, accédez à la page [Téléchargements Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) pour le faire gratuitement. Dans le programme d’installation, veillez à sélectionner la charge de travail **Développement Python**.

## <a name="create-the-project"></a>Créer le projet

Les étapes suivantes créent un projet vide qui sert de conteneur pour l’application :

1. Ouvrez Visual Studio 2017.

1. Dans la barre de menus supérieure, choisissez **Fichier > Nouveau > Projet**.

1. Dans la boîte de dialogue **Nouveau projet**, entrez « Projet Web Python » dans le champ de recherche qui se trouve dans le coin supérieur droit, choisissez **Projet Web** dans la liste du milieu, donnez un nom du type « HelloPython » au projet, puis choisissez **OK**.

    ![Boîte de dialogue Nouveau projet avec le projet web Python sélectionné](media/quickstart-python-00-web-project.png)

    Si vous ne voyez pas les modèles de projets Python, quittez la boîte de dialogue **Nouveau projet** puis, dans la barre de menus supérieure, choisissez **Outils > Obtenir les outils et fonctionnalités** pour ouvrir **Visual Studio Installer**. Choisissez la charge de travail **Développement Python**, puis choisissez **Modifier**.

    ![Charge de travail de développement Python dans le programme d’installation de Visual Studio](../python/media/installation-python-workload.png)

1. Le nouveau projet s’ouvre dans **l’Explorateur de solutions** dans le volet droit. Le projet est vide à ce stade, car il ne contient aucun autre fichier.

    ![Explorateur de solutions affichant le projet vide](media/quickstart-python-01-empty-project.png)

**Question : Quel avantage présente la création d’un projet dans Visual Studio pour une application Python ?**

**Réponse** : Les applications Python sont généralement définies à l’aide de fichiers et de dossiers uniquement, mais cette structure simple peut se révéler fastidieuse pour des applications de plus grande envergure, qui impliquent éventuellement des fichiers générés automatiquement, du JavaScript pour les applications web, etc. Un projet Visual Studio permet de gérer cette complexité. Le projet (un fichier *.pyproj*) identifie tous les fichiers sources et de contenu associés à votre projet, contient des informations de génération pour chaque fichier, conserve les informations pour l’intégration aux systèmes de contrôle de code source et vous permet d’organiser votre application en composants logiques.

**Question : Quelle est la « solution » indiquée dans l’Explorateur de solutions ?**

**Réponse** : Une solution Visual Studio est un conteneur permettant de gérer de façon groupée un ou plusieurs projets apparentés. Il stocke les paramètres de configuration qui ne sont pas propres à un projet. Les projets d’une même solution peuvent également faire référence les uns aux autres ; ainsi, l’exécution de l’un d’entre eux (une application Python) en génère automatiquement un deuxième (par exemple, une extension C++ utilisée dans l’application Python).

## <a name="install-the-flask-library"></a>Installer la bibliothèque Flask

Les applications web dans Python utilisent presque toujours l’une des nombreuses bibliothèques Python disponibles pour gérer les détails de bas niveau tels que le routage des demandes web et la mise en forme des réponses. Visual Studio fournit à cette fin un large éventail de modèles pour les applications web ; vous utiliserez l’un d’entre eux dans la suite de ce guide de démarrage rapide.

Suivez les étapes ci-dessous pour installer la bibliothèque Flask dans l’« environnement global » par défaut utilisé par Visual Studio pour ce projet.

1. Développez le nœud **Environnements Python** dans le projet pour voir l’environnement par défaut pour le projet.

    ![Explorateur de solutions montrant l’environnement Python](media/quickstart-python-02-default-environment.png)

1. Cliquez avec le bouton droit sur l’environnement et sélectionnez **Installer le package Python**. Cette commande ouvre la fenêtre **Environnements Python** sous l’onglet **Packages**.

1. Entrez « flask » dans le champ de recherche et sélectionnez **installation pip de flask à partir de PyPI**. Acceptez les invites de privilèges d’administrateur et observez la progression dans la fenêtre **Sortie** de Visual Studio. (Une invite d’élévation se produit lorsque le dossier des packages de l’environnement global se situe dans une zone protégée comme *C:\Program Files*.)

    ![Installer la bibliothèque Flask](media/quickstart-python-03-install-package.png)

1. Une fois installée, la bibliothèque apparaît dans l’environnement dans **l’Explorateur de solutions**, ce qui signifie que vous pouvez l’utiliser dans le code Python.

    ![Bibliothèque Flask installée](media/quickstart-python-04-package-installed.png)

> [!Note]
> Au lieu d’installer les bibliothèques du projet dans l’environnement global, les développeurs créent généralement un « environnement virtuel » à cette fin. Les modèles Visual Studio offrent la plupart du temps cette possibilité, comme nous l’avons précisé dans le [Guide de démarrage rapide : Créer un projet Python à l’aide d’un modèle](../python/quickstart-02-python-in-visual-studio-project-from-template.md).

**Question : Où peut-on se renseigner sur les autres packages Python disponibles ?**

**Réponse** : Accédez à [Python Package Index](https://pypi.org/).

## <a name="add-a-code-file"></a>Ajouter un fichier de code

Vous êtes maintenant prêt à ajouter un peu de code Python pour implémenter une application web minimale.

1. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis sélectionnez **Ajouter > Nouvel élément**.

1. Dans la boîte de dialogue qui s’affiche, sélectionnez **Fichier Python vide**, nommez-le *app.py*, puis sélectionnez **Ajouter**. Visual Studio ouvre automatiquement le fichier dans une fenêtre d’éditeur.

1. Copiez le code suivant et collez-le dans *app.py* :

    ```python
    from flask import Flask

    # Create an instance of the Flask class that is the WSGI application.
    # The first argument is the name of the application module or package,
    # typically __name__ when using a single module.
    app = Flask(__name__)

    # Flask route decorators map / and /hello to the hello function.
    # To add other resources, create functions that generate the page contents
    # and add decorators to define the appropriate resource locators for them.

    @app.route('/')
    @app.route('/hello')
    def hello():
        # Render the page
        return "Hello Python!"

    if __name__ == '__main__':
        # Run the app server on localhost:4449
        app.run('localhost', 4449)
    ```

1. Vous avez peut-être remarqué que la boîte de dialogue **Ajouter > Nouvel élément** présente de nombreux autres types de fichiers qu’il est possible d’ajouter à un projet Python, notamment une classe Python, un package Python, un test unitaire Python, des fichiers *web.config*, etc. En règle générale, ces modèles d’élément, comme on les appelle, sont un excellent moyen de créer rapidement des fichiers avec du code réutilisable et utile.

**Question : Où peut-on se renseigner sur Flask ?**

**Réponse** : Reportez-vous à la documentation de Flask, en commençant par le [Guide de démarrage rapide Flask](http://flask.pocoo.org/docs/0.12/quickstart/#quickstart).

## <a name="run-the-application"></a>Exécuter l'application

1. Cliquez avec le bouton droit sur *app.py* dans l’**Explorateur de solutions** et sélectionnez **Définir comme fichier de démarrage**. Cette commande identifie le fichier de code à lancer dans Python à l’exécution de l’application.

    ![Définition du fichier de démarrage d’un projet dans l’Explorateur de solutions](media/quickstart-python-05-set-as-startup-file.png)

1. Cliquez avec le bouton droit sur le projet dans **l’Explorateur de solutions**, puis sélectionnez **Propriétés**. Ensuite, sélectionnez l’onglet **Déboguer** et affectez la valeur `4449` à la propriété **Numéro de port**. Cette étape permet de s’assurer que Visual Studio lance un navigateur avec `localhost:4449`, par cohérence avec les arguments `app.run` du code.

1. Sélectionnez **Déboguer > Démarrer sans débogage** (**Ctrl**+**F5**) pour enregistrer les modifications apportées aux fichiers et exécuter l’application.

1. Une fenêtre de commande s’affiche avec le message « Exécution sous https://localhost:4449/ », puis une fenêtre de navigateur s’ouvre sur `localhost:4449`, où figure le message « Hello, Python ! ». La requête GET apparaît également dans la fenêtre de commande avec l’état 200.

    Si le navigateur ne s’ouvre pas automatiquement, lancez celui de votre choix et accédez à `localhost:4449`.

    Si vous voyez uniquement l’interpréteur de commandes interactif Python dans la fenêtre de commande, ou si cette fenêtre clignote brièvement à l’écran, vérifiez que vous avez défini *app.py* comme fichier de démarrage à l’étape 1 ci-dessus.

1. Accédez à `localhost:4449/hello` afin de vérifier que l’élément décoratif de la ressource `/hello` fonctionne également. Là encore, la requête GET apparaît dans la fenêtre de commande avec l’état 200. N’hésitez pas à essayer d’autres URL pour vérifier qu’elles affichent des codes d’état 404 dans la fenêtre de commande.

1. Fermez la fenêtre de commande pour arrêter l’application, puis fermez la fenêtre du navigateur.

**Question : Quelle est la différence entre les commandes Démarrer sans débogage et Démarrer le débogage ?**

**Réponse** : On utilise **Démarrer le débogage** pour exécuter l’application dans le contexte du [Débogueur Visual Studio](../python/debugging-python-in-visual-studio.md), qui permet de définir des points d’arrêt, d’examiner les variables et de parcourir le code ligne par ligne. Les applications risquent de s’exécuter plus lentement dans le débogueur à cause des hooks qui permettent le débogage. **Démarrer sans débogage**, à l’inverse, exécute directement l’application comme si elle était lancée en ligne de commande, sans contexte de débogage ; par ailleurs, il ouvre automatiquement un navigateur et accède à l’URL spécifiée dans l’onglet **Déboguer** des propriétés du projet.

## <a name="next-steps"></a>Étapes suivantes

Félicitations ! Vous avez exécuté votre première application Python à partir de Visual Studio, et vous avez commencé à apprendre à utiliser Visual Studio comme un environnement IDE Python !

Les étapes que vous avez suivies dans ce guide de démarrage rapide étant relativement génériques, vous avez probablement deviné qu’il est possible et préférable de les automatiser. Cette automatisation est le rôle des modèles de projet de Visual Studio. Sélectionnez le bouton ci-dessous pour voir une démonstration de création d’une application web similaire à celle de cet article, mais en moins d’étapes.

> [!div class="nextstepaction"]
> [Guide de démarrage rapide : Créer un projet Python à l’aide d’un modèle](../python/quickstart-02-python-in-visual-studio-project-from-template.md)

Pour continuer avec un didacticiel plus complet sur Python dans Visual Studio, qui explique notamment comment utiliser la fenêtre interactive, le débogage, la visualisation des données et Git, sélectionnez le bouton ci-dessous.

> [!div class="nextstepaction"]
> [Didacticiel : Bien démarrer avec Python dans Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

Pour explorer plus en détail ce que Visual Studio a à offrir, sélectionnez les liens ci-dessous.

- En savoir plus sur les [modèles d’applications web Python dans Visual Studio](../python/python-web-application-project-templates.md).
- En savoir plus sur le [débogage Python](../python/debugging-python-in-visual-studio.md)
- En savoir plus sur [l’environnement IDE Visual Studio](../ide/visual-studio-ide.md) en général.
