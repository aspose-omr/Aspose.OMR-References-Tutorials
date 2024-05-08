---
title: Esegui OMR con riconoscimento di codici a barre in .NET
linktitle: Esegui OMR con riconoscimento di codici a barre in .NET
second_title: API Aspose.OMR .NET
description: Scopri come eseguire il riconoscimento ottico dei segni con il riconoscimento dei codici a barre in .NET utilizzando Aspose.OMR per .NET. Semplifica l'estrazione dei dati dalle immagini scansionate!
type: docs
weight: 10
url: /it/net/omr-operations/perform-omr-barcode-recognition/
---
In questo tutorial, ti guideremo attraverso il processo di esecuzione del riconoscimento ottico dei segni (OMR) con il riconoscimento dei codici a barre in .NET utilizzando la libreria Aspose.OMR per .NET. Questo potente strumento consente di estrarre dati da immagini scansionate contenenti aree contrassegnate e codici a barre, rendendolo un componente essenziale per varie applicazioni come sondaggi, valutazioni e raccolta dati.
## Prerequisiti
Prima di iniziare, assicurati di avere i seguenti prerequisiti:
1. Visual Studio: assicurati di avere Visual Studio installato sul tuo sistema.
2.  Libreria Aspose.OMR per .NET: scarica e installa la libreria Aspose.OMR per .NET da[Sito ufficiale](https://releases.aspose.com/omr/net/).
3. Conoscenza di base di .NET: familiarità con il framework .NET e il linguaggio di programmazione C#.
## Importa spazi dei nomi
Prima di immergerti nel codice, importa gli spazi dei nomi necessari:
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
Suddividiamo il codice di esempio in più passaggi:
## Passaggio 1: definire il modello e i percorsi delle immagini dell'utente
Innanzitutto, specifica i percorsi per il file modello e l'immagine scansionata dell'utente:
```csharp
string TemplateName = @"AsposeTestWithBarcode.omr";
string UserImage = "AsposeTestWithBarcode.jpg";
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
## Passaggio 5: riconoscere l'immagine
Esegui il riconoscimento OMR e del codice a barre sull'immagine scansionata dell'utente:
```csharp
string imagePath = Path.Combine(testFolderPath, UserImage);
string csvResult = templateProcessor.RecognizeImage(imagePath).GetCsv();
```
## Passaggio 6: esporta il risultato
Esporta il risultato OMR in un file CSV:
```csharp
File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImage) + ".csv"), csvResult);
Console.WriteLine("Result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImage) + ".csv"));
```
## Passaggio 7: conclusione
Hai eseguito con successo il riconoscimento ottico dei segni con il riconoscimento dei codici a barre in .NET utilizzando Aspose.OMR per .NET. Questa potente libreria semplifica l'estrazione dei dati dalle immagini scansionate, rendendola ideale per varie applicazioni che richiedono la raccolta e l'analisi dei dati.
## Conclusione
In conclusione, l'utilizzo della libreria Aspose.OMR per .NET consente la perfetta integrazione delle funzionalità di riconoscimento ottico dei segni e di riconoscimento dei codici a barre nelle applicazioni .NET. Seguendo i passaggi descritti in questo tutorial, puoi estrarre in modo efficiente i dati dalle immagini scansionate, aprendo numerose possibilità per attività di rilevamento, valutazione ed elaborazione dei dati.
## Domande frequenti
### Aspose.OMR per .NET è compatibile con tutti i tipi di codici a barre?
Sì, Aspose.OMR per .NET supporta vari tipi di codici a barre, inclusi codici QR, UPC-A, UPC-E, EAN-8, EAN-13, Codice 128 e altri.
### Posso personalizzare il modello OMR in base alle mie esigenze?
Assolutamente, puoi creare e personalizzare modelli OMR utilizzando l'editor di modelli Aspose.OMR, consentendoti di progettare moduli su misura per le tue esigenze specifiche.
### Aspose.OMR per .NET offre supporto per l'elaborazione di domande a scelta multipla?
Sì, Aspose.OMR per .NET eccelle nell'elaborazione di domande a scelta multipla, fornendo un riconoscimento accurato delle scelte contrassegnate all'interno delle immagini scansionate.
### È disponibile una versione di prova per Aspose.OMR per .NET?
 Sì, puoi accedere a una versione di prova gratuita di Aspose.OMR per .NET da[rilascia](https://releases.aspose.com/).
### Dove posso cercare assistenza o supporto per Aspose.OMR per .NET?
 Per qualsiasi richiesta o assistenza riguardante Aspose.OMR per .NET, è possibile visitare il[Forum Aspose.OMR](https://forum.aspose.com/c/omr/38) connettersi con la comunità e chiedere consiglio agli esperti.