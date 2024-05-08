---
title: Voer OMR uit op afbeeldingen in .NET
linktitle: Voer OMR uit op afbeeldingen in .NET
second_title: Aspose.OMR .NET-API
description: Leer hoe u optische merkherkenning kunt uitvoeren op afbeeldingen in .NET met behulp van Aspose.OMR voor .NET. Stroomlijn de gegevensextractie uit op afbeeldingen gebaseerde formulieren!
type: docs
weight: 11
url: /nl/net/omr-operations/perform-omr-on-images/
---
In deze zelfstudie begeleiden we u bij het uitvoeren van Optical Mark Recognition (OMR) op afbeeldingen in .NET met behulp van de Aspose.OMR voor .NET-bibliotheek. OMR is een techniek die wordt gebruikt om gegevens te herkennen en te extraheren uit gemarkeerde gebieden op afbeeldingen, waardoor deze van onschatbare waarde is voor taken zoals enquêtes, beoordelingen en gegevensverzameling.
## Vereisten
Voordat we beginnen, zorg ervoor dat u aan de volgende vereisten voldoet:
1. Visual Studio: Zorg ervoor dat Visual Studio op uw systeem is geïnstalleerd.
2.  Aspose.OMR voor .NET-bibliotheek: Download en installeer de Aspose.OMR voor .NET-bibliotheek van de[releases](https://releases.aspose.com/omr/net/).
3. Basiskennis van .NET: maak uzelf vertrouwd met het .NET-framework en de programmeertaal C#.
## Naamruimten importeren
Begin met het importeren van de benodigde naamruimten:
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
Laten we de voorbeeldcode voor de duidelijkheid opsplitsen in meerdere stappen:
## Stap 1: Definieer sjabloon- en gebruikersafbeeldingspaden
Geef eerst de paden op voor de OMR-sjabloon en gebruikersafbeeldingen:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## Stap 2: Bereid invoer en uitvoer voor
Bereid de invoer- en uitvoermappen voor voor OMR-verwerking:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
```
## Stap 3: Initialiseer de OMR-engine
Initialiseer de Aspose.OMR-engine om de verwerking te starten:
```csharp
OmrEngine engine = new OmrEngine();
```
## Stap 4: Sjabloon laden
Laad de OMR-sjabloon in de sjabloonprocessor:
```csharp
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## Stap 5: Herhaal gebruikersafbeeldingen
Herhaal elke gebruikersafbeelding om OMR uit te voeren:
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string imagePath = Path.Combine(testFolderPath, UserImages[i]);
    string csvResult = templateProcessor.RecognizeImage(imagePath).GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"), csvResult);
    Console.WriteLine("Result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"));
}
```
## Stap 6: Conclusie
hebt met succes optische tekenherkenning uitgevoerd op afbeeldingen in .NET met behulp van Aspose.OMR voor .NET. Deze mogelijkheid stroomlijnt de extractie van gegevens uit afbeeldingen, waardoor verschillende toepassingen zoals enquêtes en beoordelingen mogelijk worden gemaakt.
## Conclusie
Concluderend biedt de Aspose.OMR voor .NET-bibliotheek een krachtige oplossing voor optische merkherkenningstaken in .NET-toepassingen. Door de stappen in deze tutorial te volgen, kunt u de OMR-functionaliteit naadloos in uw projecten integreren, waardoor efficiënte gegevensextractie uit afbeeldingen mogelijk wordt.
## Veel Gestelde Vragen
### Kan Aspose.OMR voor .NET meerdere afbeeldingen tegelijk verwerken?
Ja, Aspose.OMR voor .NET ondersteunt batchverwerking van meerdere afbeeldingen, waardoor een efficiënte verwerking van grote datasets mogelijk is.
### Welke soorten merkherkenning ondersteunt Aspose.OMR voor .NET?
Aspose.OMR voor .NET ondersteunt verschillende typen markeringsherkenning, waaronder selectievakjes, bellen en rasters.
### Is het mogelijk om OMR-sjablonen aan te passen aan specifieke formulieren?
Absoluut, u kunt OMR-sjablonen maken en aanpassen met de Aspose.OMR Template Editor, zodat u ze precies kunt afstemmen op uw vereisten.
### Biedt Aspose.OMR voor .NET ondersteuning voor scheve afbeeldingen?
Ja, Aspose.OMR voor .NET bevat functies voor het verwerken van scheve en geroteerde afbeeldingen, waardoor nauwkeurige herkenning van markeringen wordt gegarandeerd.
### Waar kan ik ondersteuning en bronnen vinden voor Aspose.OMR voor .NET?
 Voor ondersteuning, documentatie en interactie met de gemeenschap gaat u naar de[Aspose.OMR-forum](https://forum.aspose.com/c/omr/38) En[officiële documentatie](https://reference.aspose.com/omr/net/).