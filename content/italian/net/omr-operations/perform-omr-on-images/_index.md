---
title: Esegui OMR sulle immagini in .NET
linktitle: Esegui OMR sulle immagini in .NET
second_title: API Aspose.OMR .NET
description: Scopri come eseguire il riconoscimento ottico dei segni sulle immagini in .NET utilizzando Aspose.OMR per .NET. Semplifica l'estrazione dei dati da moduli basati su immagini!
type: docs
weight: 11
url: /it/net/omr-operations/perform-omr-on-images/
---
In questo tutorial ti guideremo attraverso il processo di esecuzione del riconoscimento ottico dei segni (OMR) sulle immagini in .NET utilizzando la libreria Aspose.OMR per .NET. OMR è una tecnica utilizzata per riconoscere ed estrarre dati da aree contrassegnate sulle immagini, rendendola preziosa per attività quali sondaggi, valutazioni e raccolta dati.
## Prerequisiti
Prima di iniziare, assicurati di possedere i seguenti prerequisiti:
1. Visual Studio: assicurati di avere Visual Studio installato sul tuo sistema.
2.  Libreria Aspose.OMR per .NET: scarica e installa la libreria Aspose.OMR per .NET da[rilascia](https://releases.aspose.com/omr/net/).
3. Conoscenza di base di .NET: familiarizza con il framework .NET e il linguaggio di programmazione C#.
## Importa spazi dei nomi
Inizia importando gli spazi dei nomi necessari:
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
Suddividiamo il codice di esempio in più passaggi per maggiore chiarezza:
## Passaggio 1: definire il modello e i percorsi delle immagini dell'utente
Innanzitutto, specifica i percorsi per il modello OMR e le immagini dell'utente:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## Passaggio 2: preparare input e output
Preparare le directory di input e output per l'elaborazione OMR:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
```
## Passaggio 3: inizializzare il motore OMR
Inizializza il motore Aspose.OMR per iniziare l'elaborazione:
```csharp
OmrEngine engine = new OmrEngine();
```
## Passaggio 4: carica il modello
Carica il modello OMR nell'elaboratore di modelli:
```csharp
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## Passaggio 5: scorrere le immagini dell'utente
Scorrere ciascuna immagine utente per eseguire OMR:
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string imagePath = Path.Combine(testFolderPath, UserImages[i]);
    string csvResult = templateProcessor.RecognizeImage(imagePath).GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"), csvResult);
    Console.WriteLine("Result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"));
}
```
## Passaggio 6: conclusione
Hai eseguito con successo il riconoscimento ottico dei segni sulle immagini in .NET utilizzando Aspose.OMR per .NET. Questa funzionalità semplifica l'estrazione dei dati dalle immagini, facilitando varie applicazioni come sondaggi e valutazioni.
## Conclusione
In conclusione, la libreria Aspose.OMR per .NET fornisce una potente soluzione per le attività di riconoscimento ottico dei segni nelle applicazioni .NET. Seguendo i passaggi descritti in questo tutorial, puoi integrare perfettamente la funzionalità OMR nei tuoi progetti, consentendo un'estrazione efficiente dei dati dalle immagini.
## Domande frequenti
### Aspose.OMR per .NET può gestire più immagini contemporaneamente?
Sì, Aspose.OMR per .NET supporta l'elaborazione batch di più immagini, consentendo una gestione efficiente di set di dati di grandi dimensioni.
### Quali tipi di riconoscimento dei marchi supporta Aspose.OMR per .NET?
Aspose.OMR per .NET supporta vari tipi di riconoscimento dei segni, incluse caselle di controllo, bolle e griglie.
### È possibile personalizzare i modelli OMR per adattarli a moduli specifici?
Assolutamente, puoi creare e personalizzare i modelli OMR utilizzando l'editor dei modelli Aspose.OMR, adattandoli alle tue esatte esigenze.
### Aspose.OMR per .NET offre supporto per immagini distorte?
Sì, Aspose.OMR per .NET include funzionalità per gestire immagini inclinate e ruotate, garantendo un riconoscimento accurato dei segni.
### Dove posso trovare supporto e risorse per Aspose.OMR per .NET?
 Per supporto, documentazione e interazione con la comunità, visitare il sito[Forum Aspose.OMR](https://forum.aspose.com/c/omr/38) E[documentazione ufficiale](https://reference.aspose.com/omr/net/).