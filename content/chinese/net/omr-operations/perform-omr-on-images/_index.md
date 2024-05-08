---
title: 对 .NET 中的图像执行 OMR
linktitle: 对 .NET 中的图像执行 OMR
second_title: Aspose.OMR .NET API
description: 了解如何使用 Aspose.OMR for .NET 对 .NET 中的图像执行光学标记识别。简化从基于图像的表单中提取数据！
type: docs
weight: 11
url: /zh/net/omr-operations/perform-omr-on-images/
---
在本教程中，我们将引导您完成使用 Aspose.OMR for .NET 库在 .NET 中对图像执行光学标记识别 (OMR) 的过程。OMR 是一种用于识别和提取图像上标记区域数据的技术，对于调查、评估和数据收集等任务非常有用。
## 先决条件
在开始之前，请确保您满足以下先决条件：
1. Visual Studio：确保您的系统上安装了 Visual Studio。
2.  Aspose.OMR for .NET 库：从以下位置下载并安装 Aspose.OMR for .NET 库：[发布](https://releases.aspose.com/omr/net/).
3. .NET 基础知识：熟悉 .NET 框架和 C# 编程语言。
## 导入命名空间
首先导入必要的命名空间：
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
为了清楚起见，我们将示例代码分解为多个步骤：
## 第 1 步：定义模板和用户图像路径
首先，指定 OMR 模板和用户图像的路径：
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## 第 2 步：准备输入和输出
准备用于 OMR 处理的输入和输出目录：
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
```
## 步骤3：初始化OMR引擎
初始化Aspose.OMR引擎开始处理：
```csharp
OmrEngine engine = new OmrEngine();
```
## 第四步：加载模板
将 OMR 模板加载到模板处理器中：
```csharp
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## 步骤 5：遍历用户图像
迭代每个用户图像来执行OMR：
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string imagePath = Path.Combine(testFolderPath, UserImages[i]);
    string csvResult = templateProcessor.RecognizeImage(imagePath).GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"), csvResult);
    Console.WriteLine("Result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"));
}
```
## 第 6 步：结论
您已使用 Aspose.OMR for .NET 对 .NET 中的图像成功执行光学标记识别。此功能简化了从图像中提取数据的过程，促进了调查和评估等各种应用。
## 结论
总之，Aspose.OMR for .NET 库为 .NET 应用程序中的光学标记识别任务提供了强大的解决方案。通过遵循本教程中概述的步骤，您可以将 OMR 功能无缝集成到您的项目中，从而实现从图像中高效提取数据。
## 经常问的问题
### Aspose.OMR for .NET 可以同时处理多个图像吗？
是的，Aspose.OMR for .NET 支持批量处理多个图像，从而可以高效处理大型数据集。
### Aspose.OMR for .NET 支持哪些类型的标记识别？
Aspose.OMR for .NET 支持各种标记识别类型，包括复选框、气泡和网格。
### 是否可以自定义 OMR 模板以匹配特定表单？
当然，您可以使用 Aspose.OMR 模板编辑器创建和自定义 OMR 模板，根据您的具体要求进行定制。
### Aspose.OMR for .NET 是否支持倾斜图像？
是的，Aspose.OMR for .NET 包含处理倾斜和旋转图像的功能，确保准确的标记识别。
### 在哪里可以找到 Aspose.OMR for .NET 的支持和资源？
如需支持、文档和社区互动，请访问[Aspose.OMR 论坛](https://forum.aspose.com/c/omr/38)和[官方文档](https://reference.aspose.com/omr/net/).