---
title: Effectuer un recalcul OMR dans .NET
linktitle: Effectuer un recalcul OMR dans .NET
second_title: API Aspose.OMR .NET
description: Découvrez comment effectuer un recalcul de reconnaissance optique de marques dans .NET à l’aide d’Aspose.OMR pour .NET. Améliorez la précision des données à partir des images numérisées !
type: docs
weight: 12
url: /fr/net/omr-operations/perform-omr-recalculation/
---
Dans ce didacticiel, nous vous guiderons tout au long du processus de recalcul de reconnaissance optique de marques (OMR) dans .NET à l'aide de la bibliothèque Aspose.OMR pour .NET. Le recalcul OMR vous permet d'ajuster les résultats de reconnaissance en fonction de seuils personnalisés, améliorant ainsi la précision de l'extraction des données à partir des images numérisées.
## Conditions préalables
Avant de continuer, assurez-vous de disposer des prérequis suivants :
1. Visual Studio : installez Visual Studio sur votre système pour le développement .NET.
2.  Bibliothèque Aspose.OMR pour .NET : téléchargez et installez la bibliothèque Aspose.OMR pour .NET à partir du[site officiel](https://releases.aspose.com/omr/net/).
3. Connaissance de base de .NET : Familiarisez-vous avec le framework .NET et le langage de programmation C#.
## Importer des espaces de noms
Commencez par importer les espaces de noms nécessaires :
```csharp
using Aspose.OMR.Api;
using Aspose.OMR.Model;
using System;
using System.Diagnostics;
using System.IO;
```
Décomposons l'exemple de code en étapes détaillées :
## Étape 1 : Définir les chemins du modèle et des images
Spécifiez les chemins du modèle OMR et des images utilisateur :
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## Étape 2 : Configurer les dossiers
Préparez les répertoires d'entrée et de sortie pour le traitement OMR :
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
int CustomThreshold = 40; // Définir un seuil personnalisé
```
## Étape 3 : initialiser le moteur et le processeur de modèles
Initialisez le moteur Aspose.OMR et obtenez le processeur de modèle :
```csharp
OmrEngine engine = new OmrEngine();
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## Étape 4 : Traiter les images utilisateur
Parcourez chaque image utilisateur pour effectuer un recalcul OMR :
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string image = UserImages[i];
    string imagePath = Path.Combine(testFolderPath, image);
    Console.WriteLine("\n\rProcessing image: " + imagePath);
    // Mesurer le temps de performance
    Stopwatch sw = Stopwatch.StartNew();
    // Reconnaître l'image
    RecognitionResult result = templateProcessor.RecognizeImage(imagePath);
    sw.Stop();
    Console.WriteLine("Recognition time: " + sw.Elapsed);
    // Exporter les résultats de la reconnaissance au format CSV
    string stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"), stringRes);
    Console.WriteLine("Result Exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"));
    sw.Restart();
    // Effectuer un recalcul OMR avec un seuil personnalisé
    Console.WriteLine("\n\rPerforming recalculation\n\r");
    templateProcessor.Recalculate(result, CustomThreshold);
    sw.Stop();
    Console.WriteLine("Recalculation time: " + sw.Elapsed);
    // Exporter les résultats recalculés
    stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"), stringRes);
    Console.WriteLine("Recalculation result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"));
}
```
## Étape 5 : Conclusion
Vous avez effectué avec succès le recalcul de la reconnaissance optique des marques dans .NET à l’aide d’Aspose.OMR pour .NET. Cette fonctionnalité vous permet d'affiner les résultats de reconnaissance en fonction de seuils personnalisés, améliorant ainsi la précision des données.
## Conclusion
En conclusion, la bibliothèque Aspose.OMR pour .NET fournit des outils puissants pour les tâches de reconnaissance optique de marques dans les applications .NET. En suivant les étapes décrites dans ce didacticiel, vous pouvez intégrer de manière transparente les capacités de recalcul OMR dans vos projets, améliorant ainsi la précision de l'extraction des données à partir des images numérisées.
## Questions fréquemment posées
### Qu’est-ce que le recalcul de l’OMR et pourquoi est-il important ?
Le recalcul OMR est le processus d'ajustement des résultats de reconnaissance en fonction de seuils personnalisés. Cela est important pour améliorer la précision de l’extraction des données à partir des images numérisées, en particulier dans les scénarios où la reconnaissance standard peut ne pas suffire.
### En quoi le recalcul de l’OMR diffère-t-il de la reconnaissance standard ?
Le recalcul OMR permet des ajustements plus fins des résultats de reconnaissance en appliquant des seuils personnalisés, tandis que la reconnaissance standard suit des algorithmes prédéfinis sans intervention de l'utilisateur.
### Le recalcul OMR peut-il être automatisé dans les applications .NET ?
Oui, le recalcul OMR peut être automatisé dans les applications .NET en intégrant la bibliothèque Aspose.OMR pour .NET et en utilisant son API pour traiter les images et ajuster les résultats de reconnaissance.
### Quels facteurs doivent être pris en compte lors de la détermination du seuil personnalisé pour le recalcul de l’OMR ?
Des facteurs tels que la qualité de l’image, la densité des marques et le niveau de précision souhaité doivent être pris en compte lors de la détermination du seuil personnalisé pour le recalcul de l’OMR.
### Où puis-je trouver des ressources supplémentaires et une assistance pour Aspose.OMR pour .NET ?
 Pour la documentation, l'assistance et l'interaction avec la communauté, visitez le[Forum Aspose.OMR](https://forum.aspose.com/c/omr/38) et[documentation officielle](https://reference.aspose.com/omr/net/).