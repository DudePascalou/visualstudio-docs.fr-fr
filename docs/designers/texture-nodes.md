---
title: "Nœuds de texture | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b7df5ef3-dd4f-4964-9d96-34e0e180515e
caps.latest.revision: 12
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 12
---
# Nœuds de texture
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans le Concepteur Shader, les nœuds de texture représentent différents types et géométries de texture et produisent ou transforment les coordonnées de texture.  Les textures fournissent des détails de couleurs et d'éclairage sur les objets.  
  
## Référence de nœud de texture  
  
|Nœud|Détails|Propriétés|  
|----------|-------------|----------------|  
|**Exemple de cubemap**|Prélève un exemple de couleur provenant d'une carte cubique au niveau des coordonnées spécifiées.<br /><br /> Vous pouvez utiliser une carte cubique pour fournir un détail de couleur pour les effets de reflet ou pour appliquer une texture à un objet sphérique avec moins de distorsion qu'une texture 2D.<br /><br /> **Entrée :**<br /><br /> `UVW`: `float3`<br /> Vecteur qui spécifie l'emplacement du cube de texture où l'échantillon est prélevé.  L'exemple est prélevé à l'endroit où le vecteur croise le cube.<br /><br /> **Sortie :**<br /><br /> `Output`: `float4`<br /> Échantillon de couleur.|**Texture**<br /> Registre de textures associé à l'échantillonneur.|  
|**Exemple de mappage de normales**|Prélève un exemple normal provenant d'une carte normale 2D au niveau des coordonnées spécifiées<br /><br /> Vous pouvez utiliser une carte normale pour simuler l'aspect d'un détail géométrique supplémentaire à la surface d'un objet.  Les cartes normales contiennent des données compressées qui représentent un vecteur unitaire plutôt que des données de couleur.<br /><br /> **Entrée :**<br /><br /> `UV`: `float2`<br /> Coordonnées d'où est prélevé l'exemple.<br /><br /> **Sortie :**<br /><br /> `Output`: `float3`<br /> Exemple normal.|**Réglage d'axe**<br /> Facteur utilisé pour ajuster la latéralisation gauche\/droite d'un échantillon de carte normale.<br /><br /> **Texture**<br /> Registre de textures associé à l'échantillonneur.|  
|**UV Panoramique**|Effectue un mouvement panoramique des coordonnées spécifiées de texture en fonction du temps.<br /><br /> Vous pouvez l'utiliser pour déplacer une carte de texture ou une carte normale à la surface d'un objet.<br /><br /> **Entrée :**<br /><br /> `UV`: `float2`<br /> Coordonnées auxquelles appliquer le panoramique.<br /><br /> `Time`: `float`<br /> La durée de panoramique en secondes.<br /><br /> **Sortie :**<br /><br /> `Output`: `float2`<br /> Coordonnées panoramiquées.|**Vitesse X**<br /> Nombre de texels panoramiqués le long de l'axe des abcisses, par seconde.<br /><br /> **Vitesse Y**<br /> Nombre de texels panoramiqués le long de l'axe des ordonnées, par seconde.|  
|**UV Parallax**|Déplace les coordonnées de texture spécifiées en tant que fonction de hauteur et d'angle de visualisation.<br /><br /> L'effet créé est connu sous le nom de *mappage parallaxe* ou de mappage de déplacement virtuel.  Vous pouvez l'utiliser pour créer une illusion de profondeur sur une surface plate.<br /><br /> **Entrée :**<br /><br /> `UV`: `float2`<br /> Coordonnées à déplacer.<br /><br /> `Height`: `float`<br /> La valeur de heightmap associée aux coordonnées `UV`.<br /><br /> **Sortie :**<br /><br /> `Output`: `float2`<br /> Les coordonnées déplacées.|**Plan de profondeur**<br /> Profondeur de référence pour l'effet parallaxe.  Par défaut, la valeur est 0,5.  Les valeurs basses relèvent la texture ; les valeurs élevées l'enfoncent dans la surface.<br /><br /> **Échelle de profondeur**<br /> L'échelle de l'effet parallaxe.  Cela accentue ou diminue la profondeur apparente.  Les valeurs standard sont comprises entre 0,02 et 0,1.|  
|**Faire pivoter UV**|Fait pivoter les coordonnées spécifiées de texture autour d'un point central en fonction du temps.<br /><br /> Vous pouvez l'utiliser pour faire tourner une carte de texture ou une carte normale à la surface d'un objet.<br /><br /> **Entrée :**<br /><br /> `UV`: `float2`<br /> Coordonnées à faire pivoter.<br /><br /> `Time`: `float`<br /> La durée de panoramique en secondes.<br /><br /> **Sortie :**<br /><br /> `Output`: `float2`<br /> Les coordonnées pivotées.|**Centrer X**<br /> Coordonnée x qui définit le centre de rotation.<br /><br /> **Centrer Y**<br /> Coordonnée y qui définit le centre de rotation.<br /><br /> **Vitesse**<br /> Angle, en radians, en fonction duquel la texture pivote chaque seconde.|  
|**Coordonnée de texture**|Coordonnées de texture du pixel actuel.<br /><br /> Les coordonnées de la texture sont déterminées par l'interpolation entre les attributs des coordonnées de la texture des sommets voisins.  Vous pouvez les considérer comme la position du pixel actuel dans l'espace de la texture.<br /><br /> **Sortie :**<br /><br /> `Output`: `float2`<br /> Coordonnées de texture.|None|  
|**Dimensions de la texture**|Calcule la largeur et la hauteur d'une carte de texture 2D.<br /><br /> Vous pouvez utiliser les dimensions de texture pour prendre en compte la largeur et la hauteur de la texture dans un shader.<br /><br /> **Sortie :**<br /><br /> `Output`: `float2`<br /> La largeur et la hauteur de la texture, sous la forme d'un vecteur.  La largeur est stockée dans le premier élément du vecteur.  La hauteur est stockée dans le deuxième élément.|**Texture**<br /> Registre de textures associé aux dimensions de la texture.|  
|**Différentiel d'élément de texture**|Génère le delta \(distance\) entre les texels d'une carte de texture 2D.<br /><br /> Vous pouvez utiliser le delta de texel pour échantillonner des valeurs voisines de texel dans un shader.<br /><br /> **Sortie :**<br /><br /> `Output`: `float2`<br /> Le delta \(distance\) d'un texel au texel suivant \(déplacement en diagonale dans la direction positive\), exprimée comme un vecteur dans l'espcae standard de texture.  Vous pouvez dériver les positions de tous les texels voisins en ignorant ou supprimant de manière sélective les coordonnées U ou V du delta.|**Texture**<br /> Registre de textures associé au delta de texel.|  
|**Échantillon de texture**|Prélève un exemple de couleur provenant d'une carte de texture 2D au niveau des coordonnées spécifiées.<br /><br /> Vous pouvez utiliser une carte de texture pour ajouter un détail de couleur à la surface d'un objet.<br /><br /> **Entrée :**<br /><br /> `UV`: `float2`<br /> Coordonnées d'où est prélevé l'exemple.<br /><br /> **Sortie :**<br /><br /> `Output`: `float4`<br /> Échantillon de couleur.|**Texture**<br /> Registre de textures associé à l'échantillonneur.|