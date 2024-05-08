---
title: أداء OMR مع العتبة في .NET
linktitle: أداء OMR مع العتبة في .NET
second_title: Aspose.OMR .NET API
description: تعرف على كيفية إجراء التعرف البصري على العلامات باستخدام حد مخصص في .NET باستخدام Aspose.OMR لـ .NET. تعزيز دقة البيانات من الصور الممسوحة ضوئيا!
type: docs
weight: 13
url: /ar/net/omr-operations/perform-omr-with-threshold/
---
يعد التعرف البصري على العلامات (OMR) تقنية مهمة لاستخراج البيانات من الصور الممسوحة ضوئيًا والتي تحتوي على مناطق محددة. في هذا البرنامج التعليمي، سنستكشف كيفية إجراء OMR باستخدام حد مخصص في .NET باستخدام مكتبة Aspose.OMR لـ .NET. تسمح هذه الميزة بضبط عملية التعرف بناءً على متطلبات محددة، وبالتالي تحسين الدقة.
## المتطلبات الأساسية
قبل أن نخوض في البرنامج التعليمي، تأكد من أن لديك المتطلبات الأساسية التالية:
1. Visual Studio: قم بتثبيت Visual Studio على نظامك لتطوير .NET.
2.  Aspose.OMR لمكتبة .NET: قم بتنزيل وتثبيت Aspose.OMR لمكتبة .NET من[الموقع الرسمي](https://releases.aspose.com/omr/net/).
3. المعرفة الأساسية بـ .NET: تعرف على .NET Framework ولغة البرمجة C#.
## استيراد مساحات الأسماء
ابدأ باستيراد مساحات الأسماء الضرورية:
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
دعنا نقسم رمز المثال إلى خطوات تفصيلية:
## الخطوة 1: تحديد القالب ومسارات الصور
حدد المسارات لقالب OMR وصور المستخدم:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## الخطوة 2: تعيين عتبة مخصصة
تحديد الحد المخصص لمعالجة OMR:
```csharp
int CustomThreshold = 40;
```
## الخطوة 3: إعداد الإدخال والإخراج
قم بإعداد أدلة الإدخال والإخراج لمعالجة OMR:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
```
## الخطوة 4: تهيئة المحرك ومعالج القالب
قم بتهيئة محرك Aspose.OMR واحصل على معالج القالب:
```csharp
OmrEngine engine = new OmrEngine();
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## الخطوة 5: تنفيذ OMR باستخدام العتبة المخصصة
قم بالتكرار من خلال كل صورة مستخدم وقم بإجراء OMR باستخدام الحد المخصص:
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
## خاتمة
باتباع هذا البرنامج التعليمي، تعلمت كيفية إجراء التعرف البصري على العلامات باستخدام حد مخصص في .NET باستخدام مكتبة Aspose.OMR لـ .NET. تمكنك هذه الإمكانية من ضبط عملية التعرف، وبالتالي تحسين دقة استخراج البيانات من الصور الممسوحة ضوئيًا.
## أسئلة مكررة
### ما أهمية استخدام حد مخصص بالريال العماني؟
يتيح الحد المخصص للمستخدمين ضبط حساسية عملية التعرف، وبالتالي تحسين الدقة بناءً على خصائص ومتطلبات الصورة المحددة.
### كيف يختلف ريال عماني ذو الحد المخصص عن ريال عماني القياسي؟
يطبق OMR القياسي حدودًا محددة مسبقًا لاكتشاف العلامات، في حين يمكّن OMR مع حد مخصص المستخدمين من تحديد معلمات التعرف وتحسينها وفقًا لاحتياجاتهم.
### ما هي العوامل التي يجب مراعاتها عند تحديد حد مخصص للريال العماني؟
يجب أن تؤخذ في الاعتبار عوامل مثل جودة الصورة وكثافة العلامة ومستويات الضوضاء الخلفية عند تحديد الحد المخصص المناسب لـ OMR.
### هل يمكن أتمتة OMR مع حد مخصص لمعالجة الدُفعات؟
نعم، يمكن أتمتة OMR مع عتبة مخصصة للمعالجة المجمعة لصور متعددة، مما يسهل استخراج البيانات بكفاءة في سيناريوهات واسعة النطاق.
### أين يمكنني العثور على موارد إضافية ودعم لـ Aspose.OMR لـ .NET؟
 للحصول على التوثيق والدعم والتفاعل المجتمعي، قم بزيارة[منتدى Aspose.OMR](https://forum.aspose.com/c/omr/38) و[الوثائق الرسمية](https://reference.aspose.com/omr/net/).