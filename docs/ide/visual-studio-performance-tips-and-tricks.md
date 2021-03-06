---
title: Conseils et astuces sur les performances dans Visual Studio
ms.date: 08/31/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 2fbcb59e-e981-4b40-8b7a-c1140d31ec4b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ec6563086968cb84c0ad2177d5a1c13e051012cf
ms.sourcegitcommit: a8e01952be5a539104e2c599e9b8945322118055
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="visual-studio-performance-tips-and-tricks"></a>Conseils et astuces sur les performances dans Visual Studio

Les recommandations pour améliorer les performances de Visual Studio concernent les cas où la mémoire est insuffisante, ce qui se produit rarement. Dans ces situations, vous pouvez optimiser certaines fonctionnalités de Visual Studio que vous n’utilisez peut-être pas. Les conseils suivants ne sont pas à interpréter comme des recommandations générales.

> [!NOTE]
> Si vous rencontrez des difficultés à utiliser le produit en raison de problèmes de mémoire, faites-le nous savoir via [l’outil de commentaires](../ide/how-to-report-a-problem-with-visual-studio-2017.md).

## <a name="optimize-your-environment"></a>Optimiser votre environnement

- **Utiliser un système d’exploitation 64 bits**

    Si vous mettez à niveau votre système d’une version 32 bits de Windows vers une version 64 bits, vous passez de 2 Go à 4 Go la quantité de mémoire virtuelle disponible pour Visual Studio. Cela permet à Visual Studio de gérer des charges de travail beaucoup plus importantes, même avec un processus 32 bits.

    Pour plus d’informations, consultez [Limites de mémoire](https://msdn.microsoft.com/library/windows/desktop/aa366778(v=vs.85).aspx#memory_limits) et [Use /LARGEADDRESSAWARE on 64-bit Windows](https://blogs.msdn.microsoft.com/oldnewthing/20050601-24/?p=35483/).

## <a name="configure-solution-and-projects"></a>Configurer des solutions et des projets

Si votre solution est très volumineuse et contient de nombreux projets, vous pouvez apporter les optimisations suivantes :

- **Déchargement de projets**

    Vous pouvez décharger manuellement les projets individuels rarement utilisés à partir de **l’Explorateur de solutions** à l’aide du menu contextuel.

- **Refactoriser la solution**

    Vous pouvez fractionner votre solution en plusieurs petits fichiers solution dans les projets couramment utilisés. Cette refactorisation doit réduire considérablement l’utilisation de mémoire pour votre flux de travail. Les solutions plus petites se chargent également plus vite.

## <a name="configure-debugging-options"></a>Configurer les options de débogage

En règle générale, si vous manquez de mémoire pendant le débogage des sessions, vous pouvez optimiser les performances en modifiant un peu la configuration.

- **Activer Uniquement mon code**

    L’optimisation la plus simple consiste à activer la fonctionnalité **Uniquement mon code**, qui charge uniquement des symboles pour votre projet. L’activation de cette fonctionnalité peut contribuer à économiser considérablement la mémoire pour le débogage des applications managées (.NET). Cette option est déjà activée par défaut dans certains types de projets.

    Pour activer **Uniquement mon code**, choisissez **Outils** > **Options** > **Débogage** > **Général**, puis sélectionnez **Activer Uniquement mon code**.

- **Spécifier les symboles à charger**

    Pour le débogage natif, le chargement des fichiers de symboles (*.pdb*) consomme beaucoup de ressources mémoire. Vous pouvez configurer les paramètres de symboles de votre débogueur pour économiser la mémoire. En règle générale, vous configurez la solution pour charger uniquement les modules de votre projet.

    Pour spécifier le chargement des symboles, choisissez **Outils** > **Options** > **Débogage** > **Symboles**.

    Définissez les options sur **Uniquement les modules spécifiés** au lieu de **Tous les modules**, puis spécifiez les modules que vous voulez charger. Pendant le débogage, vous pouvez également cliquer avec le bouton droit sur des modules spécifiques dans la fenêtre **Modules** pour inclure explicitement un module dans le chargement de symboles. (Pour ouvrir la fenêtre pendant le débogage, choisissez **Déboguer** > **Fenêtres** > **Modules**.)

    Pour plus d’informations, consultez [Présentation des fichiers de symboles](https://blogs.msdn.microsoft.com/visualstudioalm/2015/01/05/understanding-symbol-files-and-visual-studios-symbol-settings/).

- **Désactiver les outils de diagnostic**

    Nous vous recommandons de désactiver le profilage de l’UC après utilisation. Cette fonctionnalité peut consommer de grandes quantités de ressources. Une fois que le profilage de l’UC est activé, cet état est conservé dans les sessions de débogage suivantes, il est donc recommandé de le désactiver explicitement une fois terminé. Vous pouvez économiser des ressources en désactivant les outils de diagnostic pendant le débogage si vous n’avez pas besoin des fonctionnalités fournies.

    Pour désactiver les **Outils de diagnostic**, démarrez une session de débogage, choisissez **Outils** > **Options** > **Activer les outils de diagnostic** et désélectionnez l’option.

    Pour plus d’informations, consultez [Outils de profilage](../profiling/profiling-tools.md).

## <a name="disable-tools-and-extensions"></a>Désactiver des outils et des extensions

Certains outils ou extensions peuvent être désactivés pour améliorer les performances.

> [!TIP]
> Vous pouvez souvent isoler les problèmes de performances en désactivant une par une les extensions et en revérifiant les performances.

### <a name="managed-language-services-roslyn"></a>Services de langage gérés (Roslyn)

Pour plus d’informations sur les performances de .NET Compiler Platform (« Roslyn »), consultez [Performance considerations for large solutions](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

- **Désactiver l’analyse complète de la solution**

    Visual Studio analyse l’ensemble de votre solution afin d’offrir une expérience complète sur les erreurs avant d’appeler une génération. Cette fonctionnalité est utile pour identifier les erreurs dès que possible. Toutefois, pour les solutions très volumineuses, cette fonctionnalité peut consommer des ressources de mémoire considérables. Si vous rencontrez des problèmes de mémoire ou du même type, vous pouvez désactiver cette expérience pour libérer ces ressources. Par défaut, cette option est activée pour Visual Basic et désactivée pour C#.

    Pour désactiver **Analyse complète de la solution**, choisissez **Outils** > **Options** > **Éditeur de texte** > **<Visual Basic ou C#>**. Ensuite, choisissez **Avancé** et décochez **Activer l’analyse complète de la solution**.

- **Désactiver CodeLens**

    Visual Studio effectue une tâche **Rechercher toutes les références** sur chaque méthode qui s’affiche. CodeLens fournit des fonctionnalités comme l’affichage en ligne du nombre de références. Le travail est exécuté dans un processus distinct (par exemple, *ServiceHub.RoslynCodeAnalysisService32*). Dans les solutions très volumineuses ou sur des systèmes limités en ressources, cette fonctionnalité peut avoir un impact significatif sur les performances, même si elle est exécutée avec une priorité basse. Si ce processus utilise une grande partie de l’UC ou que vous rencontrez des problèmes de mémoire (par exemple, quand vous chargez une solution volumineuse sur un ordinateur de 4 Go), vous pouvez essayer de désactiver cette fonctionnalité pour libérer des ressources.

    Pour désactiver **CodeLens**, choisissez **Outils** > **Options** > **Éditeur de texte** > **Tous les langages** > **CodeLens** et désélectionnez la fonctionnalité.

    Cette fonctionnalité est disponible dans Visual Studio Enterprise et Visual Studio Professional.

### <a name="other-tools-and-extensions"></a>Autres outils et extensions

- **Désactiver des extensions**

    Les extensions sont des composants logiciels supplémentaires ajoutés à Visual Studio qui fournissent de nouvelles fonctionnalités ou étendent les fonctionnalités existantes. Les extensions peuvent souvent être une source de problèmes de ressources mémoire. Si vous rencontrez des problèmes de ressources mémoire, essayez de désactiver les extensions une par une pour connaître leur impact sur le scénario ou le flux de travail.

    Pour désactiver des extensions, accédez à **Outils** > **Extensions et mises à jour** et désactivez une extension particulière.

- **Désactiver le concepteur XAML**

    Le concepteur XAML est activé par défaut, mais consomme des ressources seulement si vous ouvrez un fichier *.xaml*. Si vous utilisez des fichiers XAML, mais ne voulez pas utiliser les fonctionnalités du concepteur, désactivez cette fonctionnalité pour libérer de la mémoire.

    Pour désactiver le **concepteur XAML**, accédez à **Outils** > **Options** > **Concepteur XAML** > **Activer le concepteur XAML** et désélectionnez l’option.

- **Supprimer des charges de travail**

    Vous pouvez utiliser Visual Studio Installer pour supprimer des charges de travail qui ne sont plus utilisées. Cette action permet de rationaliser le coût du démarrage et de l’exécution en ignorant les packages et les assemblys qui ne sont plus nécessaires.

## <a name="force-a-garbage-collection"></a>Forcer une opération de garbage collection

Le CLR utilise un système de gestion de mémoire garbage collection. Dans ce système, la mémoire est parfois utilisée par des objets qui ne sont plus nécessaires. Cet état est temporaire. Le récupérateur de mémoire libère cette mémoire en fonction de ses méthodes heuristiques en matière d’utilisation des ressources et de performances. Vous pouvez obliger le CLR à collecter la mémoire inutilisée à l’aide d’un raccourci clavier dans Visual Studio. Si une quantité importante de mémoire est en attente de nettoyage et que vous forcez une opération de garbage collection, vous devez voir chuter l’utilisation de la mémoire par le processus *devenv.exe* dans le **Gestionnaire des tâches**. Cette méthode est rarement nécessaire. Toutefois, quand une opération ayant consommé beaucoup de ressources se termine (par exemple, une génération complète, une session de débogage ou un événement d’ouverture de solution), elle peut vous aider à déterminer la quantité de mémoire qui est réellement utilisée par le processus. Parce que Visual Studio est mixte (à la fois managé et natif), il est parfois possible que l’allocateur natif et le récupérateur de mémoire entrent en concurrence pour utiliser des ressources mémoire limitées. Dans les situations d’utilisation importante de la mémoire, il peut être utile de forcer l’exécution du récupérateur de mémoire.

Pour forcer une opération de garbage collection, utilisez la touche de raccourci : **Ctrl**+**Alt**+**Maj**+**F12**, **Ctrl**+**Alt**+**Maj**+**F12** (appuyez dessus deux fois).

Si le forçage de l’opération de garbage collection permet à votre scénario de fonctionner de manière fiable, envoyez un rapport à travers l’outil de commentaires de Visual Studio, car ce comportement est susceptible d’être un bogue.

Pour obtenir une description détaillée du récupérateur de mémoire CLR, consultez [Concepts fondamentaux de l’opération de garbage collection](/dotnet/standard/garbage-collection/fundamentals).

## <a name="see-also"></a>Voir aussi

- [Optimiser les performances de Visual Studio](../ide/optimize-visual-studio-performance.md)
- [Visual Studio blog - Load solutions faster with Visual Studio 2017 version 15.6](https://blogs.msdn.microsoft.com/visualstudio/2018/04/04/load-solutions-faster-with-visual-studio-2017-version-15-6/)