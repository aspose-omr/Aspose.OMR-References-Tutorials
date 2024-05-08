---
title: Lakukan Perhitungan Ulang OMR di .NET
linktitle: Lakukan Perhitungan Ulang OMR di .NET
second_title: Asumsikan.OMR .NET API
description: Pelajari cara melakukan penghitungan ulang Pengenalan Tanda Optik di .NET menggunakan Aspose.OMR untuk .NET. Tingkatkan akurasi data dari gambar yang dipindai!
type: docs
weight: 12
url: /id/net/omr-operations/perform-omr-recalculation/
---
Dalam tutorial ini, kami akan memandu Anda melalui proses melakukan penghitungan ulang Optical Mark Recognition (OMR) di .NET menggunakan pustaka Aspose.OMR untuk .NET. Penghitungan ulang OMR memungkinkan Anda menyesuaikan hasil pengenalan berdasarkan ambang batas khusus, sehingga meningkatkan keakuratan ekstraksi data dari gambar yang dipindai.
## Prasyarat
Sebelum melanjutkan, pastikan Anda memiliki prasyarat berikut:
1. Visual Studio: Instal Visual Studio di sistem Anda untuk pengembangan .NET.
2.  Aspose.OMR untuk .NET Library: Unduh dan instal Aspose.OMR untuk .NET Library dari[situs web resmi](https://releases.aspose.com/omr/net/).
3. Pengetahuan Dasar tentang .NET: Biasakan diri Anda dengan kerangka .NET dan bahasa pemrograman C#.
## Impor Namespace
Mulailah dengan mengimpor namespace yang diperlukan:
```csharp
using Aspose.OMR.Api;
using Aspose.OMR.Model;
using System;
using System.Diagnostics;
using System.IO;
```
Mari kita pecahkan kode contoh menjadi langkah-langkah mendetail:
## Langkah 1: Tentukan Templat dan Jalur Gambar
Tentukan jalur untuk template OMR dan gambar pengguna:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## Langkah 2: Siapkan Folder
Siapkan direktori input dan output untuk pemrosesan OMR:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
int CustomThreshold = 40; // Tentukan ambang batas khusus
```
## Langkah 3: Inisialisasi Mesin dan Prosesor Template
Inisialisasi mesin Aspose.OMR dan dapatkan prosesor templat:
```csharp
OmrEngine engine = new OmrEngine();
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## Langkah 4: Proses Gambar Pengguna
Ulangi setiap gambar pengguna untuk melakukan penghitungan ulang OMR:
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string image = UserImages[i];
    string imagePath = Path.Combine(testFolderPath, image);
    Console.WriteLine("\n\rProcessing image: " + imagePath);
    // Ukur waktu kinerja
    Stopwatch sw = Stopwatch.StartNew();
    // Kenali gambar
    RecognitionResult result = templateProcessor.RecognizeImage(imagePath);
    sw.Stop();
    Console.WriteLine("Recognition time: " + sw.Elapsed);
    // Ekspor hasil pengakuan ke CSV
    string stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"), stringRes);
    Console.WriteLine("Result Exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"));
    sw.Restart();
    // Lakukan penghitungan ulang OMR dengan ambang batas khusus
    Console.WriteLine("\n\rPerforming recalculation\n\r");
    templateProcessor.Recalculate(result, CustomThreshold);
    sw.Stop();
    Console.WriteLine("Recalculation time: " + sw.Elapsed);
    // Ekspor hasil perhitungan ulang
    stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"), stringRes);
    Console.WriteLine("Recalculation result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"));
}
```
## Langkah 5: Kesimpulan
Anda telah berhasil melakukan penghitungan ulang Pengenalan Tanda Optik di .NET menggunakan Aspose.OMR untuk .NET. Fitur ini memungkinkan Anda menyempurnakan hasil pengenalan berdasarkan ambang batas khusus, sehingga meningkatkan akurasi data.
## Kesimpulan
Kesimpulannya, pustaka Aspose.OMR untuk .NET menyediakan alat canggih untuk tugas Pengenalan Tanda Optik dalam aplikasi .NET. Dengan mengikuti langkah-langkah yang diuraikan dalam tutorial ini, Anda dapat dengan mudah mengintegrasikan kemampuan penghitungan ulang OMR ke dalam proyek Anda, sehingga meningkatkan keakuratan ekstraksi data dari gambar yang dipindai.
## Pertanyaan yang Sering Diajukan
### Apa itu penghitungan ulang OMR dan mengapa penting?
Penghitungan ulang OMR adalah proses penyesuaian hasil pengenalan berdasarkan ambang batas khusus. Hal ini penting untuk meningkatkan keakuratan ekstraksi data dari gambar yang dipindai, terutama dalam skenario di mana pengenalan standar mungkin tidak cukup.
### Apa perbedaan penghitungan ulang OMR dengan pengakuan standar?
Penghitungan ulang OMR memungkinkan penyesuaian yang lebih baik terhadap hasil pengenalan dengan menerapkan ambang batas khusus, sedangkan pengenalan standar mengikuti algoritme yang telah ditentukan sebelumnya tanpa campur tangan pengguna.
### Bisakah penghitungan ulang OMR diotomatiskan dalam aplikasi .NET?
Ya, penghitungan ulang OMR dapat diotomatiskan dalam aplikasi .NET dengan mengintegrasikan pustaka Aspose.OMR untuk .NET dan memanfaatkan API-nya untuk memproses gambar dan menyesuaikan hasil pengenalan.
### Faktor apa saja yang harus dipertimbangkan saat menentukan ambang batas khusus untuk penghitungan ulang OMR?
Faktor-faktor seperti kualitas gambar, kepadatan tanda, dan tingkat akurasi yang diinginkan harus dipertimbangkan saat menentukan ambang batas khusus untuk penghitungan ulang OMR.
### Di mana saya dapat menemukan sumber daya tambahan dan dukungan untuk Aspose.OMR untuk .NET?
 Untuk dokumentasi, dukungan, dan interaksi komunitas, kunjungi[Forum Aspose.OMR](https://forum.aspose.com/c/omr/38) Dan[dokumentasi resmi](https://reference.aspose.com/omr/net/).