---
title: ดำเนินการ OMR ด้วย Threshold ใน .NET
linktitle: ดำเนินการ OMR ด้วย Threshold ใน .NET
second_title: Aspose.OMR .NET API
description: เรียนรู้วิธีดำเนินการจดจำเครื่องหมายด้วยแสงด้วยเกณฑ์ที่กำหนดเองใน .NET โดยใช้ Aspose.OMR สำหรับ .NET เพิ่มความแม่นยำของข้อมูลจากภาพที่สแกน!
type: docs
weight: 13
url: /th/net/omr-operations/perform-omr-with-threshold/
---
Optical Mark Recognition (OMR) เป็นเทคโนโลยีที่สำคัญในการดึงข้อมูลจากภาพที่สแกนซึ่งมีพื้นที่ที่ทำเครื่องหมายไว้ ในบทช่วยสอนนี้ เราจะสำรวจวิธีดำเนินการ OMR ด้วยเกณฑ์ที่กำหนดเองใน .NET โดยใช้ Aspose.OMR สำหรับไลบรารี .NET คุณสมบัตินี้ช่วยให้ปรับแต่งกระบวนการจดจำได้อย่างละเอียดตามความต้องการเฉพาะ ดังนั้นจึงปรับปรุงความแม่นยำ
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเจาะลึกบทช่วยสอน ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
1. Visual Studio: ติดตั้ง Visual Studio บนระบบของคุณเพื่อการพัฒนา .NET
2.  Aspose.OMR สำหรับ .NET Library: ดาวน์โหลดและติดตั้งไลบรารี Aspose.OMR สำหรับ .NET จากไฟล์[เว็บไซต์อย่างเป็นทางการ](https://releases.aspose.com/omr/net/).
3. ความรู้พื้นฐานของ .NET: ทำความคุ้นเคยกับกรอบงาน .NET และภาษาการเขียนโปรแกรม C#
## นำเข้าเนมสเปซ
เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็น:
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
มาแบ่งโค้ดตัวอย่างออกเป็นขั้นตอนโดยละเอียด:
## ขั้นตอนที่ 1: กำหนดเทมเพลตและเส้นทางรูปภาพ
ระบุเส้นทางสำหรับเทมเพลต OMR และรูปภาพผู้ใช้:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## ขั้นตอนที่ 2: ตั้งค่าเกณฑ์ที่กำหนดเอง
กำหนดเกณฑ์ที่กำหนดเองสำหรับการประมวลผล OMR:
```csharp
int CustomThreshold = 40;
```
## ขั้นตอนที่ 3: เตรียมอินพุตและเอาต์พุต
เตรียมไดเร็กทอรีอินพุตและเอาต์พุตสำหรับการประมวลผล OMR:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
```
## ขั้นตอนที่ 4: เริ่มต้นกลไกและตัวประมวลผลเทมเพลต
เตรียมใช้งานกลไก Aspose.OMR และรับตัวประมวลผลเทมเพลต:
```csharp
OmrEngine engine = new OmrEngine();
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## ขั้นตอนที่ 5: ดำเนินการ OMR ด้วยเกณฑ์ที่กำหนดเอง
วนซ้ำอิมเมจผู้ใช้แต่ละอันและดำเนินการ OMR ด้วยเกณฑ์ที่กำหนดเอง:
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
## บทสรุป
เมื่อทำตามบทช่วยสอนนี้ คุณได้เรียนรู้วิธีดำเนินการการรับรู้เครื่องหมายด้วยแสงด้วยเกณฑ์ที่กำหนดเองใน .NET โดยใช้ไลบรารี Aspose.OMR สำหรับ .NET ความสามารถนี้ช่วยให้คุณปรับแต่งกระบวนการจดจำได้อย่างละเอียด จึงเพิ่มความแม่นยำในการดึงข้อมูลจากภาพที่สแกน
## คำถามที่พบบ่อย
### การใช้เกณฑ์ที่กำหนดเองใน OMR มีความสำคัญอย่างไร
เกณฑ์ที่กำหนดเองช่วยให้ผู้ใช้สามารถปรับความไวของกระบวนการจดจำได้ จึงปรับความแม่นยำให้เหมาะสมตามลักษณะและข้อกำหนดเฉพาะของภาพ
### OMR ที่มีเกณฑ์ที่กำหนดเองแตกต่างจาก OMR มาตรฐานอย่างไร
OMR มาตรฐานใช้เกณฑ์ที่กำหนดไว้ล่วงหน้าสำหรับการตรวจจับเครื่องหมาย ในขณะที่ OMR ที่มีเกณฑ์แบบกำหนดเองทำให้ผู้ใช้สามารถกำหนดและปรับแต่งพารามิเตอร์การจดจำได้ตามความต้องการ
### ปัจจัยใดที่ควรพิจารณาเมื่อตั้งค่าเกณฑ์ที่กำหนดเองสำหรับ OMR
ควรคำนึงถึงปัจจัยต่างๆ เช่น คุณภาพของภาพ ความเข้มของเครื่องหมาย และระดับสัญญาณรบกวนพื้นหลังเมื่อกำหนดเกณฑ์ที่กำหนดเองที่เหมาะสมสำหรับ OMR
### OMR ที่มีเกณฑ์ที่กำหนดเองสามารถเป็นอัตโนมัติสำหรับการประมวลผลเป็นชุดได้หรือไม่
ใช่ OMR ที่มีเกณฑ์ที่กำหนดเองสามารถทำให้เป็นอัตโนมัติสำหรับการประมวลผลภาพหลายภาพเป็นชุด ช่วยอำนวยความสะดวกในการดึงข้อมูลที่มีประสิทธิภาพในสถานการณ์ขนาดใหญ่
### ฉันจะค้นหาแหล่งข้อมูลเพิ่มเติมและการสนับสนุนสำหรับ Aspose.OMR สำหรับ .NET ได้ที่ไหน
 สำหรับเอกสาร การสนับสนุน และการโต้ตอบกับชุมชน โปรดไปที่[ฟอรั่ม Aspose.OMR](https://forum.aspose.com/c/omr/38) และ[เอกสารอย่างเป็นทางการ](https://reference.aspose.com/omr/net/).