---
title: Wykonaj OMR na obrazach w .NET
linktitle: Wykonaj OMR na obrazach w .NET
second_title: Aspose.OMR .NET API
description: Dowiedz się, jak wykonać optyczne rozpoznawanie znaków na obrazach w .NET przy użyciu Aspose.OMR dla .NET. Usprawnij wyodrębnianie danych z formularzy opartych na obrazach!
type: docs
weight: 11
url: /pl/net/omr-operations/perform-omr-on-images/
---
tym samouczku przeprowadzimy Cię przez proces wykonywania optycznego rozpoznawania znaków (OMR) na obrazach w platformie .NET przy użyciu biblioteki Aspose.OMR dla platformy .NET. OMR to technika używana do rozpoznawania i wydobywania danych z zaznaczonych obszarów na obrazach, dzięki czemu jest nieoceniona przy zadaniach takich jak ankiety, oceny i gromadzenie danych.
## Warunki wstępne
Zanim zaczniemy, upewnij się, że masz następujące wymagania wstępne:
1. Visual Studio: Upewnij się, że masz zainstalowany program Visual Studio w swoim systemie.
2.  Biblioteka Aspose.OMR dla .NET: Pobierz i zainstaluj bibliotekę Aspose.OMR dla .NET z[wydania](https://releases.aspose.com/omr/net/).
3. Podstawowa znajomość .NET: Zapoznaj się ze frameworkiem .NET i językiem programowania C#.
## Importuj przestrzenie nazw
Zacznij od zaimportowania niezbędnych przestrzeni nazw:
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
Dla przejrzystości podzielmy przykładowy kod na wiele kroków:
## Krok 1: Zdefiniuj ścieżki szablonu i obrazu użytkownika
Najpierw określ ścieżki szablonu OMR i obrazów użytkownika:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## Krok 2: Przygotuj dane wejściowe i wyjściowe
Przygotuj katalogi wejściowe i wyjściowe do przetwarzania OMR:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
```
## Krok 3: Zainicjuj silnik OMR
Zainicjuj silnik Aspose.OMR, aby rozpocząć przetwarzanie:
```csharp
OmrEngine engine = new OmrEngine();
```
## Krok 4: Załaduj szablon
Załaduj szablon OMR do procesora szablonów:
```csharp
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## Krok 5: Iteruj po obrazach użytkownika
Iteruj po każdym obrazie użytkownika, aby wykonać OMR:
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string imagePath = Path.Combine(testFolderPath, UserImages[i]);
    string csvResult = templateProcessor.RecognizeImage(imagePath).GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"), csvResult);
    Console.WriteLine("Result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"));
}
```
## Krok 6: Wniosek
Pomyślnie wykonałeś optyczne rozpoznawanie znaków na obrazach w .NET przy użyciu Aspose.OMR dla .NET. Ta funkcja usprawnia wyodrębnianie danych z obrazów, ułatwiając różne zastosowania, takie jak ankiety i oceny.
## Wniosek
Podsumowując, biblioteka Aspose.OMR dla .NET zapewnia potężne rozwiązanie do zadań optycznego rozpoznawania znaków w aplikacjach .NET. Wykonując kroki opisane w tym samouczku, możesz bezproblemowo zintegrować funkcjonalność OMR ze swoimi projektami, umożliwiając efektywne wyodrębnianie danych z obrazów.
## Często Zadawane Pytania
### Czy Aspose.OMR dla .NET może obsługiwać wiele obrazów jednocześnie?
Tak, Aspose.OMR dla .NET obsługuje przetwarzanie wsadowe wielu obrazów, umożliwiając wydajną obsługę dużych zbiorów danych.
### Jakie typy rozpoznawania znaków obsługuje Aspose.OMR dla .NET?
Aspose.OMR dla .NET obsługuje różne typy rozpoznawania znaków, w tym pola wyboru, bąbelki i siatki.
### Czy można dostosować szablony OMR do konkretnych formularzy?
Oczywiście możesz tworzyć i dostosowywać szablony OMR za pomocą Edytora szablonów Aspose.OMR, dostosowując je do swoich dokładnych wymagań.
### Czy Aspose.OMR dla .NET oferuje obsługę przekrzywionych obrazów?
Tak, Aspose.OMR dla .NET zawiera funkcje do obsługi przekrzywionych i obróconych obrazów, zapewniając dokładne rozpoznawanie znaków.
### Gdzie mogę znaleźć wsparcie i zasoby dla Aspose.OMR dla .NET?
 Aby uzyskać pomoc, dokumentację i interakcję ze społecznością, odwiedź stronę[Forum Aspose.OMR](https://forum.aspose.com/c/omr/38) I[oficjalna dokumentacja](https://reference.aspose.com/omr/net/).