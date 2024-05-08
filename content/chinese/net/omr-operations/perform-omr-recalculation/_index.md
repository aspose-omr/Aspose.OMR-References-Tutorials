---
title: 在.NET中执行OMR重新计算
linktitle: 在.NET中执行OMR重新计算
second_title: Aspose.OMR .NET API
description: 了解如何使用 Aspose.OMR for .NET 在 .NET 中执行光学标记识别重新计算。提高扫描图像的数据准确性！
type: docs
weight: 12
url: /zh/net/omr-operations/perform-omr-recalculation/
---
在本教程中，我们将指导您使用 Aspose.OMR for .NET 库在 .NET 中执行光学标记识别 (OMR) 重新计算的过程。 OMR重新计算允许您根据自定义阈值调整识别结果，提高扫描图像数据提取的准确性。
## 先决条件
在继续之前，请确保您满足以下先决条件：
1. Visual Studio：在系统上安装 Visual Studio 以进行 .NET 开发。
2.  Aspose.OMR for .NET 库：从以下位置下载并安装 Aspose.OMR for .NET 库：[官方网站](https://releases.aspose.com/omr/net/).
3. .NET 基础知识：熟悉 .NET 框架和 C# 编程语言。
## 导入命名空间
首先导入必要的命名空间：
```csharp
using Aspose.OMR.Api;
using Aspose.OMR.Model;
using System;
using System.Diagnostics;
using System.IO;
```
让我们将示例代码分解为详细步骤：
## 第 1 步：定义模板和图像路径
指定OMR模板和用户镜像的路径：
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## 第 2 步：设置文件夹
准备用于 OMR 处理的输入和输出目录：
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
int CustomThreshold = 40; //定义自定义阈值
```
## 第3步：初始化引擎和模板处理器
初始化Aspose.OMR引擎并获取模板处理器：
```csharp
OmrEngine engine = new OmrEngine();
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## 第四步：处理用户图像
迭代每个用户图像以执行 OMR 重新计算：
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string image = UserImages[i];
    string imagePath = Path.Combine(testFolderPath, image);
    Console.WriteLine("\n\rProcessing image: " + imagePath);
    //测量执行时间
    Stopwatch sw = Stopwatch.StartNew();
    //识别图像
    RecognitionResult result = templateProcessor.RecognizeImage(imagePath);
    sw.Stop();
    Console.WriteLine("Recognition time: " + sw.Elapsed);
    //将识别结果导出到 CSV
    string stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"), stringRes);
    Console.WriteLine("Result Exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"));
    sw.Restart();
    //使用自定义阈值执行 OMR 重新计算
    Console.WriteLine("\n\rPerforming recalculation\n\r");
    templateProcessor.Recalculate(result, CustomThreshold);
    sw.Stop();
    Console.WriteLine("Recalculation time: " + sw.Elapsed);
    //导出重新计算的结果
    stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"), stringRes);
    Console.WriteLine("Recalculation result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"));
}
```
## 第五步：结论
您已成功使用 Aspose.OMR for .NET 在 .NET 中执行光学标记识别重新计算。此功能允许您根据自定义阈值微调识别结果，从而提高数据准确性。
## 结论
总之，Aspose.OMR for .NET 库为 .NET 应用程序中的光学标记识别任务提供了强大的工具。通过遵循本教程中概述的步骤，您可以将 OMR 重新计算功能无缝集成到您的项目中，从而提高从扫描图像中提取数据的准确性。
## 经常问的问题
### 什么是OMR重新计算？为什么它很重要？
OMR 重新计算是根据自定义阈值调整识别结果的过程。这对于提高从扫描图像中提取数据的准确性非常重要，尤其是在标准识别可能不够用的情况下。
### OMR 重新计算与标准识别有何不同？
OMR 重新计算允许通过应用自定义阈值对识别结果进行更精细的调整，而标准识别遵循预定义的算法，无需用户干预。
### .NET 应用程序中可以自动进行 OMR 重新计算吗？
是的，通过集成 Aspose.OMR for .NET 库并利用其 API 处理图像和调整识别结果，可以在 .NET 应用程序中自动执行 OMR 重新计算。
### 确定 OMR 重新计算的自定义阈值时应考虑哪些因素？
在确定 OMR 重新计算的自定义阈值时，应考虑图像质量、标记密度和所需的准确度水平等因素。
### 在哪里可以找到有关 Aspose.OMR for .NET 的更多资源和支持？
如需文档、支持和社区互动，请访问[Aspose.OMR 论坛](https://forum.aspose.com/c/omr/38)和[官方文档](https://reference.aspose.com/omr/net/).