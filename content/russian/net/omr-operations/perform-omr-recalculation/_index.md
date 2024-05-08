---
title: Выполнить перерасчет OMR в .NET
linktitle: Выполнить перерасчет OMR в .NET
second_title: Aspose.OMR .NET API
description: Узнайте, как выполнить перерасчет оптического распознавания меток в .NET с помощью Aspose.OMR для .NET. Повысьте точность данных из отсканированных изображений!
type: docs
weight: 12
url: /ru/net/omr-operations/perform-omr-recalculation/
---
В этом руководстве мы покажем вам процесс выполнения пересчета оптического распознавания меток (OMR) в .NET с использованием библиотеки Aspose.OMR для .NET. Пересчет OMR позволяет корректировать результаты распознавания на основе пользовательских порогов, повышая точность извлечения данных из отсканированных изображений.
## Предварительные условия
Прежде чем продолжить, убедитесь, что у вас есть следующие предварительные условия:
1. Visual Studio: установите Visual Studio в своей системе для разработки .NET.
2.  Библиотека Aspose.OMR для .NET: загрузите и установите библиотеку Aspose.OMR для .NET с сайта[Официальный веб-сайт](https://releases.aspose.com/omr/net/).
3. Базовые знания .NET: ознакомьтесь с платформой .NET и языком программирования C#.
## Импортировать пространства имен
Начните с импорта необходимых пространств имен:
```csharp
using Aspose.OMR.Api;
using Aspose.OMR.Model;
using System;
using System.Diagnostics;
using System.IO;
```
Давайте разобьем пример кода на подробные шаги:
## Шаг 1. Определите пути к шаблону и изображениям
Укажите пути к шаблону OMR и пользовательским изображениям:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## Шаг 2. Настройте папки
Подготовьте входные и выходные каталоги для обработки OMR:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
int CustomThreshold = 40; // Определить собственный порог
```
## Шаг 3. Инициализация механизма и процессора шаблонов
Инициализируйте движок Aspose.OMR и получите процессор шаблонов:
```csharp
OmrEngine engine = new OmrEngine();
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## Шаг 4. Обработка изображений пользователей
Переберите каждое изображение пользователя, чтобы выполнить перерасчет OMR:
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string image = UserImages[i];
    string imagePath = Path.Combine(testFolderPath, image);
    Console.WriteLine("\n\rProcessing image: " + imagePath);
    // Измерьте время производительности
    Stopwatch sw = Stopwatch.StartNew();
    // Распознать изображение
    RecognitionResult result = templateProcessor.RecognizeImage(imagePath);
    sw.Stop();
    Console.WriteLine("Recognition time: " + sw.Elapsed);
    // Экспорт результатов распознавания в CSV
    string stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"), stringRes);
    Console.WriteLine("Result Exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"));
    sw.Restart();
    // Выполнить перерасчет OMR с пользовательским порогом
    Console.WriteLine("\n\rPerforming recalculation\n\r");
    templateProcessor.Recalculate(result, CustomThreshold);
    sw.Stop();
    Console.WriteLine("Recalculation time: " + sw.Elapsed);
    // Экспортировать пересчитанные результаты
    stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"), stringRes);
    Console.WriteLine("Recalculation result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"));
}
```
## Шаг 5: Заключение
Вы успешно выполнили перерасчет оптического распознавания меток в .NET, используя Aspose.OMR для .NET. Эта функция позволяет точно настраивать результаты распознавания на основе пользовательских пороговых значений, повышая точность данных.
## Заключение
В заключение, библиотека Aspose.OMR для .NET предоставляет мощные инструменты для задач оптического распознавания меток в приложениях .NET. Следуя шагам, описанным в этом руководстве, вы сможете легко интегрировать возможности пересчета OMR в свои проекты, повышая точность извлечения данных из отсканированных изображений.
## Часто задаваемые вопросы
### Что такое перерасчет ОМР и почему это важно?
Перерасчет OMR — это процесс корректировки результатов распознавания на основе пользовательских порогов. Это важно для повышения точности извлечения данных из отсканированных изображений, особенно в сценариях, где стандартного распознавания может быть недостаточно.
### Чем перерасчет OMR отличается от стандартного признания?
Перерасчет OMR позволяет более точно корректировать результаты распознавания путем применения пользовательских пороговых значений, тогда как стандартное распознавание следует предопределенным алгоритмам без вмешательства пользователя.
### Можно ли автоматизировать перерасчет OMR в приложениях .NET?
Да, пересчет OMR можно автоматизировать в приложениях .NET путем интеграции библиотеки Aspose.OMR for .NET и использования ее API для обработки изображений и корректировки результатов распознавания.
### Какие факторы следует учитывать при определении пользовательского порога для перерасчета OMR?
При определении пользовательского порога для пересчета OMR следует учитывать такие факторы, как качество изображения, плотность меток и желаемый уровень точности.
### Где я могу найти дополнительные ресурсы и поддержку Aspose.OMR для .NET?
 Для получения документации, поддержки и взаимодействия с сообществом посетите[Форум Aspose.OMR](https://forum.aspose.com/c/omr/38) и[официальная документация](https://reference.aspose.com/omr/net/).