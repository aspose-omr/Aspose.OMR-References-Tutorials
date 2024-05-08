---
title: Wykonaj OMR z Threshold w .NET
linktitle: Wykonaj OMR z Threshold w .NET
second_title: Aspose.OMR .NET API
description: Dowiedz się, jak wykonać optyczne rozpoznawanie znaków z niestandardowym progiem w .NET przy użyciu Aspose.OMR dla .NET. Zwiększ dokładność danych ze zeskanowanych obrazów!
type: docs
weight: 13
url: /pl/net/omr-operations/perform-omr-with-threshold/
---
Optyczne rozpoznawanie znaków (OMR) to kluczowa technologia umożliwiająca wyodrębnianie danych ze zeskanowanych obrazów zawierających oznaczone obszary. W tym samouczku omówimy, jak wykonać OMR z niestandardowym progiem w .NET przy użyciu biblioteki Aspose.OMR dla .NET. Ta funkcja pozwala na precyzyjne dostrojenie procesu rozpoznawania w oparciu o konkretne wymagania, zwiększając w ten sposób dokładność.
## Warunki wstępne
Zanim przejdziemy do samouczka, upewnij się, że spełniasz następujące wymagania wstępne:
1. Visual Studio: Zainstaluj program Visual Studio w swoim systemie, aby móc programować w środowisku .NET.
2.  Biblioteka Aspose.OMR dla .NET: Pobierz i zainstaluj bibliotekę Aspose.OMR dla .NET z[oficjalna strona internetowa](https://releases.aspose.com/omr/net/).
3. Podstawowa znajomość .NET: Zapoznaj się ze frameworkiem .NET i językiem programowania C#.
## Importuj przestrzenie nazw
Rozpocznij od zaimportowania niezbędnych przestrzeni nazw:
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
Podzielmy przykładowy kod na szczegółowe kroki:
## Krok 1: Zdefiniuj ścieżki szablonu i obrazu
Określ ścieżki szablonu OMR i obrazów użytkownika:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## Krok 2: Ustaw próg niestandardowy
Zdefiniuj niestandardowy próg przetwarzania OMR:
```csharp
int CustomThreshold = 40;
```
## Krok 3: Przygotuj dane wejściowe i wyjściowe
Przygotuj katalogi wejściowe i wyjściowe do przetwarzania OMR:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
```
## Krok 4: Zainicjuj silnik i procesor szablonów
Zainicjuj silnik Aspose.OMR i uzyskaj procesor szablonów:
```csharp
OmrEngine engine = new OmrEngine();
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## Krok 5: Wykonaj OMR z niestandardowym progiem
Iteruj po każdym obrazie użytkownika i wykonaj OMR z niestandardowym progiem:
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string imagePath = Path.Combine(testFolderPath, UserImages[i]);
    string csvResult = templateProcessor.RecognizeImage(imagePath, CustomThreshold).GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + "_Threshold.csv"), csvResult);
    Console.WriteLine("Result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + "_Threshold.csv"));
}
Console.WriteLine("PerformOMRWithThreshold executed successfully.\n\r");
```
## Wniosek
Wykonując ten samouczek, nauczyłeś się, jak wykonywać optyczne rozpoznawanie znaków z niestandardowym progiem w .NET przy użyciu biblioteki Aspose.OMR dla .NET. Ta funkcja umożliwia precyzyjne dostrojenie procesu rozpoznawania, zwiększając w ten sposób dokładność wyodrębniania danych ze zeskanowanych obrazów.
## Często Zadawane Pytania
### Jakie znaczenie ma użycie niestandardowego progu w OMR?
Niestandardowy próg pozwala użytkownikom dostosować czułość procesu rozpoznawania, optymalizując w ten sposób dokładność w oparciu o określone cechy i wymagania obrazu.
### Czym OMR z niestandardowym progiem różni się od standardowego OMR?
Standardowy OMR stosuje predefiniowane progi do wykrywania znaków, natomiast OMR z niestandardowym progiem umożliwia użytkownikom definiowanie i udoskonalanie parametrów rozpoznawania zgodnie z ich potrzebami.
### Jakie czynniki należy wziąć pod uwagę przy ustalaniu niestandardowego progu dla OMR?
Przy określaniu odpowiedniego niestandardowego progu dla OMR należy wziąć pod uwagę takie czynniki, jak jakość obrazu, intensywność znaku i poziom szumu tła.
### Czy OMR z niestandardowym progiem można zautomatyzować w celu przetwarzania wsadowego?
Tak, OMR z niestandardowym progiem można zautomatyzować w celu przetwarzania wsadowego wielu obrazów, ułatwiając wydajną ekstrakcję danych w scenariuszach na dużą skalę.
### Gdzie mogę znaleźć dodatkowe zasoby i wsparcie dla Aspose.OMR dla .NET?
 Aby uzyskać dokumentację, wsparcie i interakcję ze społecznością, odwiedź stronę[Forum Aspose.OMR](https://forum.aspose.com/c/omr/38) I[oficjalna dokumentacja](https://reference.aspose.com/omr/net/).