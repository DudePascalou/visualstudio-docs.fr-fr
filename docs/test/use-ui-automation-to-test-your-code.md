---
title: Utiliser UI Automation pour tester votre code dans Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.codedUITest
- vs.codedUITest.recorder
- vs.codedUITest.testbuilder
- vs.codedUITest.addAssertions
- vs.codedUITest.createdialog
helpviewer_keywords:
- automated tests, testing UI interface
- coded UI test
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 897ce97da798509253bf3f7d93a79735cc354965
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
---
# <a name="use-ui-automation-to-test-your-code"></a>Utiliser UI Automation pour tester votre code

Vous pouvez créer des tests automatisés qui vérifient l’interface utilisateur (IU) de votre application. Ces tests sont appelés *tests codés de l’interface utilisateur*. Ils permettent d’effectuer des tests fonctionnels des contrôles d’interface utilisateur et de vérifier que l'application entière, y compris son interface utilisateur, fonctionne correctement. Les tests codés de l'interface utilisateur sont particulièrement utiles quand il y a une validation ou autre logique dans l'interface utilisateur, par exemple dans une page web. On les utilise aussi fréquemment pour automatiser un test manuel existant.

Comme l'illustre la figure ci-dessous, dans un scénario de développement par défaut, il est courant qu'initialement vous génériez simplement votre application (F5) et cliquiez parmi les contrôles d'interface utilisateur pour vérifier que tout fonctionne comme prévu. Vous pouvez ensuite décider de créer un test codé pour ne pas avoir à continuer de tester l’application manuellement. Selon les fonctionnalités spécifiques testées dans votre application, vous pouvez écrire du code pour un test fonctionnel ou pour un test d'intégration qui peut ou non inclure des tests au niveau de l'interface utilisateur. Si vous souhaitez simplement accéder directement à une logique métier, vous pouvez coder un test unitaire. Toutefois, dans certaines circonstances, il peut être bénéfique de tester les différents contrôles d'interface utilisateur de votre application. Un test codé de l'interface utilisateur peut automatiser le scénario initial (F5) et vérifier que l'évolution du code n'a aucun impact sur la fonctionnalité de votre application.

![Test lors du développement d’application](../test/media/cuit_overview.png)

Créer un test codé de l'interface utilisateur est très facile. Il vous suffit d'exécuter le test manuellement pendant que le Générateur de test codé de l'interface utilisateur s'exécute en arrière-plan. Vous pouvez aussi spécifier les valeurs qui doivent apparaître dans des champs spécifiques. Le Générateur de test codé de l'interface utilisateur enregistre vos actions et génère du code à partir de ces actions. Une fois le test créé, vous pouvez le modifier dans un éditeur spécial qui vous permet de modifier la séquence d'actions.

En guise d'alternative, si vous avez un cas de test qui a été enregistré dans Microsoft Test Manager, vous pouvez générer du code à partir de ce cas de test. Pour plus d’informations, consultez [Enregistrer et lire des tests manuels](/vsts/manual-test/getting-started/record-play-back-manual-tests).

Le Générateur de test codé de l'interface utilisateur et l'éditeur spécial simplifient la création et la modification des tests codés de l'interface utilisateur même si vos compétences principales sont axées sur les tests plutôt que sur le codage. Si vous êtes développeur et que vous souhaitez approfondir le test, le code est structuré pour être facile à copier et à adapter. Par exemple, vous pouvez enregistrer un test d’achat d’un article sur un site web, puis modifier le code généré et ajouter une boucle qui achète de nombreux articles.

**Spécifications**

- Visual Studio Enterprise

Pour plus d’informations sur les plateformes et les configurations prises en charge par les tests codés de l’interface utilisateur, consultez [Plateformes prises en charge pour les tests codés de l’interface utilisateur](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md).

## <a name="create-coded-ui-tests"></a>Créer des tests codés de l’interface utilisateur

1. Installez le composant **Test codé de l’interface utilisateur**.

   Si vous ne l’avez pas déjà fait, installez le composant **Test codé de l’interface utilisateur** de Visual Studio. Lancez **Visual Studio Installer** en choisissant **Outils** > **Obtenir des outils et des fonctionnalités**. Dans **Visual Studio Installer**, choisissez l’onglet **Composants individuels** et faites défiler jusqu’à la section **Débogage et test**. Sélectionnez le composant **Test codé de l’interface utilisateur** et choisissez **Modifier**.

   ![Composant Test codé de l’interface utilisateur](media/coded-ui-test-component.png)

