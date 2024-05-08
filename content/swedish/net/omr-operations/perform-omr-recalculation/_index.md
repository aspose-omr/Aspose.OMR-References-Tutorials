---
title: Utför OMR-omräkning i .NET
linktitle: Utför OMR-omräkning i .NET
second_title: Aspose.OMR .NET API
description: Lär dig hur du utför omräkning av optisk märkesigenkänning i .NET med Aspose.OMR för .NET. Förbättra datanoggrannheten från skannade bilder!
type: docs
weight: 12
url: /sv/net/omr-operations/perform-omr-recalculation/
---
I den här handledningen guidar vi dig genom processen att utföra omräkning av Optical Mark Recognition (OMR) i .NET med hjälp av Aspose.OMR for .NET-biblioteket. OMR-omräkning låter dig justera igenkänningsresultat baserat på anpassade tröskelvärden, vilket förbättrar noggrannheten för dataextraktion från skannade bilder.
## Förutsättningar
Innan du fortsätter, se till att du har följande förutsättningar:
1. Visual Studio: Installera Visual Studio på ditt system för .NET-utveckling.
2.  Aspose.OMR for .NET Library: Ladda ner och installera Aspose.OMR for .NET-biblioteket från[officiell hemsida](https://releases.aspose.com/omr/net/).
3. Grundläggande kunskaper om .NET: Bekanta dig med .NET-ramverket och programmeringsspråket C#.
## Importera namnområden
Börja med att importera de nödvändiga namnrymden:
```csharp
using Aspose.OMR.Api;
using Aspose.OMR.Model;
using System;
using System.Diagnostics;
using System.IO;
```
Låt oss dela upp exempelkoden i detaljerade steg:
## Steg 1: Definiera mall- och bildvägar
Ange sökvägarna för OMR-mallen och användarbilder:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## Steg 2: Konfigurera mappar
Förbered in- och utdatakatalogerna för OMR-bearbetning:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
int CustomThreshold = 40; // Definiera anpassad tröskel
```
## Steg 3: Initiera motor och mallprocessor
Initiera Aspose.OMR-motorn och skaffa mallprocessorn:
```csharp
OmrEngine engine = new OmrEngine();
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## Steg 4: Bearbeta användarbilder
Iterera genom varje användarbild för att utföra OMR-omräkning:
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string image = UserImages[i];
    string imagePath = Path.Combine(testFolderPath, image);
    Console.WriteLine("\n\rProcessing image: " + imagePath);
    // Mät prestationstiden
    Stopwatch sw = Stopwatch.StartNew();
    // Känner igen bilden
    RecognitionResult result = templateProcessor.RecognizeImage(imagePath);
    sw.Stop();
    Console.WriteLine("Recognition time: " + sw.Elapsed);
    // Exportera igenkänningsresultat till CSV
    string stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"), stringRes);
    Console.WriteLine("Result Exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"));
    sw.Restart();
    // Utför OMR-omräkning med anpassad tröskel
    Console.WriteLine("\n\rPerforming recalculation\n\r");
    templateProcessor.Recalculate(result, CustomThreshold);
    sw.Stop();
    Console.WriteLine("Recalculation time: " + sw.Elapsed);
    // Exportera omräknade resultat
    stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"), stringRes);
    Console.WriteLine("Recalculation result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"));
}
```
## Steg 5: Slutsats
Du har framgångsrikt utfört omräkning av Optical Mark Recognition i .NET med Aspose.OMR för .NET. Den här funktionen låter dig finjustera igenkänningsresultat baserat på anpassade trösklar, vilket förbättrar datanoggrannheten.
## Slutsats
Sammanfattningsvis tillhandahåller Aspose.OMR för .NET-biblioteket kraftfulla verktyg för optiska märkesigenkänningsuppgifter i .NET-applikationer. Genom att följa stegen som beskrivs i denna handledning kan du sömlöst integrera OMR-omräkningsfunktioner i dina projekt, vilket förbättrar noggrannheten för dataextraktion från skannade bilder.
## Vanliga frågor
### Vad är OMR-omräkning och varför är det viktigt?
OMR-omräkning är processen för att justera igenkänningsresultat baserat på anpassade trösklar. Det är viktigt för att förbättra noggrannheten av dataextraktion från skannade bilder, särskilt i scenarier där standardigenkänning kanske inte räcker.
### Hur skiljer sig OMR-omräkning från standardigenkänning?
OMR-omräkning möjliggör finare justeringar av igenkänningsresultat genom att tillämpa anpassade trösklar, medan standardigenkänning följer fördefinierade algoritmer utan användaringripande.
### Kan OMR-omräkning automatiseras i .NET-applikationer?
Ja, OMR-omräkning kan automatiseras i .NET-applikationer genom att integrera Aspose.OMR för .NET-biblioteket och använda dess API för att bearbeta bilder och justera igenkänningsresultat.
### Vilka faktorer bör beaktas när man bestämmer den anpassade tröskeln för OMR-omräkning?
Faktorer som bildkvalitet, märkestäthet och önskad noggrannhetsnivå bör beaktas när man bestämmer den anpassade tröskeln för OMR-omräkning.
### Var kan jag hitta ytterligare resurser och support för Aspose.OMR för .NET?
 För dokumentation, support och gemenskapsinteraktion, besök[Aspose.OMR forum](https://forum.aspose.com/c/omr/38) och[officiell dokumentation](https://reference.aspose.com/omr/net/).