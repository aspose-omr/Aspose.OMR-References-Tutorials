---
title: Proveďte přepočet OMR v .NET
linktitle: Proveďte přepočet OMR v .NET
second_title: Aspose.OMR .NET API
description: Naučte se, jak provést přepočet optického rozpoznávání značek v .NET pomocí Aspose.OMR for .NET. Zvyšte přesnost dat z naskenovaných obrázků!
type: docs
weight: 12
url: /cs/net/omr-operations/perform-omr-recalculation/
---
V tomto tutoriálu vás provedeme procesem provádění přepočtu optického rozpoznávání značek (OMR) v .NET pomocí knihovny Aspose.OMR for .NET. Přepočet OMR umožňuje upravit výsledky rozpoznávání na základě vlastních prahových hodnot, čímž se zvyšuje přesnost extrakce dat z naskenovaných obrázků.
## Předpoklady
Než budete pokračovat, ujistěte se, že máte následující předpoklady:
1. Visual Studio: Nainstalujte Visual Studio do systému pro vývoj .NET.
2.  Knihovna Aspose.OMR for .NET: Stáhněte a nainstalujte knihovnu Aspose.OMR for .NET z[oficiální webové stránky](https://releases.aspose.com/omr/net/).
3. Základní znalost .NET: Seznamte se s frameworkem .NET a programovacím jazykem C#.
## Import jmenných prostorů
Začněte importem potřebných jmenných prostorů:
```csharp
using Aspose.OMR.Api;
using Aspose.OMR.Model;
using System;
using System.Diagnostics;
using System.IO;
```
Pojďme si ukázkový kód rozdělit do podrobných kroků:
## Krok 1: Definujte cestu šablony a obrázku
Zadejte cesty pro šablonu OMR a uživatelské obrázky:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## Krok 2: Nastavte složky
Připravte vstupní a výstupní adresáře pro zpracování OMR:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
int CustomThreshold = 40; // Definujte vlastní práh
```
## Krok 3: Inicializujte engine a procesor šablony
Inicializujte motor Aspose.OMR a získejte procesor šablon:
```csharp
OmrEngine engine = new OmrEngine();
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## Krok 4: Zpracujte uživatelské obrázky
Projděte každý uživatelský obrázek a proveďte přepočet OMR:
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string image = UserImages[i];
    string imagePath = Path.Combine(testFolderPath, image);
    Console.WriteLine("\n\rProcessing image: " + imagePath);
    // Změřte dobu výkonu
    Stopwatch sw = Stopwatch.StartNew();
    // Rozpoznat obrázek
    RecognitionResult result = templateProcessor.RecognizeImage(imagePath);
    sw.Stop();
    Console.WriteLine("Recognition time: " + sw.Elapsed);
    // Exportujte výsledky rozpoznávání do CSV
    string stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"), stringRes);
    Console.WriteLine("Result Exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"));
    sw.Restart();
    // Proveďte přepočet OMR s vlastním prahem
    Console.WriteLine("\n\rPerforming recalculation\n\r");
    templateProcessor.Recalculate(result, CustomThreshold);
    sw.Stop();
    Console.WriteLine("Recalculation time: " + sw.Elapsed);
    // Exportujte přepočítané výsledky
    stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"), stringRes);
    Console.WriteLine("Recalculation result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"));
}
```
## Krok 5: Závěr
Úspěšně jste provedli přepočet optického rozpoznávání značek v .NET pomocí Aspose.OMR pro .NET. Tato funkce umožňuje doladit výsledky rozpoznávání na základě vlastních prahových hodnot a zlepšit tak přesnost dat.
## Závěr
Na závěr, knihovna Aspose.OMR for .NET poskytuje výkonné nástroje pro úlohy optického rozpoznávání značek v aplikacích .NET. Podle kroků uvedených v tomto kurzu můžete do svých projektů bez problémů integrovat možnosti přepočtu OMR a zvýšit tak přesnost extrakce dat z naskenovaných obrázků.
## Často kladené otázky
### Co je přepočet OMR a proč je důležitý?
Přepočet OMR je proces úpravy výsledků rozpoznávání na základě vlastních prahových hodnot. Je to důležité pro zlepšení přesnosti extrakce dat z naskenovaných obrázků, zejména ve scénářích, kde standardní rozpoznávání nemusí stačit.
### Jak se liší přepočet OMR od standardního rozpoznávání?
Přepočet OMR umožňuje jemnější úpravy výsledků rozpoznávání použitím vlastních prahových hodnot, zatímco standardní rozpoznávání se řídí předdefinovanými algoritmy bez zásahu uživatele.
### Lze v aplikacích .NET automatizovat přepočet OMR?
Ano, přepočet OMR lze v aplikacích .NET automatizovat integrací knihovny Aspose.OMR for .NET a využitím jejího API pro zpracování obrázků a úpravu výsledků rozpoznávání.
### Jaké faktory je třeba vzít v úvahu při určování vlastního prahu pro přepočet OMR?
Při určování vlastního prahu pro přepočet OMR je třeba vzít v úvahu faktory, jako je kvalita obrazu, hustota značek a požadovaná úroveň přesnosti.
### Kde najdu další zdroje a podporu pro Aspose.OMR pro .NET?
 Pro dokumentaci, podporu a interakci s komunitou navštivte[Fórum Aspose.OMR](https://forum.aspose.com/c/omr/38) a[oficiální dokumentace](https://reference.aspose.com/omr/net/).