1. Créer un projet de test codé de l'interface utilisateur.

   Les tests codés de l'interface utilisateur doivent appartenir à un projet de test codé de l'interface utilisateur. Si vous n’avez pas encore de projet de test codé de l’interface utilisateur, créez-en un. Choisissez **Fichier** > **Nouveau** > **Projet** pour ouvrir la boîte de dialogue **Nouveau projet**. Dans le volet des catégories à gauche, développez **Installé** > **Visual Basic** *ou* **Visual C#**  >  **Test**. Sélectionnez le modèle **Projet de test codé de l’interface utilisateur** et choisissez **OK**.

   ![Modèle de projet de test codé de l’interface utilisateur dans la boîte de dialogue Nouveau projet](media/coded-ui-test-project-template.png)

2. Ajouter un fichier de test codé de l'interface utilisateur.

     Si vous venez de créer un projet de test codé de l'interface utilisateur, le premier fichier de test codé de l'interface utilisateur est ajouté automatiquement. Pour ajouter un autre fichier de test, ouvrez le menu contextuel du projet de test codé de l’interface utilisateur dans l’**Explorateur de solutions** et choisissez **Ajouter** > **Test codé de l’interface utilisateur**.

     Dans la boîte de dialogue **Générer le code pour le test codé de l’interface utilisateur**, choisissez **Enregistrer les actions, modifier le mappage d’IU ou ajouter des assertions**.

     ![Boîte de dialogue Générer le code pour le test codé de l’interface utilisateur](media/generate-code-for-coded-ui-test.png)

     Le Générateur de test codé de l’interface utilisateur s’affiche.

     ![Générateur de test codé de l'interface utilisateur](../test/media/codedui_testbuilder.png)

3. Enregistrez une séquence d’actions.

     **Pour commencer l’enregistrement**, choisissez l’icône **Enregistrer**. Effectuez les actions que vous souhaitez tester dans votre application, y compris le démarrage de l'application si nécessaire. Par exemple, si vous testez une application web, vous pourriez démarrer un navigateur, accéder au site web et vous connecter à l’application.

     **Pour mettre l’enregistrement en pause**, par exemple si vous venez de recevoir du courrier électronique à traiter, choisissez **Pause**.

    > [!WARNING]
    > Toutes les actions effectuées sur le Bureau sont enregistrées. Mettez l'enregistrement en pause si vous effectuez des actions susceptibles d'inclure des données confidentielles dans l'enregistrement.

     **Pour supprimer des actions** enregistrées par erreur, choisissez **Modifier des actions**.

     **Pour générer le code** qui va répliquer vos actions, choisissez l’icône **Générer le code**, puis tapez un nom et une description pour votre méthode de test codé de l’interface utilisateur.

4. Vérifiez les valeurs dans des champs de l’interface utilisateur, comme des zones de texte.

     Choisissez **Ajouter des assertions** dans le Générateur de test codé de l’interface utilisateur, puis choisissez un contrôle d’IU dans votre application en cours d’exécution. Dans la liste de propriétés qui s’affiche, sélectionnez une propriété, par exemple **Texte** dans une zone de texte. Dans le menu contextuel, choisissez **Ajouter une assertion**. Dans la boîte de dialogue, sélectionnez l'opérateur de comparaison, la valeur de comparaison et le message d'erreur.

     Fermez la fenêtre d’assertion et choisissez **Générer le code**.

     ![Élément de ciblage du test codé de l’interface utilisateur](../test/media/codedui_1.png "CodedUI_1")

    > [!TIP]
    > Alternez entre l'enregistrement des actions et la vérification des valeurs. Générez le code à la fin de chaque séquence d'actions ou de vérifications. Si vous le souhaitez, vous pourrez insérer de nouvelles actions et vérifications ultérieurement.

     Pour plus d’informations, consultez [Validation des propriétés des contrôles](#VerifyingCodeUsingCUITGenerateAssertions).

5. Affichez le code de test généré.

     Pour afficher le code généré, fermez la fenêtre du Générateur de test codé de l'interface utilisateur. Dans le code figurent les noms que vous avez donnés à chaque étape. Le code se trouve dans le fichier de test codé de l'interface utilisateur que vous avez créé :

    ```csharp
    [CodedUITest]
    public class CodedUITest1
    { ...
      [TestMethod]
      public void CodedUITestMethod1()
      {
          this.UIMap.AddTwoNumbers();
          this.UIMap.VerifyResultValue();
          // To generate more code for this test, select
          // "Generate Code" from the shortcut menu.
      }
    }
    ```

6. Ajoutez d’autres actions et assertions.

   Placez le curseur au point approprié dans la méthode de test puis, dans le menu contextuel, choisissez **Générer le code pour le test codé de l’interface utilisateur**. Le nouveau code sera inséré à ce point.

7. Modifiez les détails des actions de test et des assertions.

     Ouvrez UIMap.uitest. Ce fichier s'ouvre dans l'Éditeur de test codé de l'interface utilisateur, où vous pouvez modifier n'importe quelle séquence d'actions enregistrée et vos assertions.

     ![Éditeur de test codé de l’interface utilisateur](../test/media/cuit_editor_edit.png "CUIT_Editor_edit")

     Pour plus d’informations, consultez [Modification des tests codés de l’interface utilisateur à l’aide de l’éditeur de test codé de l’interface utilisateur](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

8. Exécutez le test.

   Ouvrez l’Explorateur de tests ou le menu contextuel dans la méthode de test, puis choisissez **Exécuter les tests**. Pour plus d’informations sur la façon d’exécuter les tests, consultez [Exécuter des tests unitaires avec l’Explorateur de tests](../test/run-unit-tests-with-test-explorer.md) et *Options supplémentaires pour l’exécution des tests codés de l’interface utilisateur* dans la section [Quelle est la suite ?](#VerifyCodeUsingCUITWhatsNext) située à la fin de cette rubrique.

Les autres sections de cette rubrique décrivent plus en détail les étapes de cette procédure.

Pour obtenir un exemple plus détaillé, consultez [Procédures pas à pas : création, édition et gestion d’un test codé de l’interface utilisateur](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md). Dans cette procédure pas à pas, vous allez créer une simple application WPF (Windows Presentation Foundation) pour montrer comment créer, modifier et gérer un test codé de l'interface utilisateur. La procédure pas à pas fournit des solutions pour la correction des tests interrompus par différents problèmes de synchronisation et de refactorisation des contrôles.

### <a name="start-and-stop-the-application-under-test"></a>Démarrer et arrêter l’application testée

Si vous ne voulez pas démarrer et arrêter l’application, le navigateur ou la base de données séparément pour chaque test, procédez comme suit :

- Si vous ne voulez pas enregistrer les actions pour démarrer votre application durant le test, vous devez la démarrer avant de choisir l’icône **Enregistrer**.

- À la fin du test, le processus dans lequel le test s'exécute est arrêté. Si vous avez démarré votre application dans le test, l'application se ferme généralement à l'issue du test.  Si vous ne voulez pas que votre application soit fermée à la fin du test, ajoutez un fichier *.runsettings* à votre solution et utilisez l’option `KeepExecutorAliveAfterLegacyRun`. Pour plus d’informations, consultez [Configurer des tests unitaires à l’aide d’un fichier .runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).

- Ajoutez une méthode d’initialisation de test, identifiée par un attribut `[TestInitialize]`, qui exécute du code au début de chaque méthode de test. Vous pouvez par exemple démarrer l'application à partir de la méthode TestInitialize.

- Ajoutez une méthode de nettoyage de test, identifiée par un attribut `[TestCleanup]`, qui exécute du code à la fin de chaque méthode de test. La méthode de fermeture de l'application pourrait par exemple être appelée à partir de la méthode TestCleanup.

### <a name="validate-the-properties-of-ui-controls"></a>Valider les propriétés des contrôles d’interface utilisateur

Vous pouvez utiliser le **Générateur de test codé de l’interface utilisateur** pour ajouter un contrôle d’interface utilisateur à l’objet <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> de votre test ou pour générer du code pour une méthode de validation qui utilise une assertion pour un contrôle d’interface utilisateur.

Pour générer des assertions pour vos contrôles d’IU, choisissez l’outil **Ajouter des assertions** dans le Générateur de test codé de l’interface utilisateur, puis faites-le glisser vers le contrôle de l’application testée dont vous souhaitez vérifier le bon fonctionnement. Quand la zone met votre contrôle en surbrillance, relâchez le bouton de la souris. Le code de la classe de contrôle est créé immédiatement dans le fichier `UIMap.Designer.cs`.

![Élément de ciblage du test codé de l’interface utilisateur](../test/media/codedui_1.png "CodedUI_1")

Les propriétés de ce contrôle sont maintenant listées dans la boîte de dialogue **Ajouter des assertions**.

Une autre approche pour accéder à un contrôle spécifique consiste à choisir la flèche **(<<)** pour développer l’affichage du **Mappage de contrôle d’IU**. Pour rechercher un contrôle parent, frère ou enfant, vous pouvez cliquer n’importe où sur le mappage et utiliser les touches de direction pour vous déplacer dans l’arborescence.

![Propriétés du test codé de l’interface utilisateur](../test/media/codedui_2.png "CodedUI_2")

> [!TIP]
> Si vous ne voyez aucune propriété quand vous sélectionnez un contrôle dans votre application, ou si vous ne voyez pas le contrôle dans le mappage des contrôles de l’interface utilisateur, vérifiez que le contrôle a un ID unique dans le code de l’application. L’ID unique peut être un attribut d’ID HTML ou un UID WPF.

Ouvrez ensuite le menu contextuel sur la propriété du contrôle d’IU à vérifier, puis pointez sur **Ajouter une assertion**. Dans la boîte de dialogue **Ajouter une assertion**, sélectionnez le **Comparateur** pour votre assertion, par exemple <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A>, et tapez la valeur de votre assertion dans **Valeur de comparaison**.

![Assertions du test codé de l’interface utilisateur](../test/media/codedui_3.png "CodedUI_3")

Une fois que vous avez ajouté toutes les assertions pour votre test, choisissez **OK**.

Pour générer le code de vos assertions et ajouter le contrôle au mappage d’IU, choisissez l’icône **Générer le code**. Tapez un nom pour votre méthode de test codé de l'interface utilisateur et une description de la méthode, qui sera ajoutée en guise de commentaires de la méthode. Choisissez **Ajouter et générer**. Choisissez ensuite l’icône **Fermer** pour fermer le **Générateur de test codé de l’interface utilisateur**. Du code semblable au suivant est généré. Par exemple, si vous avez entré le nom `AssertForAddTwoNumbers`, le code ressemble à ce qui suit :

- Ajoute un appel à la méthode assert AssertForAddTwoNumbers à la méthode de test dans votre fichier de test codé de l'interface utilisateur :

    ```csharp
    [TestMethod]
    public void CodedUITestMethod1()
    {
        this.UIMap.AddTwoNumbers();
        this.UIMap.AssertForAddTwoNumbers();
    }
    ```

     Vous pouvez modifier ce fichier pour changer l'ordre des étapes et des assertions ou pour créer de nouvelles méthodes de test. Pour ajouter du code, placez le curseur sur la méthode de test puis, dans le menu contextuel, choisissez **Générer le code pour le test codé de l’interface utilisateur**.

- Ajoute une méthode nommée `AssertForAddTwoNumbers` à votre mappage d'interface utilisateur (UIMap.uitest). Ce fichier s'ouvre dans l'Éditeur de test codé de l'interface utilisateur, où vous pouvez modifier les assertions.

     ![Modifier l’assertion à l’aide de l’éditeur de test codé de l’interface utilisateur](../test/media/cuit_editor_assert.png "CUIT_Editor_assert")

     Pour plus d’informations, consultez [Modification des tests codés de l’interface utilisateur à l’aide de l’éditeur de test codé de l’interface utilisateur](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

     Vous pouvez aussi afficher le code généré de la méthode d'assertion dans UIMap.Designer.cs. En revanche, vous ne devez pas modifier ce fichier. Si vous souhaitez créer une version adaptée du code, copiez les méthodes dans un autre fichier tel que UIMap.cs, renommez les méthodes, puis modifiez-les à cet endroit.

    ```csharp
    public void AssertForAddTwoNumbers()
    {
        ...
    }
    ```

#### <a name="select-a-hidden-control-using-the-keyboard"></a>Sélectionner un contrôle masqué avec le clavier

Si le contrôle que vous voulez sélectionner perd le focus et disparaît quand vous sélectionnez l’outil Ajouter des assertions dans le Générateur de test codé de l’interface utilisateur :

Parfois, quand vous ajoutez des contrôles et que vous vérifiez leurs propriétés, il peut être nécessaire d’utiliser le clavier. Par exemple, quand vous essayez d'enregistrer un test codé de l'interface utilisateur qui utilise un contrôle de menu contextuel, la liste des éléments de menu dans le contrôle perd le focus et disparaît quand vous tentez de sélectionner l'outil Ajouter des assertions dans le Générateur de test codé de l'interface utilisateur. Ainsi, dans l’illustration ci-dessous, le menu contextuel dans Internet Explorer perd le focus et disparaît si vous essayez de le sélectionner avec l’outil Ajouter des assertions.

![CodedUITest&#95;SelectControlKeyboard](../test/media/codeduitest_selectcontrolkeyboard.png "CodedUITest_SelectControlKeyboard")

Pour utiliser le clavier pour sélectionner un contrôle d'interface utilisateur, placez le pointeur de la souris sur le contrôle. Maintenez enfoncées la touche **Ctrl** et la touche **I** en même temps. Relâchez les touches. Le contrôle est enregistré par le Générateur de test codé de l'interface utilisateur.

> [!WARNING]
> Si vous utilisez Microsoft Lync, vous devez fermer Lync avant de démarrer le Générateur de test codé de l'interface utilisateur. Microsoft Lync interfère avec le raccourci clavier **Ctrl+I**.

#### <a name="manually-record-mouse-hovers"></a>Enregistrer manuellement des pointages de la souris

Si vous ne pouvez pas enregistrer un pointage de la souris sur un contrôle :

Dans certaines circonstances, un contrôle spécifique utilisé dans un test codé de l’interface utilisateur peut nécessiter l’utilisation du clavier pour enregistrer manuellement des événements de pointage de la souris. Par exemple, quand vous testez une application Windows Form ou WPF (Windows Presentation Foundation), il peut exister du code personnalisé. Ou un comportement spécial peut être défini pour le pointage sur un contrôle, par exemple le développement d'une arborescence quand un utilisateur place le pointeur de la souris dessus. Pour tester ces scénarios, vous devez signaler manuellement au Générateur de test codé de l'interface utilisateur que vous pointez sur un contrôle en appuyant sur des touches de clavier prédéfinies.

Quand vous exécutez votre test codé de l'interface utilisateur, placez le pointeur de la souris sur le contrôle. Ensuite, maintenez enfoncée la touche Ctrl pendant que vous maintenez enfoncées les touches Maj et R de votre clavier. Relâchez les touches. Un événement de pointage de la souris est enregistré par le Générateur de test codé de l'interface utilisateur.

![CodedUI&#95;Hover](../test/media/codedui_hover.png "CodedUI_Hover")

Une fois que vous avez généré la méthode de test, du code semblable à celui de l'exemple ci-dessous est ajouté au fichier UIMap.Desinger.cs :

```csharp
// Mouse hover '1' label at (87, 9)
Mouse.Hover(uIItem1Text, new Point(87, 9));
```

#### <a name="configure-mouse-hover-keyboard-assignments"></a>Configurer les affectations de touches du clavier pour le pointage de souris

Si l’affectation des touches pour la capture des événements de pointage de la souris est utilisée ailleurs dans mon environnement :

Si nécessaire, l’affectation du clavier par défaut de **Ctrl**+**Maj**+**R** utilisée pour appliquer les événements de pointage de la souris dans vos tests codés de l’interface utilisateur peut être configurée pour utiliser d’autres touches.

> [!WARNING]
> Vous ne devriez pas avoir à changer les affectations du clavier pour les événements de pointage de souris dans des circonstances normales. Procédez avec caution lors de la modification de l'affectation du clavier. Votre choix est peut-être déjà utilisé ailleurs dans Visual Studio ou dans l'application testée.

Pour changer les affectations du clavier, modifiez le fichier de configuration suivant :

*%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CodedUITestBuilder.exe.config*

Dans le fichier de configuration, changez les valeurs des clés `HoverKeyModifier` et `HoverKey` pour modifier les affectations du clavier :

```xml
<!-- Begin : Background Recorder Settings -->
<!-- HoverKey to use. -->
<add key="HoverKeyModifier" value="Control, Shift"/>
<add key="HoverKey" value="R"/>
```

#### <a name="set-implicit-mouse-hovers-for-the-web-browser"></a>Définir des pointages de la souris implicites pour le navigateur web

Si vous avez des problèmes pour enregistrer les pointages de la souris sur un site web :

Dans de nombreux sites web, quand vous placez le pointeur de souris sur un contrôle spécifique, il s’étend et affiche des détails supplémentaires. En général, ces détails prennent une apparence semblable aux menus des applications de bureau. Comme il s'agit d'un modèle commun, les tests codés de l'interface utilisateur activent les pointages implicites pour la navigation web. Par exemple, si vous enregistrez des pointages dans Internet Explorer, un événement est déclenché. Ces événements peuvent provoquer l'enregistrement de pointages redondants. Pour cette raison, les pointages implicites sont enregistrés avec `ContinueOnError` définis avec la valeur `true` dans le fichier de configuration du test d'interface utilisateur. Cela permet à la lecture de se poursuivre en cas d'échec d'un événement de pointage.

Pour activer l'enregistrement des pointages implicites dans un navigateur web, ouvrez le fichier de configuration :

*%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CodedUITestBuilder.exe.config*

Vérifiez que dans le fichier de configuration la clé `RecordImplicitiHovers` a la valeur `true`, comme illustré dans l'exemple ci-dessous :

```xml
<!--Use this to enable/disable recording of implicit hovers.-->
<add key="RecordImplicitHover" value="true"/>
```

## <a name="customize-the-coded-ui-test"></a>Personnaliser le test codé de l’interface utilisateur

Après avoir créé votre test codé de l’interface utilisateur, vous pouvez le modifier à l’aide de l’un des outils suivants dans Visual Studio :

- **Générateur de test codé de l’interface utilisateur :** vous pouvez utiliser le Générateur de test codé de l’interface utilisateur pour ajouter des contrôles et une validation supplémentaires à vos tests. Consultez la section [Ajout de contrôles et validation de leurs propriétés](#VerifyingCodeUsingCUITGenerateAssertions) dans cette rubrique.

- **Éditeur de test codé de l’interface utilisateur :** l’Éditeur de test codé de l’interface utilisateur vous permet de modifier facilement vos tests codés de l’interface utilisateur. Grâce à lui, vous pouvez rechercher, afficher et modifier vos méthodes de test. Vous pouvez aussi modifier des actions d'interface utilisateur et leurs contrôles associés dans le mappage de contrôle d'interface utilisateur. Pour plus d’informations, consultez [Modification des tests codés de l’interface utilisateur à l’aide de l’éditeur de test codé de l’interface utilisateur](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).

- **Éditeur de code :**

    - Ajoutez manuellement du code pour les contrôles dans votre test comme décrit dans la section [Codage des actions et propriétés du contrôle d’IU](#VerifyingCodeCUITActionsandProperties) de cette rubrique.

    - Après avoir créé un test codé de l'interface utilisateur, vous pouvez le modifier pour qu'il soit piloté par les données. Pour plus d’informations, consultez [Création d’un test codé de l’interface utilisateur piloté par les données](../test/creating-a-data-driven-coded-ui-test.md).

    - Dans une lecture de test codé de l'interface utilisateur, vous pouvez faire en sorte que le test attende que certains événements se produisent (par exemple qu'une fenêtre s'affiche, que la barre de progression disparaisse, et ainsi de suite). Pour cela, ajoutez la méthode UITestControl.WaitForControlXXX() appropriée. Pour obtenir la liste complète des méthodes disponibles, consultez [Suspension des tests codés de l’interface utilisateur en attendant des événements spécifiques pendant la lecture](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md). Pour obtenir un exemple de test codé de l’interface utilisateur qui attend l’activation d’un contrôle à l’aide de la méthode WaitForControlEnabled, consultez [Procédures pas à pas : création, édition et gestion d’un test codé de l’interface utilisateur](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).

    - Les tests codés de l'interface utilisateur incluent la prise en charge d'une partie des contrôles HTML5 inclus dans Internet Explorer 9 et Internet Explorer 10. Pour plus d’informations, consultez [Utilisation de contrôles HTML5 dans des tests codés de l’interface utilisateur](../test/using-html5-controls-in-coded-ui-tests.md).

    - Aide au codage des tests codés de l'interface utilisateur :

       - [Anatomie d’un test codé de l’interface utilisateur](../test/anatomy-of-a-coded-ui-test.md)

       - [Bonnes pratiques pour les tests codés de l’interface utilisateur](../test/best-practices-for-coded-ui-tests.md)

       - [Test d’une grande application avec plusieurs mappages d’IU](../test/testing-a-large-application-with-multiple-ui-maps.md)

       - [Plateformes et configurations prises en charge pour les tests codés de l’interface utilisateur et les enregistrements des actions](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)

### <a name="the-generated-code"></a>Code généré

Quand vous choisissez **Générer le code**, plusieurs segments de code sont créés :

- **Une ligne dans la méthode de test.**

    ```csharp
    [CodedUITest]
    public class CodedUITest1
    { ...
      [TestMethod]
      public void CodedUITestMethod1()
      {
          this.UIMap.AddTwoNumbers();
          // To generate more code for this test, select
          // "Generate Code" from the shortcut menu.      }
    }
    ```

     Vous pouvez cliquer avec le bouton droit dans cette méthode pour ajouter d'autres actions et vérifications enregistrées. Vous pouvez aussi la modifier manuellement pour étendre ou modifier le code. Vous pouvez par exemple englober une partie du code dans une boucle.

     Vous pouvez également ajouter de nouvelles méthodes de test et y ajouter du code de la même façon. Chaque méthode de test doit avoir l'attribut `[TestMethod]`.

- **Une méthode dans UIMap.uitest**

     Cette méthode comprend les détails des actions que vous avez enregistrées ou la valeur que vous avez vérifiée. Vous pouvez modifier ce code en ouvrant le fichier UIMap.uitest. Il s'ouvre dans un éditeur spécial dans lequel vous pouvez supprimer ou refactoriser les actions enregistrées.

     Vous pouvez aussi afficher la méthode générée dans UIMap.Designer.cs. Cette méthode effectue les actions que vous avez enregistrées lors de l'exécution du test.

    ```csharp
    // File: UIMap.Designer.cs
    public partial class UIMap
    {
      /// <summary>
      /// Add two numbers
      /// </summary>
      public void AddTwoNumbers()
      { ...   }
    }
    ```

    > [!WARNING]
    > Vous ne devez pas modifier ce fichier, car il sera regénéré quand vous créerez d'autres tests.

     Vous pouvez créer des versions adaptées de ces méthodes en les copiant dans *UIMap.cs*. Vous pouvez par exemple créer une version paramétrée que vous pourriez appeler depuis une méthode de test :

    ```csharp
    // File: UIMap.cs
    public partial class UIMap // Same partial class
    {
      /// <summary>
      /// Add two numbers - parameterized version
      /// </summary>
      public void AddTwoNumbers(int firstNumber, int secondNumber)
      { ...   // Code modified to use parameters.
      }
    }
    ```

- **Déclarations dans UIMap.uitest**

    Ces déclarations représentent les contrôles d'interface utilisateur de l'application utilisés par votre test. Elles sont utilisées par le code généré pour exécuter les contrôles et accéder à leurs propriétés.

    Vous pouvez aussi les utiliser si vous écrivez votre propre code. Vous pouvez par exemple faire en sorte que votre méthode de test choisisse un lien hypertexte dans une application web, entre une valeur dans une zone de texte ou bifurque et exécute différentes actions de test en fonction de la valeur d'un champ.

    Vous pouvez ajouter plusieurs tests codés de l'interface utilisateur et plusieurs objets et fichiers de mappage d'IU pour faciliter le test d'une grande application. Pour plus d’informations, consultez [Test d’une grande application avec plusieurs mappages d’IU](../test/testing-a-large-application-with-multiple-ui-maps.md).

Pour plus d’informations sur le code généré, consultez [Anatomie d’un test codé de l’interface utilisateur](../test/anatomy-of-a-coded-ui-test.md).

### <a name="code-ui-control-actions-and-properties"></a>Coder des actions et des propriétés des contrôles de l’interface utilisateur

Quand vous utilisez des contrôles de test de l'interface utilisateur dans des tests codés de l'interface utilisateur, ils sont séparés en deux catégories : actions et propriétés.

- La première catégorie est constituée d'actions que vous pouvez effectuer sur des contrôles de test de l'interface utilisateur. Par exemple, les tests codés de l'interface utilisateur peuvent simuler des clics de souris sur un contrôle de test de l'interface utilisateur ou simuler des frappes sur des touches du clavier pour affecter un contrôle de test de l'interface utilisateur.

- La seconde catégorie vous permet d'obtenir et de définir des propriétés sur un contrôle de test de l'interface utilisateur. Par exemple, les tests codés de l'interface utilisateur peuvent obtenir le nombre d'éléments d'un contrôle `ListBox` ou définir un contrôle `CheckBox` à l'état sélectionné.

**Accès aux actions d’un contrôle de test de l’interface utilisateur**

Pour effectuer des actions sur des contrôles de test de l'interface utilisateur, telles que des clics de souris ou des actions au clavier, utilisez les méthodes des classes <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse> et <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard> :

- Pour effectuer une action orientée souris (telle qu'un clic) sur un contrôle de test de l'interface utilisateur, utilisez <xref:Microsoft.VisualStudio.TestTools.UITesting.Mouse.Click%2A>.

     `Mouse.Click(buttonCancel);`

- Pour effectuer une action orientée clavier, telle que l'entrée dans un contrôle d'édition, utilisez <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard.SendKeys%2A>.

     `Keyboard.SendKeys(textBoxDestination, @"C:\Temp\Output.txt");`

**Accès aux propriétés d’un contrôle de test de l’interface utilisateur**

Pour obtenir et définir des valeurs de propriétés spécifiques à un contrôle d'interface utilisateur, vous pouvez obtenir et définir directement les valeurs des propriétés d'un contrôle ou utiliser les méthodes <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A?displayProperty=fullName> et <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A?displayProperty=fullName> avec le nom de la propriété spécifique que vous souhaitez obtenir ou définir.

<xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> retourne un objet qui peut être converti en <xref:System.Type> approprié. <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A> accepte un objet pour la valeur de la propriété.

#### <a name="to-get-or-set-properties-from-ui-test-controls-directly"></a>Pour obtenir ou définir des propriétés directement à partir de contrôles de test d'interface utilisateur

Avec les contrôles qui dérivent de <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl>, tel que [HtmlList](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.uitesting.htmlcontrols.htmllist.aspx) ou [WinComboBox](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.uitesting.wincontrols.wincombobox.aspx), vous pouvez obtenir ou définir directement les valeurs de leurs propriétés. Le code suivant montre des exemples :

 ```csharp
 int i = myHtmlList.ItemCount;
 myWinCheckBox.Checked = true;
 ```

#### <a name="to-get-properties-from-ui-test-controls"></a>Pour obtenir des propriétés à partir de contrôles de test d'interface utilisateur

- Pour obtenir une valeur de propriété à partir d'un contrôle, utilisez <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>.

- Pour spécifier la propriété du contrôle à obtenir, utilisez la chaîne appropriée de la classe `PropertyNames` dans chaque contrôle comme paramètre de <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A>.

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.GetProperty%2A> retourne le type de données approprié, mais cette valeur de retour est convertie en <xref:System.Object>. L'objet <xref:System.Object> retourné doit ensuite être converti en type approprié.

     Exemple :

     `int i = (int)GetProperty(myHtmlList.PropertyNames.ItemCount);`

#### <a name="to-set-properties-for-ui-test-controls"></a>Pour définir des propriétés pour des contrôles de test d'interface utilisateur

- Pour définir une propriété dans un contrôle, utilisez <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>.

- Pour spécifier la propriété du contrôle à définir, utilisez la chaîne appropriée de la classe `PropertyNames` comme premier paramètre de <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.SetProperty%2A>, avec la valeur de propriété comme second paramètre.

     Exemple :

     `SetProperty(myWinCheckBox.PropertyNames.Checked, true);`

### <a name="debug"></a>Débogage

Vous pouvez analyser les tests codés de l'interface utilisateur à l'aide de journaux de tests codés de l'interface utilisateur. Les journaux de tests codés de l'interface utilisateur filtrent et enregistrent des informations importantes sur l'exécution de vos tests codés de l'interface utilisateur. Le format des journaux vous permet de déboguer les problèmes rapidement. Pour plus d’informations, consultez [Analyse des tests codés de l’interface utilisateur à l’aide des journaux de test codé de l’interface utilisateur](../test/analyzing-coded-ui-tests-using-coded-ui-test-logs.md).

## <a name="whats-next"></a>Étapes suivantes

**Options supplémentaires pour l’exécution des tests codés de l’interface utilisateur :** vous pouvez exécuter des tests codés de l’interface utilisateur directement à partir de Visual Studio, comme décrit plus haut dans cette rubrique. Vous pouvez également exécuter des tests d’interface utilisateur automatisés à partir de Microsoft Test Manager ou de Team Foundation Build. Quand les tests codés de l'interface utilisateur sont automatisés, ils doivent interagir avec le Bureau lorsque vous les exécutez, contrairement aux autres tests automatisés.

- [Exécuter des tests unitaires avec l’Explorateur de tests](../test/run-unit-tests-with-test-explorer.md)

- [Exécuter des tests dans votre processus de génération](/vsts/build-release/test/getting-started-with-continuous-testing)

- [Guide pratique pour configurer votre agent de test pour exécuter des tests qui interagissent avec le Bureau](http://msdn.microsoft.com/Library/3a94dd07-6d17-402c-ae8f-7947143755c9)

**Ajout de la prise en charge des contrôles personnalisés :** le framework des tests codés de l’interface utilisateur ne prend pas en charge chaque IU possible et ne prend pas nécessairement en charge l’IU que vous souhaitez tester. Par exemple, vous ne pouvez pas créer immédiatement de test codé de l'interface utilisateur de l'IU de Microsoft Excel. Toutefois, vous pouvez créer une extension au framework de tests codés de l’interface utilisateur qui prendra en charge un contrôle personnalisé.

- [Activer le test codé de l’interface utilisateur de vos contrôles](../test/enable-coded-ui-testing-of-your-controls.md)

- [Extension des tests codés de l’interface utilisateur et des enregistrements des actions pour prendre charge Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

Les tests codés de l'interface utilisateur servent souvent à automatiser des tests manuels. Pour plus d’informations sur les tests manuels, consultez [Exécuter des tests manuels avec Microsoft Test Manager](/vsts/manual-test/mtm/run-manual-tests-with-microsoft-test-manager). Pour plus d’informations sur les tests automatisés, consultez [Outils de test dans Visual Studio](../test/improve-code-quality.md).

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>
- [Améliorer la qualité du code](../test/improve-code-quality.md)
- [Procédures pas à pas : création, édition et gestion d’un test codé de l’interface utilisateur](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
- [Anatomie d’un test codé de l’interface utilisateur](../test/anatomy-of-a-coded-ui-test.md)
- [Bonnes pratiques pour les tests codés de l’interface utilisateur](../test/best-practices-for-coded-ui-tests.md)
- [Test d’une grande application avec plusieurs mappages d’IU](../test/testing-a-large-application-with-multiple-ui-maps.md)
- [Modification des tests codés de l’interface utilisateur à l’aide de l’éditeur de test codé de l’interface utilisateur](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)
- [Plateformes et configurations prises en charge pour les tests codés de l’interface utilisateur et les enregistrements des actions](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Mise à niveau de tests codés de l’interface utilisateur à partir de Visual Studio 2010](../test/upgrading-coded-ui-tests-from-visual-studio-2010.md)
