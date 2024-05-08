---
title: .NET에서 임계값을 사용하여 OMR 수행
linktitle: .NET에서 임계값을 사용하여 OMR 수행
second_title: Aspose.OMR .NET API
description: .NET용 Aspose.OMR을 사용하여 .NET에서 사용자 정의 임계값으로 광학 마크 인식을 수행하는 방법을 알아보세요. 스캔한 이미지의 데이터 정확성을 높이세요!
type: docs
weight: 13
url: /ko/net/omr-operations/perform-omr-with-threshold/
---
광학 마크 인식(OMR)은 표시된 영역이 포함된 스캔 이미지에서 데이터를 추출하는 데 중요한 기술입니다. 이 튜토리얼에서는 .NET용 Aspose.OMR 라이브러리를 사용하여 .NET에서 사용자 정의 임계값으로 OMR을 수행하는 방법을 살펴보겠습니다. 이 기능을 사용하면 특정 요구 사항에 따라 인식 프로세스를 미세 조정할 수 있으므로 정확도가 향상됩니다.
## 전제 조건
튜토리얼을 자세히 살펴보기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1. Visual Studio: .NET 개발을 위해 시스템에 Visual Studio를 설치합니다.
2.  .NET 라이브러리용 Aspose.OMR: 다음에서 .NET 라이브러리용 Aspose.OMR을 다운로드하고 설치합니다.[공식 웹 사이트](https://releases.aspose.com/omr/net/).
3. .NET 기본 지식: .NET 프레임워크 및 C# 프로그래밍 언어에 익숙해집니다.
## 네임스페이스 가져오기
필요한 네임스페이스를 가져오는 것부터 시작하세요.
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
예제 코드를 세부 단계로 나누어 보겠습니다.
## 1단계: 템플릿 및 이미지 경로 정의
OMR 템플릿 및 사용자 이미지의 경로를 지정합니다.
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## 2단계: 사용자 정의 임계값 설정
OMR 처리를 위한 사용자 정의 임계값을 정의합니다.
```csharp
int CustomThreshold = 40;
```
## 3단계: 입력 및 출력 준비
OMR 처리를 위한 입력 및 출력 디렉터리를 준비합니다.
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
```
## 4단계: 엔진 및 템플릿 프로세서 초기화
Aspose.OMR 엔진을 초기화하고 템플릿 프로세서를 얻습니다.
```csharp
OmrEngine engine = new OmrEngine();
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## 5단계: 사용자 정의 임계값으로 OMR 수행
각 사용자 이미지를 반복하고 사용자 정의 임계값을 사용하여 OMR을 수행합니다.
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
## 결론
이 튜토리얼을 따라 .NET 라이브러리용 Aspose.OMR을 사용하여 .NET에서 사용자 정의 임계값으로 광학 마크 인식을 수행하는 방법을 배웠습니다. 이 기능을 사용하면 인식 프로세스를 미세 조정할 수 있으므로 스캔한 이미지에서 데이터 추출의 정확성이 향상됩니다.
## 자주 묻는 질문
### OMR에서 사용자 정의 임계값을 사용하는 것의 중요성은 무엇입니까?
사용자 정의 임계값을 통해 사용자는 인식 프로세스의 민감도를 조정하여 특정 이미지 특성 및 요구 사항에 따라 정확도를 최적화할 수 있습니다.
### 사용자 정의 임계값이 있는 OMR은 표준 OMR과 어떻게 다릅니까?
표준 OMR은 마크 감지를 위해 사전 정의된 임계값을 적용하는 반면, 사용자 정의 임계값이 있는 OMR을 사용하면 사용자가 필요에 따라 인식 매개변수를 정의하고 세분화할 수 있습니다.
### OMR에 대한 사용자 정의 임계값을 설정할 때 어떤 요소를 고려해야 합니까?
OMR에 대한 적절한 사용자 정의 임계값을 결정할 때 이미지 품질, 마크 강도, 배경 소음 수준과 같은 요소를 고려해야 합니다.
### 일괄 처리를 위해 사용자 정의 임계값이 있는 OMR을 자동화할 수 있습니까?
예. 여러 이미지의 일괄 처리를 위해 사용자 정의 임계값이 있는 OMR을 자동화하여 대규모 시나리오에서 효율적인 데이터 추출을 촉진할 수 있습니다.
### .NET용 Aspose.OMR에 대한 추가 리소스와 지원은 어디서 찾을 수 있나요?
 문서화, 지원 및 커뮤니티 상호 작용을 보려면 다음을 방문하세요.[Aspose.OMR 포럼](https://forum.aspose.com/c/omr/38) 그리고[공식 문서](https://reference.aspose.com/omr/net/).