---
title: Effectuer un OMR sur des images dans .NET
linktitle: Effectuer un OMR sur des images dans .NET
second_title: API Aspose.OMR .NET
description: Découvrez comment effectuer une reconnaissance optique de marques sur des images dans .NET à l'aide d'Aspose.OMR pour .NET. Rationalisez l’extraction de données à partir de formulaires basés sur des images !
type: docs
weight: 11
url: /fr/net/omr-operations/perform-omr-on-images/
---
Dans ce didacticiel, nous vous guiderons tout au long du processus de reconnaissance optique de marques (OMR) sur des images dans .NET à l'aide de la bibliothèque Aspose.OMR pour .NET. L'OMR est une technique utilisée pour reconnaître et extraire des données de zones marquées sur des images, ce qui la rend inestimable pour des tâches telles que des enquêtes, des évaluations et la collecte de données.
## Conditions préalables
Avant de commencer, assurez-vous de disposer des prérequis suivants :
1. Visual Studio : assurez-vous que Visual Studio est installé sur votre système.
2.  Bibliothèque Aspose.OMR pour .NET : téléchargez et installez la bibliothèque Aspose.OMR pour .NET à partir du[sorties](https://releases.aspose.com/omr/net/).
3. Connaissance de base de .NET : Familiarisez-vous avec le framework .NET et le langage de programmation C#.
## Importer des espaces de noms
Commencez par importer les espaces de noms nécessaires :
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
Décomposons l'exemple de code en plusieurs étapes pour plus de clarté :
## Étape 1 : Définir les chemins du modèle et des images utilisateur
Tout d'abord, spécifiez les chemins d'accès au modèle OMR et aux images utilisateur :
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## Étape 2 : préparer les entrées et les sorties
Préparez les répertoires d'entrée et de sortie pour le traitement OMR :
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
```
## Étape 3 : initialiser le moteur OMR
Initialisez le moteur Aspose.OMR pour commencer le traitement :
```csharp
OmrEngine engine = new OmrEngine();
```
## Étape 4 : Charger le modèle
Chargez le modèle OMR dans le processeur de modèles :
```csharp
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## Étape 5 : Parcourir les images utilisateur
Parcourez chaque image utilisateur pour effectuer l'OMR :
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string imagePath = Path.Combine(testFolderPath, UserImages[i]);
    string csvResult = templateProcessor.RecognizeImage(imagePath).GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"), csvResult);
    Console.WriteLine("Result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"));
}
```
## Étape 6 : Conclusion
Vous avez réussi à effectuer une reconnaissance optique de marques sur des images dans .NET à l'aide d'Aspose.OMR pour .NET. Cette capacité rationalise l'extraction de données à partir d'images, facilitant diverses applications telles que des enquêtes et des évaluations.
## Conclusion
En conclusion, la bibliothèque Aspose.OMR pour .NET fournit une solution puissante pour les tâches de reconnaissance optique de marques dans les applications .NET. En suivant les étapes décrites dans ce didacticiel, vous pouvez intégrer de manière transparente la fonctionnalité OMR dans vos projets, permettant ainsi une extraction efficace des données à partir des images.
## Questions fréquemment posées
### Aspose.OMR pour .NET peut-il gérer plusieurs images simultanément ?
Oui, Aspose.OMR pour .NET prend en charge le traitement par lots de plusieurs images, permettant une gestion efficace de grands ensembles de données.
### Quels types de reconnaissance de marques Aspose.OMR pour .NET prend-il en charge ?
Aspose.OMR pour .NET prend en charge différents types de reconnaissance de marques, notamment les cases à cocher, les bulles et les grilles.
### Est-il possible de personnaliser les modèles OMR pour qu'ils correspondent à des formulaires spécifiques ?
Absolument, vous pouvez créer et personnaliser des modèles OMR à l'aide de l'éditeur de modèles Aspose.OMR, en les adaptant à vos besoins exacts.
### Aspose.OMR pour .NET offre-t-il la prise en charge des images asymétriques ?
Oui, Aspose.OMR pour .NET inclut des fonctionnalités permettant de gérer les images inclinées et pivotées, garantissant ainsi une reconnaissance précise des marques.
### Où puis-je trouver de l’assistance et des ressources pour Aspose.OMR pour .NET ?
 Pour obtenir de l'aide, de la documentation et une interaction avec la communauté, visitez le[Forum Aspose.OMR](https://forum.aspose.com/c/omr/38) et[documentation officielle](https://reference.aspose.com/omr/net/).