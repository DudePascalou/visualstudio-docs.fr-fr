---
title: Référence de schéma 2.0 Extension VSIX | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7459b4292220e6bb1e5a00b912efe7eb99cce825
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="vsix-extension-schema-20-reference"></a>Référence de schéma 2.0 Extension VSIX
Un fichier de manifeste de déploiement VSIX décrit le contenu d’un package VSIX. Le format de fichier est régi par un schéma. La version 2.0 de ce schéma prend en charge l’ajout d’attributs et types personnalisés.  Le schéma du manifeste est extensible. Le chargeur de manifeste ignore les éléments et attributs qui ne comprend pas XML.  
  
> [!IMPORTANT]
>  Visual Studio 2015 peut charger des fichiers VSIX dans les formats de Visual Studio 2010, Visual Studio 2012 ou Visual Studio 2013.  
  
## <a name="package-manifest-schema"></a>Schéma de manifeste de package  
 L’élément racine du fichier XML manifeste est `<PackageManifest>`, avec un seul attribut `Version`, qui est la version du format de manifeste. Si des modifications majeures sont apportées au format, le format de version changera. Cette rubrique décrit le format de manifeste version 2.0, qui est spécifiée dans le manifeste en définissant le `Version` à la Version de la valeur d’attribut = « 2.0 ».  
  
### <a name="packagemanifest-element"></a>Élément PackageManifest  
 Dans la `<PackageManifest>` élément racine, vous pouvez utiliser les éléments suivants :  
  
-   `<Metadata>` -Les métadonnées et la publicité plus d’informations sur le package lui-même. Seul `Metadata` élément est autorisé dans le manifeste.  
  
-   `<Installation>` – Cette section définit la manière de dans que ce package d’extension peut être installé, y compris les références d’application qui peuvent être installées. Un seul `Installation` élément est autorisé dans le manifeste. Un manifeste doit avoir un `Installation` élément ou ce package ne s’installe pas dans une référence.  
  
-   `<Dependencies>` -Une liste facultative de dépendances pour ce package sont définies ici.  
  
-   `<Assets>` -Cette section contient toutes les ressources contenues dans ce package. Sans cette section, ce package ne sera pas surface aucun contenu.  
  
-   `<AnyElement>*` -Le schéma de manifeste est suffisamment flexible pour permettre à d’autres éléments. Tous les éléments enfants non reconnus par le chargeur de manifeste sont exposés dans l’API du Gestionnaire d’extensions en tant qu’objets XmlElement supplémentaires. À l’aide de ces éléments enfants, les extensions VSIX peuvent définir des données supplémentaires dans le fichier manifeste accessible par code en cours d’exécution dans Visual Studio lors de l’exécution. Consultez <xref:Microsoft.VisualStudio.ExtensionManager.IExtension.AdditionalElements%2A> et <xref:Microsoft.VisualStudio.ExtensionManager.IExtension.LocalizedAdditionalElements%2A>.  
  
### <a name="metadata-element"></a>Élément de métadonnées  
 Cette section est les métadonnées sur le package, son identité et les informations. `<Metadata>` contient les éléments suivants :  
  
-   `<Identity>` -Ceci définit les informations d’identification pour ce package et inclut les attributs suivants :  
  
    -   `Id` -Cet attribut doit être un ID unique pour le package choisi par son auteur. Le nom doit être qualifié de la même façon que les types CLR sont namespaced : Company.Product.Feature.Name. Le `Id` attribut est limité à 100 caractères.  
  
    -   `Version` -Définit la version de ce package et son contenu. Cet attribut suit le format de contrôle de version d’assembly CLR : Major.Minor.Build.Revision (1.2.40308.00). Un package avec un numéro de version supérieur est considérée comme des mises à jour le package et peut être installé sur la version installée existante.  
  
    -   `Language` -Cet attribut est la langue par défaut pour le package et correspond à des données textuelles de ce manifeste. Cet attribut suit la convention de code CLR aux paramètres régionaux pour les assemblys de ressources, par exemple : en-us, fr, fr-fr. Vous pouvez spécifier `neutral` pour déclarer une extension indépendante du langage qui s’exécute sur n’importe quelle version de Visual Studio. La valeur par défaut est `neutral`.  
  
    -   `Publisher` -Cet attribut identifie le serveur de publication de ce package, une société ou le nom individuel. Le `Publisher` attribut est limité à 100 caractères.  
  
