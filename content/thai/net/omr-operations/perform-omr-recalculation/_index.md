---
title: ทำการคำนวณใหม่ OMR ใน .NET
linktitle: ทำการคำนวณใหม่ OMR ใน .NET
second_title: Aspose.OMR .NET API
description: เรียนรู้วิธีการคำนวณ Optical Mark Recognition ใหม่ใน .NET โดยใช้ Aspose.OMR สำหรับ .NET เพิ่มความแม่นยำของข้อมูลจากภาพที่สแกน!
type: docs
weight: 12
url: /th/net/omr-operations/perform-omr-recalculation/
---
ในบทช่วยสอนนี้ เราจะแนะนำคุณตลอดขั้นตอนการคำนวณ Optical Mark Recognition (OMR) ใหม่ใน .NET โดยใช้ Aspose.OMR สำหรับไลบรารี .NET การคำนวณ OMR ใหม่ช่วยให้คุณสามารถปรับผลลัพธ์การจดจำตามเกณฑ์ที่กำหนดเอง ซึ่งช่วยเพิ่มความแม่นยำในการดึงข้อมูลจากภาพที่สแกน
## ข้อกำหนดเบื้องต้น
ก่อนดำเนินการต่อ ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1. Visual Studio: ติดตั้ง Visual Studio บนระบบของคุณเพื่อการพัฒนา .NET
2.  Aspose.OMR สำหรับ .NET Library: ดาวน์โหลดและติดตั้งไลบรารี Aspose.OMR สำหรับ .NET จากไฟล์[เว็บไซต์อย่างเป็นทางการ](https://releases.aspose.com/omr/net/).
3. ความรู้พื้นฐานของ .NET: ทำความคุ้นเคยกับกรอบงาน .NET และภาษาการเขียนโปรแกรม C#
## นำเข้าเนมสเปซ
เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็น:
```csharp
using Aspose.OMR.Api;
using Aspose.OMR.Model;
using System;
using System.Diagnostics;
using System.IO;
```
มาแบ่งโค้ดตัวอย่างออกเป็นขั้นตอนโดยละเอียด:
## ขั้นตอนที่ 1: กำหนดเทมเพลตและเส้นทางรูปภาพ
ระบุเส้นทางสำหรับเทมเพลต OMR และรูปภาพผู้ใช้:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## ขั้นตอนที่ 2: ตั้งค่าโฟลเดอร์
เตรียมไดเร็กทอรีอินพุตและเอาต์พุตสำหรับการประมวลผล OMR:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
int CustomThreshold = 40; // กำหนดเกณฑ์ที่กำหนดเอง
```
## ขั้นตอนที่ 3: เริ่มต้นกลไกและตัวประมวลผลเทมเพลต
เตรียมใช้งานกลไก Aspose.OMR และรับตัวประมวลผลเทมเพลต:
```csharp
OmrEngine engine = new OmrEngine();
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## ขั้นตอนที่ 4: ประมวลผลรูปภาพของผู้ใช้
วนซ้ำอิมเมจผู้ใช้แต่ละอันเพื่อคำนวณ OMR ใหม่:
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string image = UserImages[i];
    string imagePath = Path.Combine(testFolderPath, image);
    Console.WriteLine("\n\rProcessing image: " + imagePath);
    // วัดเวลาประสิทธิภาพ
    Stopwatch sw = Stopwatch.StartNew();
    // รับรู้ถึงภาพ
    RecognitionResult result = templateProcessor.RecognizeImage(imagePath);
    sw.Stop();
    Console.WriteLine("Recognition time: " + sw.Elapsed);
    // ส่งออกผลการรับรู้เป็น CSV
    string stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"), stringRes);
    Console.WriteLine("Result Exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"));
    sw.Restart();
    // ดำเนินการคำนวณ OMR ใหม่ด้วยเกณฑ์ที่กำหนดเอง
    Console.WriteLine("\n\rPerforming recalculation\n\r");
    templateProcessor.Recalculate(result, CustomThreshold);
    sw.Stop();
    Console.WriteLine("Recalculation time: " + sw.Elapsed);
    // ส่งออกผลลัพธ์ที่คำนวณใหม่
    stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"), stringRes);
    Console.WriteLine("Recalculation result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"));
}
```
## ขั้นตอนที่ 5: บทสรุป
คุณดำเนินการคำนวณการจดจำเครื่องหมายด้วยแสงใหม่ใน .NET โดยใช้ Aspose.OMR สำหรับ .NET สำเร็จแล้ว คุณสมบัตินี้ช่วยให้คุณปรับแต่งผลลัพธ์การจดจำตามเกณฑ์ที่กำหนดเอง ปรับปรุงความแม่นยำของข้อมูล
## บทสรุป
โดยสรุป ไลบรารี Aspose.OMR สำหรับ .NET มอบเครื่องมืออันทรงพลังสำหรับงาน Optical Mark Recognition ในแอปพลิเคชัน .NET ด้วยการทำตามขั้นตอนที่ระบุไว้ในบทช่วยสอนนี้ คุณสามารถรวมความสามารถในการคำนวณ OMR ใหม่เข้ากับโปรเจ็กต์ของคุณได้อย่างราบรื่น ช่วยเพิ่มความแม่นยำในการดึงข้อมูลจากรูปภาพที่สแกน
## คำถามที่พบบ่อย
### การคำนวณ OMR ใหม่คืออะไร และเหตุใดจึงสำคัญ
การคำนวณ OMR ใหม่คือกระบวนการปรับผลลัพธ์การจดจำตามเกณฑ์ที่กำหนดเอง การปรับปรุงความแม่นยำในการดึงข้อมูลจากภาพที่สแกนเป็นสิ่งสำคัญ โดยเฉพาะอย่างยิ่งในสถานการณ์ที่การจดจำมาตรฐานอาจไม่เพียงพอ
### การคำนวณ OMR ใหม่แตกต่างจากการรับรู้มาตรฐานอย่างไร
การคำนวณ OMR ใหม่ช่วยให้สามารถปรับผลลัพธ์การจดจำได้ละเอียดยิ่งขึ้นโดยการใช้เกณฑ์ที่กำหนดเอง ในขณะที่การจดจำมาตรฐานเป็นไปตามอัลกอริธึมที่กำหนดไว้ล่วงหน้าโดยที่ผู้ใช้ไม่ต้องดำเนินการใด ๆ
### การคำนวณ OMR ใหม่สามารถทำโดยอัตโนมัติในแอปพลิเคชัน .NET ได้หรือไม่
ใช่ การคำนวณ OMR ใหม่สามารถทำได้โดยอัตโนมัติในแอปพลิเคชัน .NET โดยการผสานรวม Aspose.OMR สำหรับไลบรารี .NET และใช้ API สำหรับการประมวลผลรูปภาพและปรับผลการจดจำ
### ปัจจัยใดที่ควรพิจารณาเมื่อกำหนดเกณฑ์ที่กำหนดเองสำหรับการคำนวณ OMR ใหม่
ควรพิจารณาปัจจัยต่างๆ เช่น คุณภาพของภาพ ความหนาแน่นของเครื่องหมาย และระดับความแม่นยำที่ต้องการเมื่อกำหนดเกณฑ์ที่กำหนดเองสำหรับการคำนวณ OMR ใหม่
### ฉันจะค้นหาแหล่งข้อมูลเพิ่มเติมและการสนับสนุนสำหรับ Aspose.OMR สำหรับ .NET ได้ที่ไหน
 สำหรับเอกสาร การสนับสนุน และการโต้ตอบกับชุมชน โปรดไปที่[ฟอรั่ม Aspose.OMR](https://forum.aspose.com/c/omr/38) และ[เอกสารอย่างเป็นทางการ](https://reference.aspose.com/omr/net/).