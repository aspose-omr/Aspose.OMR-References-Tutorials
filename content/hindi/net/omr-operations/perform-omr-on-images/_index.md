---
title: .NET में छवियों पर OMR निष्पादित करें
linktitle: .NET में छवियों पर OMR निष्पादित करें
second_title: Aspose.OMR .NET एपीआई
description: .NET के लिए Aspose.OMR का उपयोग करके .NET में छवियों पर ऑप्टिकल मार्क रिकॉग्निशन करना सीखें। छवि-आधारित प्रपत्रों से डेटा निष्कर्षण को सुव्यवस्थित करें!
type: docs
weight: 11
url: /hi/net/omr-operations/perform-omr-on-images/
---
इस ट्यूटोरियल में, हम आपको Aspose.OMR for .NET लाइब्रेरी का उपयोग करके .NET में छवियों पर ऑप्टिकल मार्क रिकॉग्निशन (OMR) करने की प्रक्रिया से परिचित कराएँगे। OMR एक ऐसी तकनीक है जिसका उपयोग छवियों पर चिह्नित क्षेत्रों से डेटा को पहचानने और निकालने के लिए किया जाता है, जो इसे सर्वेक्षण, आकलन और डेटा संग्रह जैसे कार्यों के लिए अमूल्य बनाता है।
## आवश्यक शर्तें
शुरू करने से पहले, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ हैं:
1. विज़ुअल स्टूडियो: सुनिश्चित करें कि आपके सिस्टम पर विज़ुअल स्टूडियो स्थापित है।
2.  .NET लाइब्रेरी के लिए Aspose.OMR: .NET लाइब्रेरी के लिए Aspose.OMR को डाउनलोड और इंस्टॉल करें।[विज्ञप्ति](https://releases.aspose.com/omr/net/).
3. .NET का बुनियादी ज्ञान: .NET फ्रेमवर्क और C# प्रोग्रामिंग भाषा से स्वयं को परिचित कराएं।
## नामस्थान आयात करें
आवश्यक नामस्थानों को आयात करके प्रारंभ करें:
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
स्पष्टता के लिए आइए उदाहरण कोड को कई चरणों में विभाजित करें:
## चरण 1: टेम्पलेट और उपयोगकर्ता छवि पथ परिभाषित करें
सबसे पहले, OMR टेम्पलेट और उपयोगकर्ता छवियों के लिए पथ निर्दिष्ट करें:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## चरण 2: इनपुट और आउटपुट तैयार करें
OMR प्रसंस्करण के लिए इनपुट और आउटपुट निर्देशिका तैयार करें:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
```
## चरण 3: OMR इंजन आरंभ करें
प्रसंस्करण शुरू करने के लिए Aspose.OMR इंजन को प्रारंभ करें:
```csharp
OmrEngine engine = new OmrEngine();
```
## चरण 4: टेम्पलेट लोड करें
OMR टेम्पलेट को टेम्पलेट प्रोसेसर में लोड करें:
```csharp
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## चरण 5: उपयोगकर्ता छवियों के माध्यम से पुनरावृति करें
OMR निष्पादित करने के लिए प्रत्येक उपयोगकर्ता छवि के माध्यम से पुनरावृति करें:
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string imagePath = Path.Combine(testFolderPath, UserImages[i]);
    string csvResult = templateProcessor.RecognizeImage(imagePath).GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"), csvResult);
    Console.WriteLine("Result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"));
}
```
## चरण 6: निष्कर्ष
आपने .NET के लिए Aspose.OMR का उपयोग करके .NET में छवियों पर ऑप्टिकल मार्क रिकॉग्निशन सफलतापूर्वक निष्पादित किया है। यह क्षमता छवियों से डेटा निकालने को सुव्यवस्थित करती है, सर्वेक्षण और मूल्यांकन जैसे विभिन्न अनुप्रयोगों को सुविधाजनक बनाती है।
## निष्कर्ष
अंत में, .NET लाइब्रेरी के लिए Aspose.OMR .NET अनुप्रयोगों में ऑप्टिकल मार्क रिकग्निशन कार्यों के लिए एक शक्तिशाली समाधान प्रदान करता है। इस ट्यूटोरियल में उल्लिखित चरणों का पालन करके, आप छवियों से कुशल डेटा निष्कर्षण को सक्षम करते हुए, अपनी परियोजनाओं में ओएमआर कार्यक्षमता को सहजता से एकीकृत कर सकते हैं।
## अक्सर पूछे जाने वाले प्रश्नों
### क्या .NET के लिए Aspose.OMR एक साथ कई छवियों को संभाल सकता है?
हां, .NET के लिए Aspose.OMR कई छवियों के बैच प्रोसेसिंग का समर्थन करता है, जिससे बड़े डेटासेट के कुशल प्रबंधन की अनुमति मिलती है।
### .NET के लिए Aspose.OMR किस प्रकार की मार्क पहचान का समर्थन करता है?
.NET के लिए Aspose.OMR चेकबॉक्स, बबल और ग्रिड सहित विभिन्न चिह्न पहचान प्रकारों का समर्थन करता है।
### क्या विशिष्ट प्रपत्रों से मेल खाने के लिए ओएमआर टेम्पलेट्स को अनुकूलित करना संभव है?
बिल्कुल, आप Aspose.OMR टेम्पलेट संपादक का उपयोग करके OMR टेम्पलेट्स बना और अनुकूलित कर सकते हैं, उन्हें अपनी सटीक आवश्यकताओं के अनुरूप बना सकते हैं।
### क्या .NET के लिए Aspose.OMR तिरछी छवियों के लिए समर्थन प्रदान करता है?
हां, .NET के लिए Aspose.OMR में तिरछी और घुमावदार छवियों को संभालने की विशेषताएं शामिल हैं, जो सटीक चिह्न पहचान सुनिश्चित करती हैं।
### मैं .NET के लिए Aspose.OMR हेतु समर्थन और संसाधन कहां पा सकता हूं?
 सहायता, दस्तावेज़ीकरण और सामुदायिक संपर्क के लिए, यहां जाएं[Aspose.OMR फोरम](https://forum.aspose.com/c/omr/38) और[आधिकारिक दस्तावेज](https://reference.aspose.com/omr/net/).