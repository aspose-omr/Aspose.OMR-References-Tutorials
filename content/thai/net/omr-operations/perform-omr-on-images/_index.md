---
title: ดำเนินการ OMR บนรูปภาพใน .NET
linktitle: ดำเนินการ OMR บนรูปภาพใน .NET
second_title: Aspose.OMR .NET API
description: เรียนรู้วิธีดำเนินการจดจำเครื่องหมายด้วยแสงบนรูปภาพใน .NET โดยใช้ Aspose.OMR สำหรับ .NET เพิ่มความคล่องตัวในการดึงข้อมูลจากแบบฟอร์มที่ใช้รูปภาพ!
type: docs
weight: 11
url: /th/net/omr-operations/perform-omr-on-images/
---
ในบทช่วยสอนนี้ เราจะแนะนำคุณตลอดกระบวนการดำเนินการ Optical Mark Recognition (OMR) บนรูปภาพใน .NET โดยใช้ Aspose.OMR สำหรับไลบรารี .NET OMR เป็นเทคนิคที่ใช้ในการจดจำและดึงข้อมูลจากพื้นที่ที่ทำเครื่องหมายไว้บนภาพ ทำให้มีคุณค่าสำหรับงานต่างๆ เช่น การสำรวจ การประเมิน และการรวบรวมข้อมูล
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
1. Visual Studio: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง Visual Studio ในระบบของคุณ
2.  Aspose.OMR สำหรับ .NET Library: ดาวน์โหลดและติดตั้งไลบรารี Aspose.OMR สำหรับ .NET จากไฟล์[เผยแพร่](https://releases.aspose.com/omr/net/).
3. ความรู้พื้นฐานของ .NET: ทำความคุ้นเคยกับกรอบงาน .NET และภาษาการเขียนโปรแกรม C#
## นำเข้าเนมสเปซ
เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็น:
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
มาแบ่งโค้ดตัวอย่างออกเป็นหลายขั้นตอนเพื่อความชัดเจน:
## ขั้นตอนที่ 1: กำหนดเทมเพลตและเส้นทางรูปภาพของผู้ใช้
ขั้นแรก ให้ระบุเส้นทางสำหรับเทมเพลต OMR และรูปภาพผู้ใช้:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## ขั้นตอนที่ 2: เตรียมอินพุตและเอาต์พุต
เตรียมไดเร็กทอรีอินพุตและเอาต์พุตสำหรับการประมวลผล OMR:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
```
## ขั้นตอนที่ 3: เริ่มต้นเครื่องยนต์ OMR
เตรียมใช้งานเอ็นจิ้น Aspose.OMR เพื่อเริ่มการประมวลผล:
```csharp
OmrEngine engine = new OmrEngine();
```
## ขั้นตอนที่ 4: โหลดเทมเพลต
โหลดเทมเพลต OMR ลงในตัวประมวลผลเทมเพลต:
```csharp
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## ขั้นตอนที่ 5: ทำซ้ำผ่านรูปภาพของผู้ใช้
วนซ้ำอิมเมจผู้ใช้แต่ละอันเพื่อดำเนินการ OMR:
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string imagePath = Path.Combine(testFolderPath, UserImages[i]);
    string csvResult = templateProcessor.RecognizeImage(imagePath).GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"), csvResult);
    Console.WriteLine("Result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"));
}
```
## ขั้นตอนที่ 6: บทสรุป
คุณดำเนินการจดจำเครื่องหมายด้วยแสงบนรูปภาพใน .NET ได้สำเร็จโดยใช้ Aspose.OMR สำหรับ .NET ความสามารถนี้เพิ่มความคล่องตัวในการดึงข้อมูลจากรูปภาพ อำนวยความสะดวกในการใช้งานต่างๆ เช่น การสำรวจและการประเมิน
## บทสรุป
โดยสรุป ไลบรารี Aspose.OMR สำหรับ .NET มอบโซลูชันอันทรงพลังสำหรับงาน Optical Mark Recognition ในแอปพลิเคชัน .NET ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ คุณสามารถรวมฟังก์ชัน OMR เข้ากับโปรเจ็กต์ของคุณได้อย่างราบรื่น ช่วยให้สามารถดึงข้อมูลจากรูปภาพได้อย่างมีประสิทธิภาพ
## คำถามที่พบบ่อย
### Aspose.OMR สำหรับ .NET สามารถจัดการหลายภาพพร้อมกันได้หรือไม่
ใช่ Aspose.OMR สำหรับ .NET รองรับการประมวลผลภาพหลายภาพเป็นชุด ช่วยให้สามารถจัดการชุดข้อมูลขนาดใหญ่ได้อย่างมีประสิทธิภาพ
### Aspose.OMR สำหรับ .NET รองรับการจดจำเครื่องหมายประเภทใดบ้าง
Aspose.OMR สำหรับ .NET รองรับการจดจำเครื่องหมายหลายประเภท รวมถึงช่องทำเครื่องหมาย ฟองอากาศ และกริด
### เป็นไปได้ไหมที่จะปรับแต่งเทมเพลต OMR ให้ตรงกับแบบฟอร์มเฉพาะ?
แน่นอน คุณสามารถสร้างและปรับแต่งเทมเพลต OMR ได้โดยใช้ตัวแก้ไขเทมเพลต Aspose.OMR ซึ่งปรับแต่งให้ตรงตามความต้องการของคุณ
### Aspose.OMR สำหรับ .NET รองรับภาพที่บิดเบี้ยวหรือไม่
ใช่ Aspose.OMR สำหรับ .NET มีคุณสมบัติในการจัดการภาพที่บิดเบี้ยวและหมุน ทำให้มั่นใจได้ถึงการจดจำเครื่องหมายที่แม่นยำ
### ฉันจะค้นหาการสนับสนุนและแหล่งข้อมูลสำหรับ Aspose.OMR สำหรับ .NET ได้ที่ไหน
 สำหรับการสนับสนุน เอกสาร และการโต้ตอบกับชุมชน โปรดไปที่[ฟอรั่ม Aspose.OMR](https://forum.aspose.com/c/omr/38) และ[เอกสารอย่างเป็นทางการ](https://reference.aspose.com/omr/net/).