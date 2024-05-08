---
title: تنفيذ OMR على الصور في .NET
linktitle: تنفيذ OMR على الصور في .NET
second_title: Aspose.OMR .NET API
description: تعرف على كيفية إجراء التعرف البصري على العلامات على الصور الموجودة في .NET باستخدام Aspose.OMR لـ .NET. تبسيط استخراج البيانات من النماذج القائمة على الصور!
type: docs
weight: 11
url: /ar/net/omr-operations/perform-omr-on-images/
---
في هذا البرنامج التعليمي، سنرشدك خلال عملية إجراء التعرف البصري على العلامات (OMR) على الصور الموجودة في .NET باستخدام مكتبة Aspose.OMR لـ .NET. OMR هي تقنية تستخدم للتعرف على البيانات واستخراجها من المناطق المحددة في الصور، مما يجعلها لا تقدر بثمن لمهام مثل الدراسات الاستقصائية والتقييمات وجمع البيانات.
## المتطلبات الأساسية
قبل أن نبدأ، تأكد من توفر المتطلبات الأساسية التالية:
1. Visual Studio: تأكد من تثبيت Visual Studio على نظامك.
2.  Aspose.OMR لمكتبة .NET: قم بتنزيل وتثبيت Aspose.OMR لمكتبة .NET من[إطلاق](https://releases.aspose.com/omr/net/).
3. المعرفة الأساسية بـ .NET: تعرف على .NET Framework ولغة البرمجة C#.
## استيراد مساحات الأسماء
ابدأ باستيراد مساحات الأسماء الضرورية:
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
دعونا نقسم رمز المثال إلى خطوات متعددة من أجل الوضوح:
## الخطوة 1: تحديد القالب ومسارات صور المستخدم
أولاً، حدد المسارات لقالب OMR وصور المستخدم:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## الخطوة 2: إعداد الإدخال والإخراج
قم بإعداد أدلة الإدخال والإخراج لمعالجة OMR:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
```
## الخطوة 3: تهيئة محرك OMR
قم بتهيئة محرك Aspose.OMR لبدء المعالجة:
```csharp
OmrEngine engine = new OmrEngine();
```
## الخطوة 4: تحميل القالب
قم بتحميل قالب OMR في معالج القالب:
```csharp
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## الخطوة 5: التكرار من خلال صور المستخدم
قم بالتكرار من خلال كل صورة مستخدم لإجراء OMR:
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string imagePath = Path.Combine(testFolderPath, UserImages[i]);
    string csvResult = templateProcessor.RecognizeImage(imagePath).GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"), csvResult);
    Console.WriteLine("Result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"));
}
```
## الخطوة 6: الاستنتاج
لقد نجحت في إجراء التعرف البصري على العلامات على الصور الموجودة في .NET باستخدام Aspose.OMR لـ .NET. تعمل هذه الإمكانية على تبسيط استخراج البيانات من الصور، وتسهيل التطبيقات المختلفة مثل الدراسات الاستقصائية والتقييمات.
## خاتمة
في الختام، توفر مكتبة Aspose.OMR لـ .NET حلاً قويًا لمهام التعرف الضوئي على العلامات في تطبيقات .NET. باتباع الخطوات الموضحة في هذا البرنامج التعليمي، يمكنك دمج وظيفة OMR بسلاسة في مشاريعك، مما يتيح استخراج البيانات بكفاءة من الصور.
## أسئلة مكررة
### هل يمكن لـ Aspose.OMR لـ .NET التعامل مع صور متعددة في وقت واحد؟
نعم، يدعم Aspose.OMR for .NET المعالجة المجمعة لصور متعددة، مما يسمح بالمعالجة الفعالة لمجموعات البيانات الكبيرة.
### ما أنواع التعرف على العلامات التي يدعمها Aspose.OMR لـ .NET؟
يدعم Aspose.OMR for .NET العديد من أنواع التعرف على العلامات، بما في ذلك مربعات الاختيار والفقاعات والشبكات.
### هل من الممكن تخصيص قوالب OMR لتتناسب مع نماذج محددة؟
بالتأكيد، يمكنك إنشاء وتخصيص قوالب OMR باستخدام محرر قوالب Aspose.OMR، وتخصيصها وفقًا لمتطلباتك الدقيقة.
### هل يوفر Aspose.OMR for .NET الدعم للصور المنحرفة؟
نعم، يتضمن Aspose.OMR for .NET ميزات للتعامل مع الصور المنحرفة والمدورة، مما يضمن التعرف الدقيق على العلامات.
### أين يمكنني العثور على الدعم والموارد الخاصة بـ Aspose.OMR لـ .NET؟
 للحصول على الدعم والتوثيق والتفاعل المجتمعي، قم بزيارة[منتدى Aspose.OMR](https://forum.aspose.com/c/omr/38) و[الوثائق الرسمية](https://reference.aspose.com/omr/net/).