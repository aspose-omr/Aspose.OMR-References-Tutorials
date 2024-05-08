---
title: Eseguire il ricalcolo OMR in .NET
linktitle: Eseguire il ricalcolo OMR in .NET
second_title: API Aspose.OMR .NET
description: Scopri come eseguire il ricalcolo del riconoscimento ottico dei segni in .NET utilizzando Aspose.OMR per .NET. Migliora la precisione dei dati dalle immagini scansionate!
type: docs
weight: 12
url: /it/net/omr-operations/perform-omr-recalculation/
---
In questo tutorial, ti guideremo attraverso il processo di esecuzione del ricalcolo del riconoscimento ottico dei segni (OMR) in .NET utilizzando la libreria Aspose.OMR per .NET. Il ricalcolo OMR consente di regolare i risultati del riconoscimento in base a soglie personalizzate, migliorando la precisione dell'estrazione dei dati dalle immagini scansionate.
## Prerequisiti
Prima di procedere assicurati di avere i seguenti prerequisiti:
1. Visual Studio: installa Visual Studio sul tuo sistema per lo sviluppo .NET.
2.  Libreria Aspose.OMR per .NET: scarica e installa la libreria Aspose.OMR per .NET da[Sito ufficiale](https://releases.aspose.com/omr/net/).
3. Conoscenza di base di .NET: familiarizza con il framework .NET e il linguaggio di programmazione C#.
## Importa spazi dei nomi
Inizia importando gli spazi dei nomi necessari:
```csharp
using Aspose.OMR.Api;
using Aspose.OMR.Model;
using System;
using System.Diagnostics;
using System.IO;
```
Suddividiamo il codice di esempio in passaggi dettagliati:
## Passaggio 1: definire il modello e i percorsi delle immagini
Specificare i percorsi per il modello OMR e le immagini dell'utente:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## Passaggio 2: impostare le cartelle
Preparare le directory di input e output per l'elaborazione OMR:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
int CustomThreshold = 40; // Definire la soglia personalizzata
```
## Passaggio 3: inizializzare il motore e il processore dei modelli
Inizializza il motore Aspose.OMR e ottieni il processore del modello:
```csharp
OmrEngine engine = new OmrEngine();
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## Passaggio 4: elaborazione delle immagini dell'utente
Scorrere ciascuna immagine utente per eseguire il ricalcolo OMR:
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string image = UserImages[i];
    string imagePath = Path.Combine(testFolderPath, image);
    Console.WriteLine("\n\rProcessing image: " + imagePath);
    // Misurare il tempo della prestazione
    Stopwatch sw = Stopwatch.StartNew();
    // Riconoscere l'immagine
    RecognitionResult result = templateProcessor.RecognizeImage(imagePath);
    sw.Stop();
    Console.WriteLine("Recognition time: " + sw.Elapsed);
    // Esporta i risultati del riconoscimento in CSV
    string stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"), stringRes);
    Console.WriteLine("Result Exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"));
    sw.Restart();
    // Esegui il ricalcolo OMR con soglia personalizzata
    Console.WriteLine("\n\rPerforming recalculation\n\r");
    templateProcessor.Recalculate(result, CustomThreshold);
    sw.Stop();
    Console.WriteLine("Recalculation time: " + sw.Elapsed);
    // Esporta i risultati ricalcolati
    stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"), stringRes);
    Console.WriteLine("Recalculation result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"));
}
```
## Passaggio 5: conclusione
Hai eseguito con successo il ricalcolo del riconoscimento ottico dei contrassegni in .NET utilizzando Aspose.OMR per .NET. Questa funzionalità consente di ottimizzare i risultati del riconoscimento in base a soglie personalizzate, migliorando la precisione dei dati.
## Conclusione
In conclusione, la libreria Aspose.OMR per .NET fornisce potenti strumenti per le attività di riconoscimento ottico dei segni nelle applicazioni .NET. Seguendo i passaggi descritti in questo tutorial, puoi integrare perfettamente le funzionalità di ricalcolo OMR nei tuoi progetti, migliorando la precisione dell'estrazione dei dati dalle immagini scansionate.
## Domande frequenti
### Che cos'è il ricalcolo dell'OMR e perché è importante?
Il ricalcolo OMR è il processo di regolazione dei risultati del riconoscimento in base a soglie personalizzate. È importante per migliorare la precisione dell'estrazione dei dati dalle immagini scansionate, soprattutto negli scenari in cui il riconoscimento standard potrebbe non essere sufficiente.
### In cosa differisce il ricalcolo dell'OMR dal riconoscimento standard?
Il ricalcolo OMR consente regolazioni più precise dei risultati del riconoscimento applicando soglie personalizzate, mentre il riconoscimento standard segue algoritmi predefiniti senza l'intervento dell'utente.
### Il ricalcolo OMR può essere automatizzato nelle applicazioni .NET?
Sì, il ricalcolo OMR può essere automatizzato nelle applicazioni .NET integrando la libreria Aspose.OMR per .NET e utilizzando la sua API per elaborare le immagini e regolare i risultati del riconoscimento.
### Quali fattori dovrebbero essere considerati quando si determina la soglia personalizzata per il ricalcolo dell'OMR?
Quando si determina la soglia personalizzata per il ricalcolo OMR, è necessario considerare fattori quali la qualità dell'immagine, la densità dei contrassegni e il livello di precisione desiderato.
### Dove posso trovare risorse aggiuntive e supporto per Aspose.OMR per .NET?
 Per documentazione, supporto e interazione con la comunità, visitare il sito[Forum Aspose.OMR](https://forum.aspose.com/c/omr/38) E[documentazione ufficiale](https://reference.aspose.com/omr/net/).