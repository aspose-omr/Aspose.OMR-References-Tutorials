---
title: .NET'te OMR Yeniden Hesaplamasını Gerçekleştirin
linktitle: .NET'te OMR Yeniden Hesaplamasını Gerçekleştirin
second_title: Aspose.OMR .NET API'si
description: Aspose.OMR for .NET'i kullanarak .NET'te Optik İşaret Tanıma yeniden hesaplamasını nasıl gerçekleştireceğinizi öğrenin. Taranan görüntülerdeki veri doğruluğunu artırın!
type: docs
weight: 12
url: /tr/net/omr-operations/perform-omr-recalculation/
---
Bu eğitimde, Aspose.OMR for .NET kitaplığını kullanarak .NET'te Optik İşaret Tanıma (OMR) yeniden hesaplaması gerçekleştirme sürecinde size rehberlik edeceğiz. OMR yeniden hesaplaması, taranan görüntülerden veri çıkarma doğruluğunu artırarak tanıma sonuçlarını özel eşiklere göre ayarlamanıza olanak tanır.
## Önkoşullar
Devam etmeden önce aşağıdaki önkoşullara sahip olduğunuzdan emin olun:
1. Visual Studio: .NET geliştirme için sisteminize Visual Studio'yu yükleyin.
2.  Aspose.OMR for .NET Kütüphanesi: Aspose.OMR for .NET kütüphanesini aşağıdaki adresten indirip yükleyin:[resmi internet sitesi](https://releases.aspose.com/omr/net/).
3. Temel .NET Bilgisi: .NET framework'üne ve C# programlama diline aşina olun.
## Ad Alanlarını İçe Aktar
Gerekli ad alanlarını içe aktararak başlayın:
```csharp
using Aspose.OMR.Api;
using Aspose.OMR.Model;
using System;
using System.Diagnostics;
using System.IO;
```
Örnek kodu ayrıntılı adımlara ayıralım:
## 1. Adım: Şablon ve Görüntü Yollarını Tanımlayın
OMR şablonu ve kullanıcı görüntüleri için yolları belirtin:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## Adım 2: Klasörleri Ayarlayın
OMR işleme için giriş ve çıkış dizinlerini hazırlayın:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
int CustomThreshold = 40; // Özel eşiği tanımlayın
```
## 3. Adım: Motoru ve Şablon İşlemcisini Başlatın
Aspose.OMR motorunu başlatın ve şablon işlemciyi edinin:
```csharp
OmrEngine engine = new OmrEngine();
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## 4. Adım: Kullanıcı Görüntülerini İşleyin
OMR yeniden hesaplamasını gerçekleştirmek için her kullanıcı görüntüsünü yineleyin:
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string image = UserImages[i];
    string imagePath = Path.Combine(testFolderPath, image);
    Console.WriteLine("\n\rProcessing image: " + imagePath);
    // Performans süresini ölçün
    Stopwatch sw = Stopwatch.StartNew();
    // Resmi tanı
    RecognitionResult result = templateProcessor.RecognizeImage(imagePath);
    sw.Stop();
    Console.WriteLine("Recognition time: " + sw.Elapsed);
    // Tanıma sonuçlarını CSV'ye aktar
    string stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"), stringRes);
    Console.WriteLine("Result Exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"));
    sw.Restart();
    // Özel eşikle OMR yeniden hesaplamasını gerçekleştirin
    Console.WriteLine("\n\rPerforming recalculation\n\r");
    templateProcessor.Recalculate(result, CustomThreshold);
    sw.Stop();
    Console.WriteLine("Recalculation time: " + sw.Elapsed);
    // Yeniden hesaplanan sonuçları dışa aktar
    stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"), stringRes);
    Console.WriteLine("Recalculation result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"));
}
```
## Adım 5: Sonuç
Aspose.OMR for .NET'i kullanarak .NET'te Optik İşaret Tanıma yeniden hesaplamasını başarıyla gerçekleştirdiniz. Bu özellik, özel eşiklere göre tanıma sonuçlarında ince ayar yapmanızı sağlayarak veri doğruluğunu artırır.
## Çözüm
Sonuç olarak Aspose.OMR for .NET kitaplığı, .NET uygulamalarındaki Optik İşaret Tanıma görevleri için güçlü araçlar sağlar. Bu eğitimde özetlenen adımları izleyerek OMR yeniden hesaplama yeteneklerini projelerinize sorunsuz bir şekilde entegre edebilir, taranan görüntülerden veri çıkarma doğruluğunu artırabilirsiniz.
## Sıkça Sorulan Sorular
### OMR yeniden hesaplaması nedir ve neden önemlidir?
OMR yeniden hesaplaması, tanıma sonuçlarını özel eşiklere göre ayarlama işlemidir. Özellikle standart tanımanın yeterli olmayabileceği senaryolarda, taranan görüntülerden veri çıkarma doğruluğunun artırılması açısından önemlidir.
### OMR yeniden hesaplamasının standart tanımadan farkı nedir?
OMR yeniden hesaplaması, özel eşikler uygulayarak tanıma sonuçlarında daha hassas ayarlamalar yapılmasını sağlarken standart tanıma, kullanıcı müdahalesi olmadan önceden tanımlanmış algoritmaları takip eder.
### OMR yeniden hesaplaması .NET uygulamalarında otomatikleştirilebilir mi?
Evet, OMR yeniden hesaplaması, Aspose.OMR for .NET kitaplığının entegre edilmesi ve görüntülerin işlenmesi ve tanıma sonuçlarının ayarlanması için API'sinden yararlanılarak .NET uygulamalarında otomatikleştirilebilir.
### OMR yeniden hesaplaması için özel eşiği belirlerken hangi faktörler dikkate alınmalıdır?
OMR yeniden hesaplaması için özel eşiği belirlerken görüntü kalitesi, işaret yoğunluğu ve istenen doğruluk düzeyi gibi faktörler dikkate alınmalıdır.
### Aspose.OMR for .NET için ek kaynakları ve desteği nerede bulabilirim?
 Belgeler, destek ve topluluk etkileşimi için şu adresi ziyaret edin:[Aspose.OMR forumu](https://forum.aspose.com/c/omr/38) Ve[resmi belgeler](https://reference.aspose.com/omr/net/).