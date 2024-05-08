---
title: Provádějte OMR s Threshold v .NET
linktitle: Provádějte OMR s Threshold v .NET
second_title: Aspose.OMR .NET API
description: Naučte se, jak provádět rozpoznávání optických značek s vlastním prahem v .NET pomocí Aspose.OMR for .NET. Zvyšte přesnost dat z naskenovaných obrázků!
type: docs
weight: 13
url: /cs/net/omr-operations/perform-omr-with-threshold/
---
Optical Mark Recognition (OMR) je klíčová technologie pro extrakci dat z naskenovaných obrázků obsahujících označené oblasti. V tomto tutoriálu prozkoumáme, jak provádět OMR s vlastním prahem v .NET pomocí knihovny Aspose.OMR for .NET. Tato funkce umožňuje doladit proces rozpoznávání na základě specifických požadavků, a tím zvýšit přesnost.
## Předpoklady
Než se pustíme do výukového programu, ujistěte se, že máte následující předpoklady:
1. Visual Studio: Nainstalujte Visual Studio do systému pro vývoj .NET.
2.  Knihovna Aspose.OMR for .NET: Stáhněte a nainstalujte knihovnu Aspose.OMR for .NET z[oficiální webové stránky](https://releases.aspose.com/omr/net/).
3. Základní znalost .NET: Seznamte se s frameworkem .NET a programovacím jazykem C#.
## Import jmenných prostorů
Začněte importem potřebných jmenných prostorů:
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
Pojďme si ukázkový kód rozdělit do podrobných kroků:
## Krok 1: Definujte cestu šablony a obrázku
Zadejte cesty pro šablonu OMR a uživatelské obrázky:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## Krok 2: Nastavte vlastní prahovou hodnotu
Definujte vlastní práh pro zpracování OMR:
```csharp
int CustomThreshold = 40;
```
## Krok 3: Připravte vstup a výstup
Připravte vstupní a výstupní adresáře pro zpracování OMR:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
```
## Krok 4: Inicializujte engine a procesor šablony
Inicializujte motor Aspose.OMR a získejte procesor šablon:
```csharp
OmrEngine engine = new OmrEngine();
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## Krok 5: Proveďte OMR s vlastním prahem
Iterujte každý uživatelský obraz a provádějte OMR s vlastním prahem:
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
## Závěr
Podle tohoto kurzu jste se naučili, jak provádět rozpoznávání optických značek s vlastním prahem v .NET pomocí knihovny Aspose.OMR for .NET. Tato funkce vám umožňuje doladit proces rozpoznávání, čímž se zvýší přesnost extrakce dat z naskenovaných obrázků.
## Často kladené otázky
### Jaký význam má použití vlastního prahu v OMR?
Vlastní práh umožňuje uživatelům upravit citlivost procesu rozpoznávání, a tím optimalizovat přesnost na základě specifických charakteristik a požadavků obrazu.
### Jak se liší OMR s vlastním prahem od standardního OMR?
Standardní OMR používá předdefinované prahové hodnoty pro detekci značek, zatímco OMR s vlastní prahovou hodnotou umožňuje uživatelům definovat a upřesňovat parametry rozpoznávání podle jejich potřeb.
### Jaké faktory je třeba vzít v úvahu při nastavování vlastního prahu pro OMR?
Při určování vhodného vlastního prahu pro OMR je třeba vzít v úvahu faktory, jako je kvalita obrazu, intenzita značek a úrovně šumu pozadí.
### Lze OMR s vlastním prahem automatizovat pro dávkové zpracování?
Ano, OMR s vlastním prahem lze automatizovat pro dávkové zpracování více snímků, což usnadňuje efektivní extrakci dat ve scénářích velkého rozsahu.
### Kde najdu další zdroje a podporu pro Aspose.OMR pro .NET?
 Pro dokumentaci, podporu a interakci s komunitou navštivte[Fórum Aspose.OMR](https://forum.aspose.com/c/omr/38) a[oficiální dokumentace](https://reference.aspose.com/omr/net/).