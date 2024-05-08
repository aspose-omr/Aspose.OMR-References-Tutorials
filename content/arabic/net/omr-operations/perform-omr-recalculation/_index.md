---
title: إجراء إعادة حساب ريال عماني في .NET
linktitle: إجراء إعادة حساب ريال عماني في .NET
second_title: Aspose.OMR .NET API
description: تعرف على كيفية إجراء إعادة حساب التعرف الضوئي على العلامات في .NET باستخدام Aspose.OMR لـ .NET. تعزيز دقة البيانات من الصور الممسوحة ضوئيا!
type: docs
weight: 12
url: /ar/net/omr-operations/perform-omr-recalculation/
---
في هذا البرنامج التعليمي، سنرشدك خلال عملية إعادة حساب التعرف على العلامات الضوئية (OMR) في .NET باستخدام مكتبة Aspose.OMR لـ .NET. تسمح لك إعادة حساب OMR بضبط نتائج التعرف بناءً على الحدود المخصصة، مما يعزز دقة استخراج البيانات من الصور الممسوحة ضوئيًا.
## المتطلبات الأساسية
قبل المتابعة، تأكد من توفر المتطلبات الأساسية التالية:
1. Visual Studio: قم بتثبيت Visual Studio على نظامك لتطوير .NET.
2.  Aspose.OMR لمكتبة .NET: قم بتنزيل وتثبيت Aspose.OMR لمكتبة .NET من[الموقع الرسمي](https://releases.aspose.com/omr/net/).
3. المعرفة الأساسية بـ .NET: تعرف على .NET Framework ولغة البرمجة C#.
## استيراد مساحات الأسماء
ابدأ باستيراد مساحات الأسماء الضرورية:
```csharp
using Aspose.OMR.Api;
using Aspose.OMR.Model;
using System;
using System.Diagnostics;
using System.IO;
```
دعنا نقسم رمز المثال إلى خطوات تفصيلية:
## الخطوة 1: تحديد القالب ومسارات الصور
حدد المسارات لقالب OMR وصور المستخدم:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## الخطوة 2: إعداد المجلدات
قم بإعداد أدلة الإدخال والإخراج لمعالجة OMR:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
int CustomThreshold = 40; // تحديد عتبة مخصصة
```
## الخطوة 3: تهيئة المحرك ومعالج القالب
قم بتهيئة محرك Aspose.OMR واحصل على معالج القالب:
```csharp
OmrEngine engine = new OmrEngine();
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## الخطوة 4: معالجة صور المستخدم
قم بالتكرار من خلال كل صورة مستخدم لإجراء إعادة حساب OMR:
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string image = UserImages[i];
    string imagePath = Path.Combine(testFolderPath, image);
    Console.WriteLine("\n\rProcessing image: " + imagePath);
    // قياس وقت الأداء
    Stopwatch sw = Stopwatch.StartNew();
    // التعرف على الصورة
    RecognitionResult result = templateProcessor.RecognizeImage(imagePath);
    sw.Stop();
    Console.WriteLine("Recognition time: " + sw.Elapsed);
    // تصدير نتائج التعرف إلى CSV
    string stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"), stringRes);
    Console.WriteLine("Result Exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"));
    sw.Restart();
    // إجراء إعادة حساب ريال عماني (OMR) باستخدام الحد المخصص
    Console.WriteLine("\n\rPerforming recalculation\n\r");
    templateProcessor.Recalculate(result, CustomThreshold);
    sw.Stop();
    Console.WriteLine("Recalculation time: " + sw.Elapsed);
    // تصدير النتائج المعاد حسابها
    stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"), stringRes);
    Console.WriteLine("Recalculation result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"));
}
```
## الخطوة 5: الاستنتاج
لقد قمت بنجاح بإعادة حساب التعرف الضوئي على العلامات في .NET باستخدام Aspose.OMR لـ .NET. تسمح لك هذه الميزة بضبط نتائج التعرف استنادًا إلى الحدود المخصصة، مما يؤدي إلى تحسين دقة البيانات.
## خاتمة
في الختام، توفر مكتبة Aspose.OMR لـ .NET أدوات قوية لمهام التعرف الضوئي على العلامات في تطبيقات .NET. باتباع الخطوات الموضحة في هذا البرنامج التعليمي، يمكنك دمج إمكانات إعادة حساب OMR بسلاسة في مشاريعك، مما يعزز دقة استخراج البيانات من الصور الممسوحة ضوئيًا.
## أسئلة مكررة
### ما هي إعادة حساب الريال العماني، وما أهميتها؟
إعادة حساب OMR هي عملية ضبط نتائج التعرف بناءً على الحدود المخصصة. من المهم تحسين دقة استخراج البيانات من الصور الممسوحة ضوئيًا، خاصة في السيناريوهات التي قد لا يكفي فيها التعرف القياسي.
### كيف تختلف إعادة حساب OMR عن الاعتراف القياسي؟
تسمح إعادة حساب OMR بإجراء تعديلات أكثر دقة على نتائج التعرف من خلال تطبيق عتبات مخصصة، بينما يتبع التعرف القياسي خوارزميات محددة مسبقًا دون تدخل المستخدم.
### هل يمكن أتمتة إعادة حساب الـ OMR في تطبيقات .NET؟
نعم، يمكن أتمتة إعادة حساب OMR في تطبيقات .NET من خلال دمج Aspose.OMR لمكتبة .NET واستخدام واجهة برمجة التطبيقات (API) الخاصة بها لمعالجة الصور وضبط نتائج التعرف.
### ما هي العوامل التي يجب مراعاتها عند تحديد الحد المخصص لإعادة حساب ريال عماني؟
يجب أخذ عوامل مثل جودة الصورة وكثافة العلامة ومستوى الدقة المطلوب في الاعتبار عند تحديد الحد المخصص لإعادة حساب ريال عماني.
### أين يمكنني العثور على موارد إضافية ودعم لـ Aspose.OMR لـ .NET؟
 للحصول على التوثيق والدعم والتفاعل المجتمعي، قم بزيارة[منتدى Aspose.OMR](https://forum.aspose.com/c/omr/38) و[الوثائق الرسمية](https://reference.aspose.com/omr/net/).