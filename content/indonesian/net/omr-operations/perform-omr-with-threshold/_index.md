---
title: Lakukan OMR dengan Threshold di .NET
linktitle: Lakukan OMR dengan Threshold di .NET
second_title: Asumsikan.OMR .NET API
description: Pelajari cara melakukan Pengenalan Tanda Optik dengan ambang batas khusus di .NET menggunakan Aspose.OMR untuk .NET. Tingkatkan akurasi data dari gambar yang dipindai!
type: docs
weight: 13
url: /id/net/omr-operations/perform-omr-with-threshold/
---
Pengenalan Tanda Optik (OMR) adalah teknologi penting untuk mengekstraksi data dari gambar pindaian yang berisi area yang ditandai. Dalam tutorial ini, kita akan mempelajari cara melakukan OMR dengan ambang batas kustom di .NET menggunakan pustaka Aspose.OMR untuk .NET. Fitur ini memungkinkan penyesuaian proses pengenalan berdasarkan kebutuhan spesifik, sehingga meningkatkan akurasi.
## Prasyarat
Sebelum kita mempelajari tutorialnya, pastikan Anda memiliki prasyarat berikut:
1. Visual Studio: Instal Visual Studio di sistem Anda untuk pengembangan .NET.
2.  Aspose.OMR untuk .NET Library: Unduh dan instal Aspose.OMR untuk .NET Library dari[situs web resmi](https://releases.aspose.com/omr/net/).
3. Pengetahuan Dasar tentang .NET: Biasakan diri Anda dengan kerangka .NET dan bahasa pemrograman C#.
## Impor Namespace
Mulailah dengan mengimpor namespace yang diperlukan:
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
Mari kita pecahkan kode contoh menjadi langkah-langkah mendetail:
## Langkah 1: Tentukan Templat dan Jalur Gambar
Tentukan jalur untuk template OMR dan gambar pengguna:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## Langkah 2: Tetapkan Ambang Batas Kustom
Tentukan ambang batas khusus untuk pemrosesan OMR:
```csharp
int CustomThreshold = 40;
```
## Langkah 3: Siapkan Input dan Output
Siapkan direktori input dan output untuk pemrosesan OMR:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
```
## Langkah 4: Inisialisasi Mesin dan Prosesor Template
Inisialisasi mesin Aspose.OMR dan dapatkan prosesor templat:
```csharp
OmrEngine engine = new OmrEngine();
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## Langkah 5: Lakukan OMR dengan Ambang Batas Kustom
Ulangi setiap gambar pengguna dan lakukan OMR dengan ambang batas khusus:
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
## Kesimpulan
Dengan mengikuti tutorial ini, Anda telah mempelajari cara melakukan Pengenalan Tanda Optik dengan ambang batas kustom di .NET menggunakan pustaka Aspose.OMR untuk .NET. Kemampuan ini memberdayakan Anda untuk menyempurnakan proses pengenalan, sehingga meningkatkan keakuratan ekstraksi data dari gambar yang dipindai.
## Pertanyaan yang Sering Diajukan
### Apa pentingnya menggunakan ambang batas khusus di OMR?
Ambang batas khusus memungkinkan pengguna menyesuaikan sensitivitas proses pengenalan, sehingga mengoptimalkan akurasi berdasarkan karakteristik dan persyaratan gambar tertentu.
### Apa perbedaan OMR dengan ambang batas khusus dengan OMR standar?
OMR standar menerapkan ambang batas yang telah ditentukan sebelumnya untuk deteksi tanda, sedangkan OMR dengan ambang batas khusus memungkinkan pengguna menentukan dan menyempurnakan parameter pengenalan sesuai kebutuhan mereka.
### Faktor apa saja yang harus dipertimbangkan saat menetapkan ambang batas khusus untuk OMR?
Faktor-faktor seperti kualitas gambar, intensitas tanda, dan tingkat kebisingan latar belakang harus diperhitungkan saat menentukan ambang batas khusus yang sesuai untuk OMR.
### Bisakah OMR dengan ambang batas khusus diotomatisasi untuk pemrosesan batch?
Ya, OMR dengan ambang batas khusus dapat diotomatisasi untuk pemrosesan batch beberapa gambar, sehingga memfasilitasi ekstraksi data yang efisien dalam skenario skala besar.
### Di mana saya dapat menemukan sumber daya tambahan dan dukungan untuk Aspose.OMR untuk .NET?
 Untuk dokumentasi, dukungan, dan interaksi komunitas, kunjungi[Forum Aspose.OMR](https://forum.aspose.com/c/omr/38) Dan[dokumentasi resmi](https://reference.aspose.com/omr/net/).