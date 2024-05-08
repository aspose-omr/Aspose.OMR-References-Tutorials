---
title: Végezze el az OMR újraszámítást a .NET-ben
linktitle: Végezze el az OMR újraszámítást a .NET-ben
second_title: Aspose.OMR .NET API
description: Ismerje meg, hogyan hajthatja végre az optikai jelfelismerés újraszámítását .NET-ben az Aspose.OMR for .NET használatával. Növelje a beolvasott képek adatpontosságát!
type: docs
weight: 12
url: /hu/net/omr-operations/perform-omr-recalculation/
---
Ebben az oktatóanyagban végigvezetjük az optikai jelfelismerés (OMR) újraszámításának folyamatán a .NET-ben az Aspose.OMR for .NET könyvtár használatával. Az OMR újraszámítás lehetővé teszi a felismerési eredmények egyéni küszöbértékek alapján történő beállítását, javítva a beolvasott képekből az adatok kinyerésének pontosságát.
## Előfeltételek
Mielőtt folytatná, győződjön meg arról, hogy rendelkezik a következő előfeltételekkel:
1. Visual Studio: Telepítse a Visual Studio-t a rendszerére a .NET fejlesztéshez.
2.  Aspose.OMR for .NET Library: Töltse le és telepítse az Aspose.OMR for .NET könyvtárat a[hivatalos honlapján](https://releases.aspose.com/omr/net/).
3. Alapvető .NET ismeretek: Ismerkedjen meg a .NET keretrendszerrel és a C# programozási nyelvvel.
## Névterek importálása
Kezdje a szükséges névterek importálásával:
```csharp
using Aspose.OMR.Api;
using Aspose.OMR.Model;
using System;
using System.Diagnostics;
using System.IO;
```
Bontsuk fel a példakódot részletes lépésekre:
## 1. lépés: Sablon- és képútvonalak meghatározása
Adja meg az OMR-sablon és a felhasználói képek elérési útját:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## 2. lépés: Állítsa be a mappákat
Készítse elő a bemeneti és kimeneti könyvtárakat az OMR-feldolgozáshoz:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
int CustomThreshold = 40; // Egyéni küszöb meghatározása
```
## 3. lépés: Inicializálja a motort és a sablonprocesszort
Inicializálja az Aspose.OMR motort, és szerezze be a sablonprocesszort:
```csharp
OmrEngine engine = new OmrEngine();
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## 4. lépés: Felhasználói képek feldolgozása
Ismételje meg az egyes felhasználói képeket az OMR újraszámításának végrehajtásához:
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string image = UserImages[i];
    string imagePath = Path.Combine(testFolderPath, image);
    Console.WriteLine("\n\rProcessing image: " + imagePath);
    // Mérje meg a teljesítmény idejét
    Stopwatch sw = Stopwatch.StartNew();
    // Kép felismerése
    RecognitionResult result = templateProcessor.RecognizeImage(imagePath);
    sw.Stop();
    Console.WriteLine("Recognition time: " + sw.Elapsed);
    // A felismerési eredmények exportálása CSV-fájlba
    string stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"), stringRes);
    Console.WriteLine("Result Exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"));
    sw.Restart();
    // Végezze el az OMR újraszámítását egyéni küszöbértékkel
    Console.WriteLine("\n\rPerforming recalculation\n\r");
    templateProcessor.Recalculate(result, CustomThreshold);
    sw.Stop();
    Console.WriteLine("Recalculation time: " + sw.Elapsed);
    // Az újraszámított eredmények exportálása
    stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"), stringRes);
    Console.WriteLine("Recalculation result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"));
}
```
## 5. lépés: Következtetés
Sikeresen végrehajtotta az optikai jelfelismerés újraszámítását .NET-ben az Aspose.OMR for .NET használatával. Ez a funkció lehetővé teszi a felismerési eredmények finomhangolását egyéni küszöbértékek alapján, javítva ezzel az adatok pontosságát.
## Következtetés
Összefoglalva, az Aspose.OMR for .NET könyvtár hatékony eszközöket biztosít a .NET-alkalmazások optikai jelfelismerési feladataihoz. Az ebben az oktatóanyagban vázolt lépések követésével zökkenőmentesen integrálhatja az OMR újraszámítási képességeket projektjeibe, javítva a beolvasott képekből történő adatkinyerés pontosságát.
## Gyakran Ismételt Kérdések
### Mi az OMR újraszámítás, és miért fontos?
Az OMR újraszámítása a felismerési eredmények egyéni küszöbértékek alapján történő módosításának folyamata. Fontos a beolvasott képekből történő adatkinyerés pontosságának javítása érdekében, különösen olyan esetekben, amikor a szabványos felismerés nem biztos, hogy elegendő.
### Miben különbözik az OMR újraszámítás a szabványos felismeréstől?
Az OMR újraszámítása lehetővé teszi a felismerési eredmények finomabb módosítását egyéni küszöbértékek alkalmazásával, míg a standard felismerés előre meghatározott algoritmusokat követ felhasználói beavatkozás nélkül.
### Automatizálható az OMR újraszámítás .NET alkalmazásokban?
Igen, az OMR újraszámítása automatizálható .NET-alkalmazásokban az Aspose.OMR for .NET könyvtár integrálásával, és API-jának használatával a képek feldolgozására és a felismerési eredmények módosítására.
### Milyen tényezőket kell figyelembe venni az OMR újraszámítás egyéni küszöbének meghatározásakor?
Az olyan tényezőket, mint a képminőség, a jelsűrűség és a kívánt pontossági szint figyelembe kell venni az OMR újraszámítás egyéni küszöbértékének meghatározásakor.
### Hol találhatok további forrásokat és támogatást az Aspose.OMR for .NET-hez?
 Dokumentációért, támogatásért és közösségi interakcióért látogassa meg a[Aspose.OMR fórum](https://forum.aspose.com/c/omr/38) és[hivatalos dokumentáció](https://reference.aspose.com/omr/net/).