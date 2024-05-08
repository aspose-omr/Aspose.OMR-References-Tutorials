---
title: .NET でバーコード認識による OMR を実行する
linktitle: .NET でバーコード認識による OMR を実行する
second_title: Aspose.OMR .NET API
description: Aspose.OMR for .NET を使用して、.NET で光学マーク認識とバーコード認識を実行する方法を学びます。スキャンした画像からのデータ抽出を簡素化します。
type: docs
weight: 10
url: /ja/net/omr-operations/perform-omr-barcode-recognition/
---
このチュートリアルでは、Aspose.OMR for .NET ライブラリを使用して、.NET で光学式マーク認識 (OMR) とバーコード認識を実行するプロセスについて説明します。この強力なツールを使用すると、マークされた領域とバーコードを含むスキャンされた画像からデータを抽出できるため、調査、評価、データ収集などのさまざまなアプリケーションに不可欠なコンポーネントになります。
## 前提条件
始める前に、次の前提条件を満たしていることを確認してください。
1. Visual Studio: システムに Visual Studio がインストールされていることを確認します。
2.  Aspose.OMR for .NETライブラリ: Aspose.OMR for .NETライブラリを以下のサイトからダウンロードしてインストールします。[公式ウェブサイト](https://releases.aspose.com/omr/net/).
3. .NET の基礎知識: .NET フレームワークと C# プログラミング言語に精通していること。
## 名前空間のインポート
コードに進む前に、必要な名前空間をインポートします。
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
サンプルコードを複数のステップに分解してみましょう。
## ステップ1: テンプレートとユーザーイメージのパスを定義する
まず、テンプレート ファイルとユーザーのスキャン画像のパスを指定します。
```csharp
string TemplateName = @"AsposeTestWithBarcode.omr";
string UserImage = "AsposeTestWithBarcode.jpg";
```
## ステップ 2: 入力と出力の準備
OMR 処理用の入力ディレクトリと出力ディレクトリを準備します。
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
```
## ステップ 3: OMR エンジンを初期化する
Aspose.OMR エンジンを初期化して処理を開始します。
```csharp
OmrEngine engine = new OmrEngine();
```
## ステップ 4: テンプレートをロードする
OMR テンプレートをテンプレート プロセッサにロードします。
```csharp
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## ステップ 5: 画像を認識する
ユーザーのスキャン画像に対して OMR およびバーコード認識を実行します。
```csharp
string imagePath = Path.Combine(testFolderPath, UserImage);
string csvResult = templateProcessor.RecognizeImage(imagePath).GetCsv();
```
## ステップ 6: 結果をエクスポートする
OMR 結果を CSV ファイルにエクスポートします。
```csharp
File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImage) + ".csv"), csvResult);
Console.WriteLine("Result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImage) + ".csv"));
```
## ステップ 7: 結論
Aspose.OMR for .NET を使用して、.NET でバーコード認識による光学式マーク認識を正常に実行できました。この強力なライブラリは、スキャン画像からのデータ抽出を簡素化し、データ収集と分析を必要とするさまざまなアプリケーションに最適です。
## 結論
結論として、Aspose.OMR for .NET ライブラリを活用すると、光学式マーク認識機能とバーコード認識機能を .NET アプリケーションにシームレスに統合できます。このチュートリアルで概説されている手順に従うことで、スキャンされた画像からデータを効率的に抽出でき、測量、評価、およびデータ処理タスクのさまざまな可能性が広がります。
## よくある質問
### Aspose.OMR for .NET はすべてのバーコード タイプと互換性がありますか?
はい、Aspose.OMR for .NET は、QR コード、UPC-A、UPC-E、EAN-8、EAN-13、Code 128 などを含むさまざまなバーコード タイプをサポートしています。
### 要件に応じて OMR テンプレートをカスタマイズできますか?
もちろん、Aspose.OMR テンプレート エディターを使用して OMR テンプレートを作成およびカスタマイズでき、特定のニーズに合わせたフォームを設計できます。
### Aspose.OMR for .NET は、多肢選択式の質問の処理をサポートしていますか?
はい、Aspose.OMR for .NET は多肢選択式の質問の処理に優れており、スキャンされた画像内のマークされた選択肢を正確に認識します。
### Aspose.OMR for .NET の試用版はありますか?
はい、Aspose.OMR for .NET の無料試用版には、[リリース](https://releases.aspose.com/).
### Aspose.OMR for .NET に関するサポートやサポートはどこに問い合わせればよいですか?
 Aspose.OMR for .NET に関するお問い合わせやサポートについては、次のサイトにアクセスしてください。[Aspose.OMR フォーラム](https://forum.aspose.com/c/omr/38)コミュニティとつながり、専門家の指導を求めることができます。