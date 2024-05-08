---
title: Выполнение OMR для изображений в .NET
linktitle: Выполнение OMR для изображений в .NET
second_title: Aspose.OMR .NET API
description: Узнайте, как выполнить оптическое распознавание меток на изображениях в .NET с помощью Aspose.OMR для .NET. Оптимизируйте извлечение данных из форм на основе изображений!
type: docs
weight: 11
url: /ru/net/omr-operations/perform-omr-on-images/
---
В этом уроке мы познакомим вас с процессом оптического распознавания меток (OMR) на изображениях в .NET с использованием библиотеки Aspose.OMR для .NET. OMR — это метод, используемый для распознавания и извлечения данных из отмеченных областей на изображениях, что делает его бесценным для таких задач, как опросы, оценки и сбор данных.
## Предварительные условия
Прежде чем мы начнем, убедитесь, что у вас есть следующие предварительные условия:
1. Visual Studio: убедитесь, что в вашей системе установлена Visual Studio.
2.  Библиотека Aspose.OMR для .NET: загрузите и установите библиотеку Aspose.OMR для .NET с сайта[релизы](https://releases.aspose.com/omr/net/).
3. Базовые знания .NET: ознакомьтесь с платформой .NET и языком программирования C#.
## Импортировать пространства имен
Начните с импорта необходимых пространств имен:
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
Для ясности давайте разобьем пример кода на несколько этапов:
## Шаг 1. Определите пути к шаблону и пользовательскому изображению
Сначала укажите пути к шаблону OMR и пользовательским изображениям:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## Шаг 2. Подготовьте входные и выходные данные
Подготовьте входные и выходные каталоги для обработки OMR:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
```
## Шаг 3. Инициализируйте механизм OMR
Инициализируйте движок Aspose.OMR, чтобы начать обработку:
```csharp
OmrEngine engine = new OmrEngine();
```
## Шаг 4. Загрузите шаблон.
Загрузите шаблон OMR в процессор шаблонов:
```csharp
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## Шаг 5. Перебираем изображения пользователей
Переберите каждое изображение пользователя, чтобы выполнить OMR:
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string imagePath = Path.Combine(testFolderPath, UserImages[i]);
    string csvResult = templateProcessor.RecognizeImage(imagePath).GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"), csvResult);
    Console.WriteLine("Result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"));
}
```
## Шаг 6: Заключение
Вы успешно выполнили оптическое распознавание меток на изображениях в .NET, используя Aspose.OMR для .NET. Эта возможность упрощает извлечение данных из изображений, облегчая использование различных приложений, таких как опросы и оценки.
## Заключение
В заключение, библиотека Aspose.OMR для .NET предоставляет мощное решение для задач оптического распознавания меток в приложениях .NET. Следуя шагам, описанным в этом руководстве, вы сможете легко интегрировать функцию OMR в свои проекты, обеспечивая эффективное извлечение данных из изображений.
## Часто задаваемые вопросы
### Может ли Aspose.OMR для .NET обрабатывать несколько изображений одновременно?
Да, Aspose.OMR для .NET поддерживает пакетную обработку нескольких изображений, что позволяет эффективно обрабатывать большие наборы данных.
### Какие типы распознавания знаков поддерживает Aspose.OMR для .NET?
Aspose.OMR для .NET поддерживает различные типы распознавания меток, включая флажки, пузырьки и сетки.
### Можно ли настроить шаблоны OMR для соответствия конкретным формам?
Конечно, вы можете создавать и настраивать шаблоны OMR с помощью редактора шаблонов Aspose.OMR, адаптируя их к вашим точным требованиям.
### Предлагает ли Aspose.OMR для .NET поддержку перекошенных изображений?
Да, Aspose.OMR для .NET включает функции обработки перекошенных и повернутых изображений, обеспечивая точное распознавание меток.
### Где я могу найти поддержку и ресурсы для Aspose.OMR для .NET?
 Для получения поддержки, документации и взаимодействия с сообществом посетите[Форум Aspose.OMR](https://forum.aspose.com/c/omr/38) и[официальная документация](https://reference.aspose.com/omr/net/).