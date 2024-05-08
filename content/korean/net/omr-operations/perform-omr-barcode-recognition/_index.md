---
title: .NET에서 바코드 인식으로 OMR 수행
linktitle: .NET에서 바코드 인식으로 OMR 수행
second_title: Aspose.OMR .NET API
description: .NET용 Aspose.OMR을 사용하여 .NET에서 바코드 인식으로 광학 마크 인식을 수행하는 방법을 알아보세요. 스캔한 이미지에서 데이터 추출을 단순화하세요!
type: docs
weight: 10
url: /ko/net/omr-operations/perform-omr-barcode-recognition/
---
이 튜토리얼에서는 .NET용 Aspose.OMR 라이브러리를 사용하여 .NET에서 바코드 인식으로 광학 마크 인식(OMR)을 수행하는 과정을 안내합니다. 이 강력한 도구를 사용하면 표시된 영역과 바코드가 포함된 스캔 이미지에서 데이터를 추출할 수 있으므로 설문조사, 평가, 데이터 수집과 같은 다양한 응용 프로그램에 필수적인 구성 요소가 됩니다.
## 전제 조건
시작하기 전에 다음 필수 구성 요소가 있는지 확인하세요.
1. Visual Studio: 시스템에 Visual Studio가 설치되어 있는지 확인하세요.
2.  .NET 라이브러리용 Aspose.OMR: 다음에서 .NET 라이브러리용 Aspose.OMR을 다운로드하고 설치합니다.[공식 웹 사이트](https://releases.aspose.com/omr/net/).
3. .NET 기본 지식: .NET 프레임워크 및 C# 프로그래밍 언어에 대한 지식.
## 네임스페이스 가져오기
코드를 살펴보기 전에 필요한 네임스페이스를 가져옵니다.
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
예제 코드를 여러 단계로 나누어 보겠습니다.
## 1단계: 템플릿 및 사용자 이미지 경로 정의
먼저 템플릿 파일과 사용자의 스캔 이미지 경로를 지정합니다.
```csharp
string TemplateName = @"AsposeTestWithBarcode.omr";
string UserImage = "AsposeTestWithBarcode.jpg";
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
## 5단계: 이미지 인식
사용자의 스캔 이미지에서 OMR 및 바코드 인식을 수행합니다.
```csharp
string imagePath = Path.Combine(testFolderPath, UserImage);
string csvResult = templateProcessor.RecognizeImage(imagePath).GetCsv();
```
## 6단계: 결과 내보내기
OMR 결과를 CSV 파일로 내보내기:
```csharp
File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImage) + ".csv"), csvResult);
Console.WriteLine("Result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImage) + ".csv"));
```
## 7단계: 결론
.NET용 Aspose.OMR을 사용하여 .NET에서 바코드 인식을 통한 광학 마크 인식을 성공적으로 수행했습니다. 이 강력한 라이브러리는 스캔한 이미지에서 데이터 추출을 단순화하므로 데이터 수집 및 분석이 필요한 다양한 애플리케이션에 이상적입니다.
## 결론
결론적으로, .NET용 Aspose.OMR 라이브러리를 활용하면 광학 표시 인식 및 바코드 인식 기능을 .NET 애플리케이션에 원활하게 통합할 수 있습니다. 이 튜토리얼에 설명된 단계를 따르면 스캔한 이미지에서 데이터를 효율적으로 추출하여 측량, 평가 및 데이터 처리 작업에 대한 다양한 가능성을 열어줄 수 있습니다.
## 자주 묻는 질문
### Aspose.OMR for .NET은 모든 바코드 유형과 호환됩니까?
예, .NET용 Aspose.OMR은 QR 코드, UPC-A, UPC-E, EAN-8, EAN-13, Code 128 등을 포함한 다양한 바코드 유형을 지원합니다.
### 내 요구 사항에 따라 OMR 템플릿을 사용자 정의할 수 있나요?
물론 Aspose.OMR 템플릿 편집기를 사용하여 OMR 템플릿을 생성하고 사용자 정의할 수 있으므로 특정 요구 사항에 맞는 양식을 디자인할 수 있습니다.
### .NET용 Aspose.OMR은 객관식 질문 처리를 지원합니까?
예, .NET용 Aspose.OMR은 객관식 질문 처리에 탁월하여 스캔한 이미지 내에서 표시된 선택 사항을 정확하게 인식합니다.
### .NET용 Aspose.OMR에 사용할 수 있는 평가판이 있습니까?
 예, 다음에서 .NET용 Aspose.OMR 무료 평가판에 액세스할 수 있습니다.[릴리스](https://releases.aspose.com/).
### .NET용 Aspose.OMR에 대한 지원을 어디서 구할 수 있나요?
 Aspose.OMR for .NET에 관한 질문이나 도움이 필요하면 다음을 방문하세요.[Aspose.OMR 포럼](https://forum.aspose.com/c/omr/38) 커뮤니티와 연결하고 전문가의 조언을 구합니다.