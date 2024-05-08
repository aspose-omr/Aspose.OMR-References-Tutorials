---
title: Effectuer OMR avec seuil dans .NET
linktitle: Effectuer OMR avec seuil dans .NET
second_title: API Aspose.OMR .NET
description: Découvrez comment effectuer une reconnaissance optique de marques avec un seuil personnalisé dans .NET à l'aide d'Aspose.OMR pour .NET. Améliorez la précision des données à partir des images numérisées !
type: docs
weight: 13
url: /fr/net/omr-operations/perform-omr-with-threshold/
---
La reconnaissance optique de marques (OMR) est une technologie cruciale pour extraire des données d'images numérisées contenant des zones marquées. Dans ce didacticiel, nous verrons comment effectuer un OMR avec un seuil personnalisé dans .NET à l'aide de la bibliothèque Aspose.OMR pour .NET. Cette fonctionnalité permet d'affiner le processus de reconnaissance en fonction d'exigences spécifiques, améliorant ainsi la précision.
## Conditions préalables
Avant de plonger dans le didacticiel, assurez-vous de disposer des prérequis suivants :
1. Visual Studio : installez Visual Studio sur votre système pour le développement .NET.
2.  Bibliothèque Aspose.OMR pour .NET : téléchargez et installez la bibliothèque Aspose.OMR pour .NET à partir du[site officiel](https://releases.aspose.com/omr/net/).
3. Connaissance de base de .NET : Familiarisez-vous avec le framework .NET et le langage de programmation C#.
## Importer des espaces de noms
Commencez par importer les espaces de noms nécessaires :
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
Décomposons l'exemple de code en étapes détaillées :
## Étape 1 : Définir les chemins du modèle et des images
Spécifiez les chemins du modèle OMR et des images utilisateur :
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## Étape 2 : définir un seuil personnalisé
Définissez le seuil personnalisé pour le traitement OMR :
```csharp
int CustomThreshold = 40;
```
## Étape 3 : Préparer les entrées et les sorties
Préparez les répertoires d'entrée et de sortie pour le traitement OMR :
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
```
## Étape 4 : initialiser le moteur et le processeur de modèles
Initialisez le moteur Aspose.OMR et obtenez le processeur de modèle :
```csharp
OmrEngine engine = new OmrEngine();
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## Étape 5 : Effectuer une OMR avec un seuil personnalisé
Parcourez chaque image utilisateur et effectuez une OMR avec le seuil personnalisé :
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string imagePath = Path.Combine(testFolderPath, UserImages[i]);
    string csvResult = templateProcessor.RecognizeImage(imagePath, CustomThreshold).GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + "_Threshold.csv"), csvResult);
    Console.WriteLine("Result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + "_Threshold.csv"));
}
Console.WriteLine("PerformOMRWithThreshold executed successfully.\n\r");
```
## Conclusion
En suivant ce didacticiel, vous avez appris à effectuer une reconnaissance optique de marques avec un seuil personnalisé dans .NET à l'aide de la bibliothèque Aspose.OMR pour .NET. Cette fonctionnalité vous permet d'affiner le processus de reconnaissance, améliorant ainsi la précision de l'extraction des données à partir des images numérisées.
## Questions fréquemment posées
### Quelle est l’importance de l’utilisation d’un seuil personnalisé dans OMR ?
Un seuil personnalisé permet aux utilisateurs d'ajuster la sensibilité du processus de reconnaissance, optimisant ainsi la précision en fonction des caractéristiques et des exigences spécifiques de l'image.
### En quoi l’OMR avec un seuil personnalisé diffère-t-il de l’OMR standard ?
L'OMR standard applique des seuils prédéfinis pour la détection des marques, tandis que l'OMR avec un seuil personnalisé permet aux utilisateurs de définir et d'affiner les paramètres de reconnaissance en fonction de leurs besoins.
### Quels facteurs doivent être pris en compte lors de la définition d’un seuil personnalisé pour l’OMR ?
Des facteurs tels que la qualité de l'image, l'intensité du marquage et les niveaux de bruit de fond doivent être pris en compte lors de la détermination du seuil personnalisé approprié pour l'OMR.
### L’OMR avec un seuil personnalisé peut-il être automatisé pour le traitement par lots ?
Oui, l'OMR avec un seuil personnalisé peut être automatisé pour le traitement par lots de plusieurs images, facilitant ainsi une extraction efficace des données dans des scénarios à grande échelle.
### Où puis-je trouver des ressources supplémentaires et une assistance pour Aspose.OMR pour .NET ?
 Pour la documentation, l'assistance et l'interaction avec la communauté, visitez le[Forum Aspose.OMR](https://forum.aspose.com/c/omr/38) et[documentation officielle](https://reference.aspose.com/omr/net/).