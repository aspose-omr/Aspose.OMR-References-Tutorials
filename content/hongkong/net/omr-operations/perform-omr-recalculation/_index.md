---
title: 在.NET中執行OMR重新計算
linktitle: 在.NET中執行OMR重新計算
second_title: Aspose.OMR .NET API
description: 了解如何使用 Aspose.OMR for .NET 在 .NET 中執行光學標記識別重新計算。提高掃描影像的資料準確性！
type: docs
weight: 12
url: /zh-hant/net/omr-operations/perform-omr-recalculation/
---
在本教學中，我們將指導您使用 Aspose.OMR for .NET 函式庫在 .NET 中執行光學標記辨識 (OMR) 重新計算的過程。 OMR重新計算可讓您根據自訂閾值調整辨識結果，提高掃描影像資料擷取的準確性。
## 先決條件
在繼續之前，請確保您符合以下先決條件：
1. Visual Studio：在系統上安裝 Visual Studio 以進行 .NET 開發。
2.  Aspose.OMR for .NET 函式庫：從下列位置下載並安裝 Aspose.OMR for .NET 函式庫：[官方網站](https://releases.aspose.com/omr/net/).
3. .NET基礎知識：熟悉.NET架構和C#程式語言。
## 導入命名空間
首先導入必要的命名空間：
```csharp
using Aspose.OMR.Api;
using Aspose.OMR.Model;
using System;
using System.Diagnostics;
using System.IO;
```
讓我們將範例程式碼分解為詳細步驟：
## 第 1 步：定義模板和圖像路徑
指定OMR模板和使用者鏡像的路徑：
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## 第 2 步：設定資料夾
準備 OMR 處理的輸入和輸出目錄：
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
int CustomThreshold = 40; //定義自訂閾值
```
## 步驟3：初始化引擎和模板處理器
初始化Aspose.OMR引擎並取得模板處理器：
```csharp
OmrEngine engine = new OmrEngine();
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## 第四步：處理使用者影像
迭代每個使用者圖像以執行 OMR 重新計算：
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string image = UserImages[i];
    string imagePath = Path.Combine(testFolderPath, image);
    Console.WriteLine("\n\rProcessing image: " + imagePath);
    //測量執行時間
    Stopwatch sw = Stopwatch.StartNew();
    //辨識影像
    RecognitionResult result = templateProcessor.RecognizeImage(imagePath);
    sw.Stop();
    Console.WriteLine("Recognition time: " + sw.Elapsed);
    //將識別結果匯出到 CSV
    string stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"), stringRes);
    Console.WriteLine("Result Exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"));
    sw.Restart();
    //使用自訂閾值執行 OMR 重新計算
    Console.WriteLine("\n\rPerforming recalculation\n\r");
    templateProcessor.Recalculate(result, CustomThreshold);
    sw.Stop();
    Console.WriteLine("Recalculation time: " + sw.Elapsed);
    //匯出重新計算的結果
    stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"), stringRes);
    Console.WriteLine("Recalculation result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"));
}
```
## 第五步：結論
您已使用 Aspose.OMR for .NET 在 .NET 中成功執行了光學標記識別重新計算。此功能可讓您根據自訂閾值微調識別結果，提高資料準確性。
## 結論
總之，Aspose.OMR for .NET 函式庫為 .NET 應用程式中的光學標記辨識任務提供了強大的工具。透過遵循本教學中概述的步驟，您可以將 OMR 重新計算功能無縫整合到您的專案中，從而提高從掃描影像中提取資料的準確性。
## 經常問的問題
### 什麼是 OMR 重新計算，為什麼它很重要？
OMR重新計算是根據自訂閾值調整識別結果的過程。這對於提高從掃描影像中提取資料的準確性非常重要，特別是在標準識別可能無法滿足的情況下。
### OMR 重新計算與標準識別有何不同？
OMR 重新計算允許透過應用自訂閾值對識別結果進行更精細的調整，而標準識別則遵循預先定義的演算法，而無需使用者乾預。
### OMR 重新計算可以在 .NET 應用程式中自動化嗎？
是的，透過整合 Aspose.OMR for .NET 程式庫並利用其 API 處理映像和調整識別結果，可以在 .NET 應用程式中自動執行 OMR 重新計算。
### 在確定 OMR 重新計算的自訂閾值時應考慮哪些因素？
在確定 OMR 重新計算的自訂閾值時，應考慮影像品質、標記密度和所需的準確度等因素。
### 在哪裡可以找到 Aspose.OMR for .NET 的其他資源和支援？
如需文件、支援和社區互動，請訪問[Aspose.OMR 論壇](https://forum.aspose.com/c/omr/38)和[官方文檔](https://reference.aspose.com/omr/net/).