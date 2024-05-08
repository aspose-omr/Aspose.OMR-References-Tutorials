---
title: .NET'teki Görüntülerde OMR gerçekleştirin
linktitle: .NET'teki Görüntülerde OMR gerçekleştirin
second_title: Aspose.OMR .NET API'si
description: Aspose.OMR for .NET kullanarak .NET'teki görüntülerde Optik İşaret Tanıma işleminin nasıl gerçekleştirileceğini öğrenin. Görüntü tabanlı formlardan veri çıkarmayı kolaylaştırın!
type: docs
weight: 11
url: /tr/net/omr-operations/perform-omr-on-images/
---
Bu eğitimde, Aspose.OMR for .NET kitaplığını kullanarak .NET'teki görüntüler üzerinde Optik İşaret Tanıma (OMR) gerçekleştirme sürecinde size yol göstereceğiz. OMR, görüntülerdeki işaretli alanlardaki verileri tanımak ve çıkarmak için kullanılan bir tekniktir; bu da onu anketler, değerlendirmeler ve veri toplama gibi görevler için paha biçilmez kılar.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşullara sahip olduğunuzdan emin olun:
1. Visual Studio: Sisteminizde Visual Studio'nun kurulu olduğundan emin olun.
2.  Aspose.OMR for .NET Kütüphanesi: Aspose.OMR for .NET kütüphanesini aşağıdaki adresten indirip yükleyin:[Salıverme](https://releases.aspose.com/omr/net/).
3. Temel .NET Bilgisi: .NET framework'üne ve C# programlama diline aşina olun.
## Ad Alanlarını İçe Aktar
Gerekli ad alanlarını içe aktararak başlayın:
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
Açıklık sağlamak için örnek kodu birden fazla adıma ayıralım:
## 1. Adım: Şablon ve Kullanıcı Görüntü Yollarını Tanımlayın
İlk olarak OMR şablonunun ve kullanıcı görsellerinin yollarını belirtin:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## Adım 2: Giriş ve Çıkışı Hazırlayın
OMR işleme için giriş ve çıkış dizinlerini hazırlayın:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
```
## 3. Adım: OMR Motorunu Başlatın
İşlemeyi başlatmak için Aspose.OMR motorunu başlatın:
```csharp
OmrEngine engine = new OmrEngine();
```
## Adım 4: Şablonu Yükleyin
OMR şablonunu şablon işlemcisine yükleyin:
```csharp
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## Adım 5: Kullanıcı Görselleri Üzerinden Yineleme Yapın
OMR gerçekleştirmek için her kullanıcı görüntüsünü yineleyin:
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string imagePath = Path.Combine(testFolderPath, UserImages[i]);
    string csvResult = templateProcessor.RecognizeImage(imagePath).GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"), csvResult);
    Console.WriteLine("Result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"));
}
```
## Adım 6: Sonuç
Aspose.OMR for .NET'i kullanarak .NET'teki görüntüler üzerinde Optik İşaret Tanıma işlemini başarıyla gerçekleştirdiniz. Bu özellik, görüntülerden veri çıkarılmasını kolaylaştırarak anketler ve değerlendirmeler gibi çeşitli uygulamaları kolaylaştırır.
## Çözüm
Sonuç olarak Aspose.OMR for .NET kitaplığı, .NET uygulamalarındaki Optik İşaret Tanıma görevleri için güçlü bir çözüm sunar. Bu eğitimde özetlenen adımları izleyerek OMR işlevini projelerinize sorunsuz bir şekilde entegre edebilir, görüntülerden verimli veri çıkarmayı mümkün kılabilirsiniz.
## Sıkça Sorulan Sorular
### Aspose.OMR for .NET aynı anda birden fazla görüntüyü işleyebilir mi?
Evet, Aspose.OMR for .NET, birden fazla görüntünün toplu işlenmesini destekleyerek büyük veri kümelerinin verimli şekilde işlenmesine olanak tanır.
### Aspose.OMR for .NET ne tür işaret tanımayı destekler?
Aspose.OMR for .NET, onay kutuları, kabarcıklar ve ızgaralar dahil olmak üzere çeşitli işaret tanıma türlerini destekler.
### OMR şablonlarını belirli formlarla eşleşecek şekilde özelleştirmek mümkün müdür?
Kesinlikle, Aspose.OMR Şablon Düzenleyicisini kullanarak OMR şablonlarını oluşturabilir ve özelleştirebilirsiniz, bunları tam gereksinimlerinize göre ayarlayabilirsiniz.
### Aspose.OMR for .NET çarpık görüntüler için destek sunuyor mu?
Evet, Aspose.OMR for .NET, çarpık ve döndürülmüş görüntüleri işlemek için özellikler içerir ve doğru işaret tanıma sağlar.
### Aspose.OMR for .NET için desteği ve kaynakları nerede bulabilirim?
 Destek, dokümantasyon ve topluluk etkileşimi için şu adresi ziyaret edin:[Aspose.OMR forumu](https://forum.aspose.com/c/omr/38) Ve[resmi belgeler](https://reference.aspose.com/omr/net/).