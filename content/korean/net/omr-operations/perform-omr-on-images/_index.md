---
title: .NET의 이미지에 대해 OMR 수행
linktitle: .NET의 이미지에 대해 OMR 수행
second_title: Aspose.OMR .NET API
description: .NET용 Aspose.OMR을 사용하여 .NET의 이미지에서 광학 마크 인식을 수행하는 방법을 알아보세요. 이미지 기반 양식에서 데이터 추출을 간소화하세요!
type: docs
weight: 11
url: /ko/net/omr-operations/perform-omr-on-images/
---
이 튜토리얼에서는 .NET용 Aspose.OMR 라이브러리를 사용하여 .NET의 이미지에 OMR(광학 마크 인식)을 수행하는 과정을 안내합니다. OMR은 이미지에 표시된 영역에서 데이터를 인식하고 추출하는 데 사용되는 기술이므로 설문조사, 평가, 데이터 수집 등의 작업에 매우 유용합니다.
## 전제 조건
시작하기 전에 다음 전제 조건이 충족되었는지 확인하세요.
1. Visual Studio: 시스템에 Visual Studio가 설치되어 있는지 확인하세요.
2.  .NET 라이브러리용 Aspose.OMR: 다음에서 .NET 라이브러리용 Aspose.OMR을 다운로드하고 설치합니다.[릴리스](https://releases.aspose.com/omr/net/).
3. .NET 기본 지식: .NET 프레임워크 및 C# 프로그래밍 언어에 익숙해집니다.
## 네임스페이스 가져오기
필요한 네임스페이스를 가져오는 것부터 시작하세요.
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
명확성을 위해 예제 코드를 여러 단계로 나누어 보겠습니다.
## 1단계: 템플릿 및 사용자 이미지 경로 정의
먼저 OMR 템플릿과 사용자 이미지의 경로를 지정합니다.
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## 2단계: 입력 및 출력 준비
OMR 처리를 위한 입력 및 출력 디렉터리를 준비합니다.
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
```
## 3단계: OMR 엔진 초기화
처리를 시작하려면 Aspose.OMR 엔진을 초기화하세요.
```csharp
OmrEngine engine = new OmrEngine();
```
## 4단계: 템플릿 로드
OMR 템플릿을 템플릿 프로세서에 로드합니다.
```csharp
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## 5단계: 사용자 이미지 반복
각 사용자 이미지를 반복하여 OMR을 수행합니다.
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string imagePath = Path.Combine(testFolderPath, UserImages[i]);
    string csvResult = templateProcessor.RecognizeImage(imagePath).GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"), csvResult);
    Console.WriteLine("Result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"));
}
```
## 6단계: 결론
.NET용 Aspose.OMR을 사용하여 .NET의 이미지에 대한 광학 마크 인식을 성공적으로 수행했습니다. 이 기능은 이미지에서 데이터 추출을 간소화하여 설문 조사 및 평가와 같은 다양한 애플리케이션을 용이하게 합니다.
## 결론
결론적으로, .NET용 Aspose.OMR 라이브러리는 .NET 애플리케이션의 광학 마크 인식 작업을 위한 강력한 솔루션을 제공합니다. 이 튜토리얼에 설명된 단계를 따르면 OMR 기능을 프로젝트에 원활하게 통합하여 이미지에서 효율적으로 데이터를 추출할 수 있습니다.
## 자주 묻는 질문
### .NET용 Aspose.OMR은 여러 이미지를 동시에 처리할 수 있습니까?
예, Aspose.OMR for .NET은 여러 이미지의 일괄 처리를 지원하므로 대규모 데이터 세트를 효율적으로 처리할 수 있습니다.
### .NET용 Aspose.OMR은 어떤 유형의 마크 인식을 지원합니까?
.NET용 Aspose.OMR은 체크박스, 버블, 그리드 등 다양한 표시 인식 유형을 지원합니다.
### 특정 양식에 맞게 OMR 템플릿을 사용자 정의할 수 있습니까?
물론 Aspose.OMR 템플릿 편집기를 사용하여 OMR 템플릿을 만들고 사용자 정의하여 정확한 요구 사항에 맞게 조정할 수 있습니다.
### .NET용 Aspose.OMR은 왜곡된 이미지를 지원합니까?
예, Aspose.OMR for .NET에는 기울어지거나 회전된 이미지를 처리하여 정확한 마크 인식을 보장하는 기능이 포함되어 있습니다.
### .NET용 Aspose.OMR에 대한 지원과 리소스는 어디서 찾을 수 있나요?
 지원, 문서 및 커뮤니티 상호 작용을 보려면 다음을 방문하세요.[Aspose.OMR 포럼](https://forum.aspose.com/c/omr/38) 그리고[공식 문서](https://reference.aspose.com/omr/net/).