---
title: 在 .NET 中使用 Threshold 執行 OMR
linktitle: 在 .NET 中使用 Threshold 執行 OMR
second_title: Aspose.OMR .NET API
description: 了解如何使用 Aspose.OMR for .NET 在 .NET 中使用自訂閾值執行光學標記識別。提高掃描影像的資料準確性！
type: docs
weight: 13
url: /zh-hant/net/omr-operations/perform-omr-with-threshold/
---
光學標記辨識 (OMR) 是從包含標記區域的掃描影像中提取資料的關鍵技術。在本教程中，我們將探索如何使用 Aspose.OMR for .NET 函式庫在 .NET 中使用自訂閾值執行 OMR。此功能允許根據特定要求微調識別過程，從而提高準確性。
## 先決條件
在我們深入研究本教程之前，請確保您具備以下先決條件：
1. Visual Studio：在系統上安裝 Visual Studio 以進行 .NET 開發。
2.  Aspose.OMR for .NET 函式庫：從下列位置下載並安裝 Aspose.OMR for .NET 函式庫：[官方網站](https://releases.aspose.com/omr/net/).
3. .NET基礎知識：熟悉.NET架構和C#程式語言。
## 導入命名空間
首先導入必要的命名空間：
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
讓我們將範例程式碼分解為詳細步驟：
## 第 1 步：定義模板和圖像路徑
指定OMR模板和使用者鏡像的路徑：
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## 第 2 步：設定自訂閾值
定義 OMR 處理的自訂閾值：
```csharp
int CustomThreshold = 40;
```
## 第 3 步：準備輸入與輸出
準備 OMR 處理的輸入和輸出目錄：
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
```
## 步驟4：初始化引擎和模板處理器
初始化Aspose.OMR引擎並取得模板處理器：
```csharp
OmrEngine engine = new OmrEngine();
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## 第 5 步：使用自訂閾值執行 OMR
迭代每個用戶圖像並使用自訂閾值執行 OMR：
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
## 結論
透過學習本教學課程，您已經了解如何使用 Aspose.OMR for .NET 函式庫在 .NET 中使用自訂閾值執行光學標記辨識。此功能使您能夠微調識別流程，從而提高從掃描影像中提取資料的準確性。
## 經常問的問題
### 在 OMR 中使用自訂閾值有何意義？
自訂閾值可讓使用者調整識別過程的靈敏度，從而根據特定影像特徵和要求優化準確性。
### 具有自訂閾值的 OMR 與標準 OMR 有何不同？
標準 OMR 應用預定義閾值進行標記檢測，而具有自訂閾值的 OMR 使用戶能夠根據自己的需求定義和細化識別參數。
### 設定 OMR 自訂閾值時應考慮哪些因素？
在決定適當的 OMR 自訂閾值時，應考慮影像品質、標記強度和背景雜訊水準等因素。
### 具有自訂閾值的 OMR 可以自動進行批次處理嗎？
是的，具有自訂閾值的OMR可以自動化對多個影像進行批次處理，促進大規模場景下的高效資料擷取。
### 在哪裡可以找到 Aspose.OMR for .NET 的其他資源和支援？
如需文件、支援和社區互動，請訪問[Aspose.OMR 論壇](https://forum.aspose.com/c/omr/38)和[官方文檔](https://reference.aspose.com/omr/net/).