-   `<DisplayName>` -Cet élément spécifie le nom du package convivial qui s’affiche dans le Gestionnaire d’extensions UI. Le `DisplayName` contenu est limité à 50 caractères.  
  
-   `<Description>` -Cet élément facultatif est une brève description du package et de son contenu est affichée dans le Gestionnaire d’extensions UI. Le `Description` contenu peut contenir n’importe quel texte que vous le souhaitez, mais il a limité à 1000 caractères.  
  
-   `<MoreInfo>` -Cet élément facultatif est une URL vers une page en ligne qui contient une description complète de ce package. Le protocole doit être spécifié en tant que http.  
  
-   `<License>` -Cet élément facultatif est un chemin d’accès relatif à un fichier de licence (.txt, .rtf) contenu dans le package.  
  
-   `<ReleaseNotes>` -Cet élément facultatif est un chemin d’accès relatif à un fichier de notes de version contenu dans le package (.txt, .rtf) ou bien une URL vers un site Web qui affiche les notes de publication.  
  
-   `<Icon>` -Cet élément facultatif est un chemin d’accès relatif vers un fichier image (png, bmp, jpeg, ico) contenu dans le package. L’image d’icône doit être de 32 x 32 pixels (ou sera réduite à cette taille) et s’affiche dans l’interface utilisateur de listview. Si aucun `Icon` élément est spécifié, l’interface utilisateur utilise la valeur par défaut.  
  
-   `<PreviewImage>` -Cet élément facultatif est un chemin d’accès relatif vers un fichier image (png, bmp, jpeg) contenu dans le package. L’image d’aperçu doit être de 200 x 200 pixels et affiché dans les détails de l’interface utilisateur. Si aucun `PreviewImage` élément est spécifié, l’interface utilisateur utilise la valeur par défaut.  
  
-   `<Tags>` -Cet élément facultatif répertorie les balises de texte délimitée par des points-virgules qui sont utilisées pour les indicateurs de recherche. Le `Tags` est limitée à 100 caractères.  
  
-   `<GettingStartedGuide>` -Cet élément facultatif est un chemin d’accès relatif à un fichier HTML ou une URL vers un site Web qui contient des informations sur l’utilisation de l’extension ou le contenu de ce package. Ce guide est lancé dans le cadre d’une installation.  
  
-   `<AnyElement>*` -Le schéma de manifeste est suffisamment flexible pour permettre à d’autres éléments. Tous les éléments enfants qui ne sont pas reconnus par le chargeur de manifeste sont exposés en tant que liste d’objets XmlElement. À l’aide de ces éléments enfants, les extensions VSIX peuvent définissent des données supplémentaires dans le fichier manifeste et les énumérer lors de l’exécution.  
  
### <a name="installation-element"></a>Élément d’installation  
 Cette section définit la façon de que ce package peut être installé et les références de l’application que vous pouvez l’installer dans. Cette section contient les attributs suivants :  
  
-   `Experimental` -Définissez cet attribut sur « True » si vous disposez d’une extension qui est actuellement installée pour tous les utilisateurs, mais que vous développez une version mise à jour sur le même ordinateur. Par exemple, si vous avez installé MyExtension 1.0 pour tous les utilisateurs, mais que vous souhaitez déboguer MyExtension 2.0 sur le même ordinateur, définissez expérimental = « true ». Cet attribut est disponible dans Visual Studio 2015 Update 1 et versions ultérieures.  
  
-   `Scope` -Cet attribut peut prendre la valeur « Global » ou « ProductExtension » :  
  
    -   « Globaux » Spécifie que l’installation ne s’étend pas à une référence (SKU) spécifique. Par exemple, cette valeur est utilisée lorsqu’un SDK d’Extension est installé.  
  
    -   « ProductExtension » Spécifie qu’une Extension VSIX traditionnel (version 1.0) limitées à des références SKU de Visual Studio est installée. Valeur par défaut.  
  
