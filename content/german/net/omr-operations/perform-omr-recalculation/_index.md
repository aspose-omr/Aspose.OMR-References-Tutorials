---
title: OMR-Neuberechnung in .NET durchführen
linktitle: OMR-Neuberechnung in .NET durchführen
second_title: Aspose.OMR .NET API
description: Erfahren Sie, wie Sie mit Aspose.OMR für .NET eine Neuberechnung der optischen Markierungserkennung in .NET durchführen. Verbessern Sie die Datengenauigkeit gescannter Bilder!
type: docs
weight: 12
url: /de/net/omr-operations/perform-omr-recalculation/
---
In diesem Tutorial führen wir Sie durch den Prozess der Neuberechnung der optischen Markierungserkennung (OMR) in .NET mithilfe der Aspose.OMR für .NET-Bibliothek. Die OMR-Neuberechnung ermöglicht es Ihnen, die Erkennungsergebnisse anhand benutzerdefinierter Schwellenwerte anzupassen und so die Genauigkeit der Datenextraktion aus gescannten Bildern zu verbessern.
## Voraussetzungen
Bevor Sie fortfahren, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:
1. Visual Studio: Installieren Sie Visual Studio auf Ihrem System für die .NET-Entwicklung.
2.  Aspose.OMR für .NET-Bibliothek: Laden Sie die Aspose.OMR für .NET-Bibliothek von herunter und installieren Sie sie[offizielle Website](https://releases.aspose.com/omr/net/).
3. Grundkenntnisse von .NET: Machen Sie sich mit dem .NET Framework und der Programmiersprache C# vertraut.
## Namespaces importieren
Beginnen Sie mit dem Importieren der erforderlichen Namespaces:
```csharp
using Aspose.OMR.Api;
using Aspose.OMR.Model;
using System;
using System.Diagnostics;
using System.IO;
```
Lassen Sie uns den Beispielcode in detaillierte Schritte unterteilen:
## Schritt 1: Definieren Sie Vorlagen- und Bildpfade
Geben Sie die Pfade für die OMR-Vorlage und die Benutzerbilder an:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## Schritt 2: Ordner einrichten
Bereiten Sie die Eingabe- und Ausgabeverzeichnisse für die OMR-Verarbeitung vor:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
int CustomThreshold = 40; // Definieren Sie einen benutzerdefinierten Schwellenwert
```
## Schritt 3: Engine und Vorlagenprozessor initialisieren
Initialisieren Sie die Aspose.OMR-Engine und rufen Sie den Vorlagenprozessor ab:
```csharp
OmrEngine engine = new OmrEngine();
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## Schritt 4: Benutzerbilder verarbeiten
Durchlaufen Sie jedes Benutzerbild, um eine OMR-Neuberechnung durchzuführen:
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string image = UserImages[i];
    string imagePath = Path.Combine(testFolderPath, image);
    Console.WriteLine("\n\rProcessing image: " + imagePath);
    // Messen Sie die Leistungszeit
    Stopwatch sw = Stopwatch.StartNew();
    // Bild erkennen
    RecognitionResult result = templateProcessor.RecognizeImage(imagePath);
    sw.Stop();
    Console.WriteLine("Recognition time: " + sw.Elapsed);
    // Erkennungsergebnisse in CSV exportieren
    string stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"), stringRes);
    Console.WriteLine("Result Exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"));
    sw.Restart();
    // Führen Sie eine OMR-Neuberechnung mit benutzerdefiniertem Schwellenwert durch
    Console.WriteLine("\n\rPerforming recalculation\n\r");
    templateProcessor.Recalculate(result, CustomThreshold);
    sw.Stop();
    Console.WriteLine("Recalculation time: " + sw.Elapsed);
    // Neu berechnete Ergebnisse exportieren
    stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"), stringRes);
    Console.WriteLine("Recalculation result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"));
}
```
## Schritt 5: Fazit
Sie haben die Neuberechnung der optischen Markierungserkennung in .NET mithilfe von Aspose.OMR für .NET erfolgreich durchgeführt. Mit dieser Funktion können Sie die Erkennungsergebnisse anhand benutzerdefinierter Schwellenwerte optimieren und so die Datengenauigkeit verbessern.
## Abschluss
Zusammenfassend lässt sich sagen, dass die Aspose.OMR-Bibliothek für .NET leistungsstarke Tools für Aufgaben zur optischen Markierungserkennung in .NET-Anwendungen bietet. Indem Sie die in diesem Tutorial beschriebenen Schritte befolgen, können Sie OMR-Neuberechnungsfunktionen nahtlos in Ihre Projekte integrieren und so die Genauigkeit der Datenextraktion aus gescannten Bildern verbessern.
## Häufig gestellte Fragen
### Was ist eine OMR-Neuberechnung und warum ist sie wichtig?
Bei der OMR-Neuberechnung werden die Erkennungsergebnisse anhand benutzerdefinierter Schwellenwerte angepasst. Dies ist wichtig, um die Genauigkeit der Datenextraktion aus gescannten Bildern zu verbessern, insbesondere in Szenarien, in denen die Standarderkennung möglicherweise nicht ausreicht.
### Worin unterscheidet sich die OMR-Neuberechnung von der Standarderkennung?
Durch die OMR-Neuberechnung sind feinere Anpassungen der Erkennungsergebnisse durch die Anwendung benutzerdefinierter Schwellenwerte möglich, während die Standarderkennung vordefinierten Algorithmen ohne Benutzereingriff folgt.
### Kann die OMR-Neuberechnung in .NET-Anwendungen automatisiert werden?
Ja, die OMR-Neuberechnung kann in .NET-Anwendungen automatisiert werden, indem die Aspose.OMR-Bibliothek für .NET integriert und ihre API zur Bildverarbeitung und Anpassung der Erkennungsergebnisse verwendet wird.
### Welche Faktoren sollten bei der Bestimmung des benutzerdefinierten Schwellenwerts für die OMR-Neuberechnung berücksichtigt werden?
Faktoren wie Bildqualität, Markierungsdichte und gewünschtes Genauigkeitsniveau sollten bei der Bestimmung des benutzerdefinierten Schwellenwerts für die OMR-Neuberechnung berücksichtigt werden.
### Wo finde ich zusätzliche Ressourcen und Support für Aspose.OMR für .NET?
 Für Dokumentation, Support und Community-Interaktion besuchen Sie die[Aspose.OMR-Forum](https://forum.aspose.com/c/omr/38) Und[amtliche Dokumentation](https://reference.aspose.com/omr/net/).