---
title: Lakukan OMR pada Gambar di .NET
linktitle: Lakukan OMR pada Gambar di .NET
second_title: Asumsikan.OMR .NET API
description: Pelajari cara melakukan Pengenalan Tanda Optik pada gambar di .NET menggunakan Aspose.OMR untuk .NET. Sederhanakan ekstraksi data dari formulir berbasis gambar!
type: docs
weight: 11
url: /id/net/omr-operations/perform-omr-on-images/
---
Dalam tutorial ini, kami akan memandu Anda melalui proses melakukan Pengenalan Tanda Optik (OMR) pada gambar di .NET menggunakan pustaka Aspose.OMR untuk .NET. OMR adalah teknik yang digunakan untuk mengenali dan mengekstrak data dari area yang ditandai pada gambar, sehingga sangat berharga untuk tugas-tugas seperti survei, penilaian, dan pengumpulan data.
## Prasyarat
Sebelum kita mulai, pastikan Anda memiliki prasyarat berikut:
1. Visual Studio: Pastikan Anda telah menginstal Visual Studio di sistem Anda.
2.  Aspose.OMR untuk .NET Library: Unduh dan instal Aspose.OMR untuk .NET Library dari[rilis](https://releases.aspose.com/omr/net/).
3. Pengetahuan Dasar tentang .NET: Biasakan diri Anda dengan kerangka .NET dan bahasa pemrograman C#.
## Impor Namespace
Mulailah dengan mengimpor namespace yang diperlukan:
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
Mari kita pecahkan kode contoh menjadi beberapa langkah untuk kejelasan:
## Langkah 1: Tentukan Templat dan Jalur Gambar Pengguna
Pertama, tentukan jalur untuk template OMR dan gambar pengguna:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## Langkah 2: Siapkan Input dan Output
Siapkan direktori input dan output untuk pemrosesan OMR:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
```
## Langkah 3: Inisialisasi Mesin OMR
Inisialisasi mesin Aspose.OMR untuk mulai memproses:
```csharp
OmrEngine engine = new OmrEngine();
```
## Langkah 4: Muat Templat
Muat templat OMR ke dalam pemroses templat:
```csharp
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## Langkah 5: Ulangi Melalui Gambar Pengguna
Ulangi setiap gambar pengguna untuk melakukan OMR:
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string imagePath = Path.Combine(testFolderPath, UserImages[i]);
    string csvResult = templateProcessor.RecognizeImage(imagePath).GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"), csvResult);
    Console.WriteLine("Result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"));
}
```
## Langkah 6: Kesimpulan
Anda telah berhasil melakukan Pengenalan Tanda Optik pada gambar di .NET menggunakan Aspose.OMR untuk .NET. Kemampuan ini menyederhanakan ekstraksi data dari gambar, memfasilitasi berbagai aplikasi seperti survei dan penilaian.
## Kesimpulan
Kesimpulannya, pustaka Aspose.OMR untuk .NET memberikan solusi canggih untuk tugas Pengenalan Tanda Optik di aplikasi .NET. Dengan mengikuti langkah-langkah yang dijelaskan dalam tutorial ini, Anda dapat dengan mudah mengintegrasikan fungsi OMR ke dalam proyek Anda, sehingga memungkinkan ekstraksi data yang efisien dari gambar.
## Pertanyaan yang Sering Diajukan
### Bisakah Aspose.OMR untuk .NET menangani banyak gambar secara bersamaan?
Ya, Aspose.OMR untuk .NET mendukung pemrosesan batch beberapa gambar, memungkinkan penanganan kumpulan data besar secara efisien.
### Jenis pengenalan tanda apa yang didukung Aspose.OMR untuk .NET?
Aspose.OMR untuk .NET mendukung berbagai jenis pengenalan tanda, termasuk kotak centang, gelembung, dan kisi.
### Apakah mungkin untuk menyesuaikan templat OMR agar sesuai dengan formulir tertentu?
Tentu saja, Anda dapat membuat dan menyesuaikan template OMR menggunakan Aspose.OMR Template Editor, menyesuaikannya dengan kebutuhan Anda.
### Apakah Aspose.OMR untuk .NET menawarkan dukungan untuk gambar miring?
Ya, Aspose.OMR untuk .NET menyertakan fitur untuk menangani gambar miring dan diputar, memastikan pengenalan tanda yang akurat.
### Di mana saya dapat menemukan dukungan dan sumber daya untuk Aspose.OMR untuk .NET?
 Untuk dukungan, dokumentasi, dan interaksi komunitas, kunjungi[Forum Aspose.OMR](https://forum.aspose.com/c/omr/38) Dan[dokumentasi resmi](https://reference.aspose.com/omr/net/).