-   `AllUsers` -Cet attribut facultatif indique si ce package doit être installé pour tous les utilisateurs. Par défaut, cet attribut est false, ce qui indique que le package ne par utilisateur. (Lorsque vous définissez cette valeur sur true, l’utilisateur lors de l’installation doit élever au niveau de privilèges d’administrateur pour installer l’extension VSIX qui en résulte.  
  
-   `InstalledByMsi` -Cet attribut facultatif indique si ce package est installé par un fichier MSI. Packages installés par un fichier MSI sont installés et gérés par MSI (programmes et fonctionnalités) et non par Visual Studio Extension Manager.  Par défaut, cet attribut est false, ce qui indique que le package n’est pas installé par un fichier MSI.  
  
-   `SystemComponent` -Cet attribut facultatif indique si ce package doit être considéré comme un composant du système. Composants du système de ne pas afficher dans le Gestionnaire d’extensions UI et ne peut pas être mis à jour. Par défaut, cet attribut est false, ce qui indique que le package n’est pas un composant du système.  
  
-   `AnyAttribute*` -La `Installation` élément accepte un ensemble extensible d’attributs qui seront exposées lors de l’exécution en tant qu’un dictionnaire de paires nom-valeur.  
  
-   `<InstallationTarget>` -Cet élément contrôle l’emplacement où le programme d’installation VSIX installe le package. Si la valeur de la `Scope` attribut est « ProductExtension », le package doit cibler une référence (SKU) qui a installé un fichier manifeste dans le cadre de son contenu pour annoncer sa disponibilité aux extensions. Le `<InstallationTarget>` élément possède les éléments suivants lorsque des attributs le `Scope` attribut a explicite ou par défaut « ProductExtension » :  
  
    -   `Id` -Cet attribut identifie le package.  L’attribut suit la convention d’espace de noms : Company.Product.Feature.Name. Le `Id` attribut peut contenir uniquement des caractères alphanumériques et est limité à 100 caractères. Valeurs attendues :  
  
        -   Microsoft.VisualStudio.IntegratedShell  
  
        -   Microsoft.VisualStudio.Pro  
  
        -   Microsoft.VisualStudio.Premium  
  
        -   Microsoft.VisualStudio.Ultimate  
  
        -   Microsoft.VisualStudio.VWDExpress  
  
        -   Microsoft.VisualStudio.VPDExpress  
  
        -   Microsoft.VisualStudio.VSWinExpress  
  
        -   Microsoft.VisualStudio.VSLS  
  
        -   My.Shell.App  
  
    -   `Version` -Cet attribut spécifie une plage de versions avec les versions prises en charge minimales et maximales de cette référence SKU. Un package peut décrit en détail les versions de références SKU pris en charge. La notation de plage de version est [10.0-11.0], où  
  
        -   [-version minimale incluse.  
  
        -   ]-version maximale inclus.  
  
        -   (-version minimale exclusive.  
  
        -   )-version maximale exclusif.  
  
        -   Version unique # - uniquement la version spécifiée.  
  
        > [!IMPORTANT]
        >  La version 2.0 du schéma VSIX a été introduite dans Visual Studio 2012. Pour utiliser ce schéma vous devez disposer de Visual Studio 2012 ou version ultérieure installé sur l’ordinateur et utilisez le VSIXInstaller.exe qui fait partie de ce produit. Vous pouvez cibler des versions antérieures de Visual Studio avec un Visual Studio 2012 ou d’un VSIXInstaller ultérieure, mais uniquement en utilisant les versions ultérieures du programme d’installation.  
  
    -   `AnyAttribute*` -La `<InstallationTarget>` élément permet un ensemble extensible d’attributs que vous allez être exposés au runtime en tant que paire nom-valeur dictionnaire.  
  
### <a name="dependencies-element"></a>Élément de dépendances  
 Cet élément contient une liste de dépendances qui déclare de ce package. Si toutes les dépendances sont spécifiés, ces packages (identifiés par leurs `Id`) doit être installé avant.  
  
-   `<Dependency>` élément - cet élément enfant a les attributs suivants :  
  
    -   `Id` -Cet attribut doit être un ID unique pour le package dépendant. Cette valeur d’identité doit correspondre à la `<Metadata><Identity>Id` attribut d’un package dont dépend ce package. Le `Id` attribut suit la convention d’espace de noms : Company.Product.Feature.Name. L’attribut peut contenir uniquement des caractères alphanumériques et est limité à 100 caractères.  
  
    -   `Version` -Cet attribut spécifie une plage de versions avec les versions prises en charge minimales et maximales de cette référence SKU. Un package peut décrit en détail les versions de références SKU pris en charge. La notation de plage de version est [12.0, 13.0], où :  
  
        -   [-version minimale incluse.  
  
        -   ]-version maximale inclus.  
  
        -   (-version minimale exclusive.  
  
        -   )-version maximale exclusif.  
  
        -   Version unique # - uniquement la version spécifiée.  
  
    -   `DisplayName` -Cet attribut est le nom complet du package dépendant qui est utilisé dans les éléments d’interface utilisateur tels que les boîtes de dialogue et les messages d’erreur. L’attribut est facultatif, sauf si le package dépendant est installé par MSI.  
  
    -   `Location` -Cet attribut facultatif spécifie le chemin d’accès relatif au sein de cet extension VSIX à un package VSIX imbriqué ou une URL vers l’emplacement de téléchargement de la dépendance. Cet attribut est utilisé pour aider l’utilisateur à rechercher le package requis.  
  
    -   `AnyAttribute*` -La `Dependency` élément accepte un ensemble extensible d’attributs qui seront exposées lors de l’exécution en tant qu’un dictionnaire de paires nom-valeur.  
  
### <a name="assets-element"></a>Élément de ressources  
 Cet élément contient une liste de `<Asset>` étiquettes pour chaque élément d’extension ou contenu exposés par ce package.  
  
-   `<Asset>` -Cet élément contient les attributs et les éléments suivants :  
  
    -   `Type` -C’est le type d’extension ou de contenu représenté par cet élément. Chaque `<Asset>` l’élément doit avoir un seul `Type`, mais plusieurs `<Asset>` éléments peuvent avoir le même `Type`. Cet attribut doit être représenté comme un nom qualifié complet, selon les conventions de l’espace de noms. Les types connus sont :  
  
        1.  Microsoft.VisualStudio.VsPackage  
  
        2.  Microsoft.VisualStudio.MefComponent  
  
        3.  Microsoft.VisualStudio.ToolboxControl  
  
        4.  Microsoft.VisualStudio.Samples  
  
        5.  Microsoft.VisualStudio.ProjectTemplate  
  
        6.  Microsoft.VisualStudio.ItemTemplate  
  
        7.  Microsoft.VisualStudio.Assembly  
  
         Vous pouvez créer vos propres types et leur attribuer des noms uniques. Au moment de l’exécution à l’intérieur de Visual Studio, votre code peut énumérer et accéder à ces types personnalisés via l’API du Gestionnaire d’extensions.  
  
    -   Chemin d’accès - le chemin d’accès relatif au fichier ou dossier dans le package qui contient l’élément multimédia.  
  
    -   `AnyAttribute*` -Un durée indéterminée ensemble d’attributs que vous allez être exposés au runtime comme un dictionnaire de paires nom-valeur.  
  
         `<AnyElement>*` -N’importe quel contenu structuré est autorisé entre un `<Asset>` commencer et la balise de fin. Tous les éléments sont exposés en tant que liste d’objets XmlElement. Les extensions VSIX peuvent définir les métadonnées spécifiques au type structurée dans le fichier manifeste et les énumérer lors de l’exécution.  
  
### <a name="sample-manifest"></a>Manifeste de l’exemple  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">  
  <Metadata>  
    <Identity Id="0000000-0000-0000-0000-000000000000" Version="1.0" Language="en-US" Publisher="Company" />  
    <DisplayName>Test Package</DisplayName>  
    <Description>Information about my package</Description>  
    <MoreInfo>http://www.fabrikam.com/Extension1/</MoreInfo>  
    <License>eula.rtf</License>  
    <ReleaseNotes>notes.txt</ReleaseNotes>  
    <Icon>Images\icon.png</Icon>  
    <PreviewImage>Images\preview.png</PreviewImage>  
  </Metadata>  
  <Installation InstalledByMsi="false" AllUsers="false" SystemComponent="false" Scope="ProductExtension">  
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="[11.0, 12.0]" />  
  </Installation>  
  <Dependencies>  
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="[4.5,)" />  
    <Dependency Id="Microsoft.VisualStudio.MPF.12.0" DisplayName="Visual Studio MPF 12.0" d:Source="Installed" Version="[12.0]" />  
  </Dependencies>  
  <Assets>  
    <Asset Type="Microsoft.VisualStudio.VsPackage" d:Source="Project" d:ProjectName="%CurrentProject%" Path="|%CurrentProject%;PkgdefProjectOutputGroup|" />  
  </Assets>  
</PackageManifest>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Publication d’extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md)