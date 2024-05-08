---
title: Führen Sie OMR für Bilder in .NET durch
linktitle: Führen Sie OMR für Bilder in .NET durch
second_title: Aspose.OMR .NET API
description: Erfahren Sie, wie Sie mit Aspose.OMR für .NET eine optische Markierungserkennung für Bilder in .NET durchführen. Optimieren Sie die Datenextraktion aus bildbasierten Formularen!
type: docs
weight: 11
url: /de/net/omr-operations/perform-omr-on-images/
---
In diesem Tutorial führen wir Sie durch den Prozess der Durchführung der optischen Markierungserkennung (OMR) für Bilder in .NET mithilfe der Aspose.OMR für .NET-Bibliothek. OMR ist eine Technik zum Erkennen und Extrahieren von Daten aus markierten Bereichen auf Bildern, was sie für Aufgaben wie Umfragen, Bewertungen und Datenerfassung von unschätzbarem Wert macht.
## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:
1. Visual Studio: Stellen Sie sicher, dass Visual Studio auf Ihrem System installiert ist.
2.  Aspose.OMR für .NET-Bibliothek: Laden Sie die Aspose.OMR für .NET-Bibliothek von herunter und installieren Sie sie[Veröffentlichungen](https://releases.aspose.com/omr/net/).
3. Grundkenntnisse von .NET: Machen Sie sich mit dem .NET Framework und der Programmiersprache C# vertraut.
## Namespaces importieren
Beginnen Sie mit dem Importieren der erforderlichen Namespaces:
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
Teilen wir den Beispielcode der Übersichtlichkeit halber in mehrere Schritte auf:
## Schritt 1: Definieren Sie Vorlagen- und Benutzerbildpfade
Geben Sie zunächst die Pfade für die OMR-Vorlage und die Benutzerbilder an:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## Schritt 2: Eingabe und Ausgabe vorbereiten
Bereiten Sie die Eingabe- und Ausgabeverzeichnisse für die OMR-Verarbeitung vor:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
```
## Schritt 3: OMR Engine initialisieren
Initialisieren Sie die Aspose.OMR-Engine, um mit der Verarbeitung zu beginnen:
```csharp
OmrEngine engine = new OmrEngine();
```
## Schritt 4: Vorlage laden
Laden Sie die OMR-Vorlage in den Vorlagenprozessor:
```csharp
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## Schritt 5: Durchlaufen Sie Benutzerbilder
Durchlaufen Sie jedes Benutzerbild, um OMR durchzuführen:
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string imagePath = Path.Combine(testFolderPath, UserImages[i]);
    string csvResult = templateProcessor.RecognizeImage(imagePath).GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"), csvResult);
    Console.WriteLine("Result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"));
}
```
## Schritt 6: Fazit
Sie haben mit Aspose.OMR für .NET erfolgreich eine optische Markierungserkennung für Bilder in .NET durchgeführt. Diese Funktion optimiert die Datenextraktion aus Bildern und erleichtert verschiedene Anwendungen wie Umfragen und Bewertungen.
## Abschluss
Zusammenfassend lässt sich sagen, dass die Aspose.OMR-Bibliothek für .NET eine leistungsstarke Lösung für Aufgaben zur optischen Markierungserkennung in .NET-Anwendungen bietet. Indem Sie die in diesem Tutorial beschriebenen Schritte befolgen, können Sie die OMR-Funktionalität nahtlos in Ihre Projekte integrieren und so eine effiziente Datenextraktion aus Bildern ermöglichen.
## Häufig gestellte Fragen
### Kann Aspose.OMR für .NET mehrere Bilder gleichzeitig verarbeiten?
Ja, Aspose.OMR für .NET unterstützt die Stapelverarbeitung mehrerer Bilder und ermöglicht so die effiziente Handhabung großer Datensätze.
### Welche Arten der Markierungserkennung unterstützt Aspose.OMR für .NET?
Aspose.OMR für .NET unterstützt verschiedene Markierungserkennungstypen, darunter Kontrollkästchen, Blasen und Gitter.
### Ist es möglich, OMR-Vorlagen an bestimmte Formulare anzupassen?
Natürlich können Sie mit dem Aspose.OMR-Vorlageneditor OMR-Vorlagen erstellen und anpassen und sie genau auf Ihre Anforderungen zuschneiden.
### Bietet Aspose.OMR für .NET Unterstützung für verzerrte Bilder?
Ja, Aspose.OMR für .NET enthält Funktionen zum Umgang mit schiefen und gedrehten Bildern und gewährleistet so eine genaue Markierungserkennung.
### Wo finde ich Support und Ressourcen für Aspose.OMR für .NET?
 Für Support, Dokumentation und Community-Interaktion besuchen Sie die[Aspose.OMR-Forum](https://forum.aspose.com/c/omr/38) Und[amtliche Dokumentation](https://reference.aspose.com/omr/net/).