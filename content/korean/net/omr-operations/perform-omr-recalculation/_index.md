---
title: .NET에서 OMR 재계산 수행
linktitle: .NET에서 OMR 재계산 수행
second_title: Aspose.OMR .NET API
description: .NET용 Aspose.OMR을 사용하여 .NET에서 광학 마크 인식 재계산을 수행하는 방법을 알아보세요. 스캔한 이미지의 데이터 정확성을 높이세요!
type: docs
weight: 12
url: /ko/net/omr-operations/perform-omr-recalculation/
---
이 튜토리얼에서는 .NET용 Aspose.OMR 라이브러리를 사용하여 .NET에서 광학 마크 인식(OMR) 재계산을 수행하는 과정을 안내합니다. OMR 재계산을 사용하면 사용자 정의 임계값을 기반으로 인식 결과를 조정할 수 있으므로 스캔한 이미지에서 데이터 추출의 정확성이 향상됩니다.
## 전제 조건
계속하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1. Visual Studio: .NET 개발을 위해 시스템에 Visual Studio를 설치합니다.
2.  .NET 라이브러리용 Aspose.OMR: 다음에서 .NET 라이브러리용 Aspose.OMR을 다운로드하고 설치합니다.[공식 웹 사이트](https://releases.aspose.com/omr/net/).
3. .NET 기본 지식: .NET 프레임워크 및 C# 프로그래밍 언어에 익숙해집니다.
## 네임스페이스 가져오기
필요한 네임스페이스를 가져오는 것부터 시작하세요.
```csharp
using Aspose.OMR.Api;
using Aspose.OMR.Model;
using System;
using System.Diagnostics;
using System.IO;
```
예제 코드를 세부 단계로 나누어 보겠습니다.
## 1단계: 템플릿 및 이미지 경로 정의
OMR 템플릿 및 사용자 이미지의 경로를 지정합니다.
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## 2단계: 폴더 설정
OMR 처리를 위한 입력 및 출력 디렉터리를 준비합니다.
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
int CustomThreshold = 40; // 맞춤 임계값 정의
```
## 3단계: 엔진 및 템플릿 프로세서 초기화
Aspose.OMR 엔진을 초기화하고 템플릿 프로세서를 얻습니다.
```csharp
OmrEngine engine = new OmrEngine();
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## 4단계: 사용자 이미지 처리
각 사용자 이미지를 반복하여 OMR 재계산을 수행합니다.
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string image = UserImages[i];
    string imagePath = Path.Combine(testFolderPath, image);
    Console.WriteLine("\n\rProcessing image: " + imagePath);
    // 수행 시간 측정
    Stopwatch sw = Stopwatch.StartNew();
    // 이미지 인식
    RecognitionResult result = templateProcessor.RecognizeImage(imagePath);
    sw.Stop();
    Console.WriteLine("Recognition time: " + sw.Elapsed);
    // 인식 결과를 CSV로 내보내기
    string stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"), stringRes);
    Console.WriteLine("Result Exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"));
    sw.Restart();
    // 사용자 정의 임계값을 사용하여 OMR 재계산 수행
    Console.WriteLine("\n\rPerforming recalculation\n\r");
    templateProcessor.Recalculate(result, CustomThreshold);
    sw.Stop();
    Console.WriteLine("Recalculation time: " + sw.Elapsed);
    // 다시 계산된 결과 내보내기
    stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"), stringRes);
    Console.WriteLine("Recalculation result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"));
}
```
## 5단계: 결론
.NET용 Aspose.OMR을 사용하여 .NET에서 광학 마크 인식 재계산을 성공적으로 수행했습니다. 이 기능을 사용하면 사용자 정의 임계값을 기반으로 인식 결과를 미세 조정하여 데이터 정확도를 높일 수 있습니다.
## 결론
결론적으로, .NET용 Aspose.OMR 라이브러리는 .NET 애플리케이션의 광학 마크 인식 작업을 위한 강력한 도구를 제공합니다. 이 튜토리얼에 설명된 단계를 따르면 OMR 재계산 기능을 프로젝트에 원활하게 통합하여 스캔한 이미지에서 데이터 추출의 정확성을 높일 수 있습니다.
## 자주 묻는 질문
### OMR 재계산이란 무엇이며, 왜 중요한가요?
OMR 재계산은 사용자 정의 임계값을 기반으로 인식 결과를 조정하는 프로세스입니다. 이는 특히 표준 인식이 충분하지 않은 시나리오에서 스캔한 이미지에서 데이터 추출의 정확성을 높이는 데 중요합니다.
### OMR 재계산은 표준 인식과 어떻게 다릅니까?
OMR 재계산을 사용하면 사용자 정의 임계값을 적용하여 인식 결과를 보다 세밀하게 조정할 수 있는 반면, 표준 인식은 사용자 개입 없이 미리 정의된 알고리즘을 따릅니다.
### .NET 애플리케이션에서 OMR 재계산을 자동화할 수 있습니까?
예, .NET용 Aspose.OMR 라이브러리를 통합하고 이미지 처리 및 인식 결과 조정을 위해 해당 API를 활용하여 .NET 애플리케이션에서 OMR 재계산을 자동화할 수 있습니다.
### OMR 재계산을 위한 사용자 정의 임계값을 결정할 때 어떤 요소를 고려해야 합니까?
OMR 재계산을 위한 사용자 정의 임계값을 결정할 때는 이미지 품질, 마크 밀도, 원하는 정확도 수준과 같은 요소를 고려해야 합니다.
### .NET용 Aspose.OMR에 대한 추가 리소스와 지원은 어디서 찾을 수 있나요?
 문서화, 지원 및 커뮤니티 상호 작용을 보려면 다음을 방문하세요.[Aspose.OMR 포럼](https://forum.aspose.com/c/omr/38) 그리고[공식 문서](https://reference.aspose.com/omr/net/).