---
title: 對 .NET 中的影像執行 OMR
linktitle: 對 .NET 中的影像執行 OMR
second_title: Aspose.OMR .NET API
description: 了解如何使用 Aspose.OMR for .NET 對 .NET 中的影像執行光學標記辨識。簡化從基於圖像的表單中提取資料！
type: docs
weight: 11
url: /zh-hant/net/omr-operations/perform-omr-on-images/
---
在本教學中，我們將引導您完成使用 Aspose.OMR for .NET 函式庫對 .NET 中的影像執行光學標記辨識 (OMR) 的過程。 OMR 是一種用於從影像上的標記區域識別和提取資料的技術，使其對於調查、評估和資料收集等任務非常有價值。
## 先決條件
在我們開始之前，請確保您符合以下先決條件：
1. Visual Studio：確保您的系統上安裝了 Visual Studio。
2.  Aspose.OMR for .NET 函式庫：從下列位置下載並安裝 Aspose.OMR for .NET 函式庫：[發布](https://releases.aspose.com/omr/net/).
3. .NET基礎知識：熟悉.NET架構和C#程式語言。
## 導入命名空間
首先導入必要的命名空間：
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
為了清楚起見，讓我們將範例程式碼分解為多個步驟：
## 第 1 步：定義模板和使用者圖像路徑
首先指定OMR範本和使用者鏡像的路徑：
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## 第 2 步：準備輸入與輸出
準備 OMR 處理的輸入和輸出目錄：
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
```
## 步驟3：初始化OMR引擎
初始化Aspose.OMR引擎開始處理：
```csharp
OmrEngine engine = new OmrEngine();
```
## 第四步：載入模板
將 OMR 模板載入到模板處理器中：
```csharp
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## 第 5 步：迭代使用者圖像
迭代每個用戶圖像以執行 OMR：
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string imagePath = Path.Combine(testFolderPath, UserImages[i]);
    string csvResult = templateProcessor.RecognizeImage(imagePath).GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"), csvResult);
    Console.WriteLine("Result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"));
}
```
## 第六步：結論
您已使用 Aspose.OMR for .NET 對 .NET 中的影像成功執行光學標記辨識。此功能簡化了從影像中提取資料的過程，促進了調查和評估等各種應用。
## 結論
總之，Aspose.OMR for .NET 函式庫為 .NET 應用程式中的光學標記辨識任務提供了強大的解決方案。透過遵循本教程中概述的步驟，您可以將 OMR 功能無縫整合到您的專案中，從而實現從圖像中高效提取資料。
## 經常問的問題
### Aspose.OMR for .NET 可以同時處理多個影像嗎？
是的，Aspose.OMR for .NET 支援批次處理多個影像，從而可以有效處理大型資料集。
### Aspose.OMR for .NET 支援哪些類型的標記識別？
Aspose.OMR for .NET 支援各種標記識別類型，包括複選框、氣泡和網格。
### 是否可以自訂 OMR 範本以符合特定表單？
當然，您可以使用 Aspose.OMR 模板編輯器建立和自訂 OMR 模板，根據您的特定要求進行自訂。
### Aspose.OMR for .NET 是否支援傾斜影像？
是的，Aspose.OMR for .NET 包含處理傾斜和旋轉影像的功能，確保準確的標記辨識。
### 在哪裡可以找到 Aspose.OMR for .NET 的支援和資源？
如需支援、文件和社群互動，請訪問[Aspose.OMR 論壇](https://forum.aspose.com/c/omr/38)和[官方文檔](https://reference.aspose.com/omr/net/).