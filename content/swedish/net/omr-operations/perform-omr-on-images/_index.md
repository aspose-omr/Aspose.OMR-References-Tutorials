---
title: Utför OMR på bilder i .NET
linktitle: Utför OMR på bilder i .NET
second_title: Aspose.OMR .NET API
description: Lär dig hur du utför optisk märkesigenkänning på bilder i .NET med Aspose.OMR för .NET. Effektivisera datautvinning från bildbaserade formulär!
type: docs
weight: 11
url: /sv/net/omr-operations/perform-omr-on-images/
---
den här handledningen går vi igenom processen att utföra Optical Mark Recognition (OMR) på bilder i .NET med hjälp av Aspose.OMR for .NET-biblioteket. OMR är en teknik som används för att känna igen och extrahera data från markerade områden på bilder, vilket gör den ovärderlig för uppgifter som undersökningar, bedömningar och datainsamling.
## Förutsättningar
Innan vi börjar, se till att du har följande förutsättningar:
1. Visual Studio: Se till att du har Visual Studio installerat på ditt system.
2.  Aspose.OMR for .NET Library: Ladda ner och installera Aspose.OMR for .NET-biblioteket från[släpper](https://releases.aspose.com/omr/net/).
3. Grundläggande kunskaper om .NET: Bekanta dig med .NET-ramverket och programmeringsspråket C#.
## Importera namnområden
Börja med att importera de nödvändiga namnrymden:
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
Låt oss dela upp exempelkoden i flera steg för tydlighetens skull:
## Steg 1: Definiera mall- och användarbildsökvägar
Ange först sökvägarna för OMR-mallen och användarbilder:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## Steg 2: Förbered in- och utdata
Förbered in- och utdatakatalogerna för OMR-bearbetning:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
```
## Steg 3: Initiera OMR Engine
Initiera Aspose.OMR-motorn för att börja bearbeta:
```csharp
OmrEngine engine = new OmrEngine();
```
## Steg 4: Ladda mall
Ladda OMR-mallen i mallprocessorn:
```csharp
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## Steg 5: Iterera genom användarbilder
Iterera genom varje användarbild för att utföra OMR:
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string imagePath = Path.Combine(testFolderPath, UserImages[i]);
    string csvResult = templateProcessor.RecognizeImage(imagePath).GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"), csvResult);
    Console.WriteLine("Result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"));
}
```
## Steg 6: Slutsats
Du har framgångsrikt utfört Optical Mark Recognition på bilder i .NET med Aspose.OMR för .NET. Denna förmåga effektiviserar extraheringen av data från bilder, vilket underlättar olika tillämpningar som undersökningar och bedömningar.
## Slutsats
Sammanfattningsvis erbjuder Aspose.OMR för .NET-biblioteket en kraftfull lösning för uppgifter för optisk märkesigenkänning i .NET-applikationer. Genom att följa stegen som beskrivs i denna handledning kan du sömlöst integrera OMR-funktionalitet i dina projekt, vilket möjliggör effektiv dataextraktion från bilder.
## Vanliga frågor
### Kan Aspose.OMR för .NET hantera flera bilder samtidigt?
Ja, Aspose.OMR för .NET stöder batchbehandling av flera bilder, vilket möjliggör effektiv hantering av stora datamängder.
### Vilka typer av märkesigenkänning stöder Aspose.OMR för .NET?
Aspose.OMR för .NET stöder olika typer av märkesigenkänning, inklusive kryssrutor, bubblor och rutnät.
### Är det möjligt att anpassa OMR-mallar för att matcha specifika formulär?
Absolut, du kan skapa och anpassa OMR-mallar med hjälp av Aspose.OMR Template Editor, skräddarsy dem efter dina exakta krav.
### Erbjuder Aspose.OMR för .NET stöd för sneda bilder?
Ja, Aspose.OMR för .NET innehåller funktioner för att hantera sneda och roterade bilder, vilket säkerställer korrekt märkesigenkänning.
### Var kan jag hitta support och resurser för Aspose.OMR för .NET?
 För support, dokumentation och gemenskapsinteraktion, besök[Aspose.OMR forum](https://forum.aspose.com/c/omr/38) och[officiell dokumentation](https://reference.aspose.com/omr/net/).