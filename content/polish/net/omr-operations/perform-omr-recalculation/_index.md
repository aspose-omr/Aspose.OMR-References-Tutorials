---
title: Wykonaj ponowne obliczenie OMR w .NET
linktitle: Wykonaj ponowne obliczenie OMR w .NET
second_title: Aspose.OMR .NET API
description: Dowiedz się, jak wykonać ponowne obliczenie optycznego rozpoznawania znaku w .NET przy użyciu Aspose.OMR dla .NET. Zwiększ dokładność danych ze zeskanowanych obrazów!
type: docs
weight: 12
url: /pl/net/omr-operations/perform-omr-recalculation/
---
W tym samouczku przeprowadzimy Cię przez proces wykonywania ponownych obliczeń przy użyciu funkcji optycznego rozpoznawania znaków (OMR) w platformie .NET przy użyciu biblioteki Aspose.OMR dla platformy .NET. Ponowne obliczenie OMR umożliwia dostosowanie wyników rozpoznawania w oparciu o niestandardowe progi, zwiększając dokładność ekstrakcji danych ze zeskanowanych obrazów.
## Warunki wstępne
Przed kontynuowaniem upewnij się, że spełnione są następujące wymagania wstępne:
1. Visual Studio: Zainstaluj program Visual Studio w swoim systemie, aby móc programować w środowisku .NET.
2.  Biblioteka Aspose.OMR dla .NET: Pobierz i zainstaluj bibliotekę Aspose.OMR dla .NET z[oficjalna strona internetowa](https://releases.aspose.com/omr/net/).
3. Podstawowa znajomość .NET: Zapoznaj się ze frameworkiem .NET i językiem programowania C#.
## Importuj przestrzenie nazw
Rozpocznij od zaimportowania niezbędnych przestrzeni nazw:
```csharp
using Aspose.OMR.Api;
using Aspose.OMR.Model;
using System;
using System.Diagnostics;
using System.IO;
```
Podzielmy przykładowy kod na szczegółowe kroki:
## Krok 1: Zdefiniuj ścieżki szablonu i obrazu
Określ ścieżki szablonu OMR i obrazów użytkownika:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## Krok 2: Skonfiguruj foldery
Przygotuj katalogi wejściowe i wyjściowe do przetwarzania OMR:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
int CustomThreshold = 40; // Zdefiniuj niestandardowy próg
```
## Krok 3: Zainicjuj silnik i procesor szablonów
Zainicjuj silnik Aspose.OMR i uzyskaj procesor szablonów:
```csharp
OmrEngine engine = new OmrEngine();
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## Krok 4: Przetwórz obrazy użytkownika
Wykonaj iterację po każdym obrazie użytkownika, aby wykonać ponowne obliczenie OMR:
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string image = UserImages[i];
    string imagePath = Path.Combine(testFolderPath, image);
    Console.WriteLine("\n\rProcessing image: " + imagePath);
    // Zmierz czas wykonania
    Stopwatch sw = Stopwatch.StartNew();
    // Rozpoznaj obraz
    RecognitionResult result = templateProcessor.RecognizeImage(imagePath);
    sw.Stop();
    Console.WriteLine("Recognition time: " + sw.Elapsed);
    // Eksportuj wyniki rozpoznawania do pliku CSV
    string stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"), stringRes);
    Console.WriteLine("Result Exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"));
    sw.Restart();
    // Wykonaj ponowne obliczenie OMR z niestandardowym progiem
    Console.WriteLine("\n\rPerforming recalculation\n\r");
    templateProcessor.Recalculate(result, CustomThreshold);
    sw.Stop();
    Console.WriteLine("Recalculation time: " + sw.Elapsed);
    // Eksportuj ponownie obliczone wyniki
    stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"), stringRes);
    Console.WriteLine("Recalculation result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"));
}
```
## Krok 5: Wniosek
Pomyślnie wykonałeś przeliczenie Optical Mark Recognition w .NET przy użyciu Aspose.OMR dla .NET. Ta funkcja pozwala dostosować wyniki rozpoznawania w oparciu o niestandardowe progi, zwiększając dokładność danych.
## Wniosek
Podsumowując, biblioteka Aspose.OMR dla .NET zapewnia potężne narzędzia do zadań optycznego rozpoznawania znaków w aplikacjach .NET. Wykonując kroki opisane w tym samouczku, możesz bezproblemowo zintegrować funkcje ponownego obliczania OMR ze swoimi projektami, zwiększając dokładność ekstrakcji danych ze zeskanowanych obrazów.
## Często Zadawane Pytania
### Co to jest przeliczenie OMR i dlaczego jest ważne?
Ponowne obliczenie OMR to proces dostosowywania wyników rozpoznawania w oparciu o niestandardowe progi. Jest to ważne dla poprawy dokładności wyodrębniania danych ze zeskanowanych obrazów, szczególnie w scenariuszach, w których standardowe rozpoznawanie może nie wystarczyć.
### Czym przeliczenie OMR różni się od rozpoznawania standardowego?
Ponowne obliczenie OMR umożliwia dokładniejsze dostosowanie wyników rozpoznawania poprzez zastosowanie niestandardowych progów, podczas gdy rozpoznawanie standardowe odbywa się według predefiniowanych algorytmów bez interwencji użytkownika.
### Czy przeliczanie OMR można zautomatyzować w aplikacjach .NET?
Tak, ponowne obliczanie OMR można zautomatyzować w aplikacjach .NET poprzez integrację biblioteki Aspose.OMR dla .NET i wykorzystanie jej API do przetwarzania obrazów i dostosowywania wyników rozpoznawania.
### Jakie czynniki należy wziąć pod uwagę przy ustalaniu niestandardowego progu ponownego obliczenia OMR?
Przy określaniu niestandardowego progu ponownego obliczenia OMR należy wziąć pod uwagę takie czynniki, jak jakość obrazu, gęstość znaczników i pożądany poziom dokładności.
### Gdzie mogę znaleźć dodatkowe zasoby i wsparcie dla Aspose.OMR dla .NET?
 Aby uzyskać dokumentację, wsparcie i interakcję ze społecznością, odwiedź stronę[Forum Aspose.OMR](https://forum.aspose.com/c/omr/38) I[oficjalna dokumentacja](https://reference.aspose.com/omr/net/).