---
title: .NET でイメージに対して OMR を実行する
linktitle: .NET でイメージに対して OMR を実行する
second_title: Aspose.OMR .NET API
description: Aspose.OMR for .NET を使用して .NET の画像に対して光学式マーク認識を実行する方法を学びます。画像ベースのフォームからのデータ抽出を合理化します。
type: docs
weight: 11
url: /ja/net/omr-operations/perform-omr-on-images/
---
このチュートリアルでは、Aspose.OMR for .NET ライブラリを使用して、.NET の画像に対して光学式マーク認識 (OMR) を実行するプロセスについて説明します。 OMR は、画像上のマークされた領域を認識してデータを抽出するために使用される技術であり、調査、評価、データ収集などのタスクに非常に役立ちます。
## 前提条件
始める前に、次の前提条件を満たしていることを確認してください。
1. Visual Studio: Visual Studio がシステムにインストールされていることを確認してください。
2.  Aspose.OMR for .NETライブラリ: Aspose.OMR for .NETライブラリを以下のサイトからダウンロードしてインストールします。[リリース](https://releases.aspose.com/omr/net/).
3. .NET の基本知識: .NET フレームワークと C# プログラミング言語について理解します。
## 名前空間のインポート
まず、必要な名前空間をインポートします。
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
わかりやすくするために、コード例を複数のステップに分けてみましょう。
## ステップ1: テンプレートとユーザーイメージのパスを定義する
まず、OMR テンプレートとユーザー イメージのパスを指定します。
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
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
## ステップ 5: ユーザー画像を反復処理する
各ユーザー イメージを反復処理して OMR を実行します。
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string imagePath = Path.Combine(testFolderPath, UserImages[i]);
    string csvResult = templateProcessor.RecognizeImage(imagePath).GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"), csvResult);
    Console.WriteLine("Result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"));
}
```
## ステップ 6: 結論
Aspose.OMR for .NET を使用して、.NET で画像の光学式マーク認識を正常に実行しました。この機能により、画像からのデータの抽出が効率化され、調査や評価などのさまざまなアプリケーションが容易になります。
## 結論
結論として、Aspose.OMR for .NET ライブラリは、.NET アプリケーションでの光学式マーク認識タスクのための強力なソリューションを提供します。このチュートリアルで説明されている手順に従うことで、OMR 機能をプロジェクトにシームレスに統合し、画像から効率的にデータを抽出できるようになります。
## よくある質問
### Aspose.OMR for .NET は複数の画像を同時に処理できますか?
はい、Aspose.OMR for .NET は複数の画像のバッチ処理をサポートしており、大規模なデータセットを効率的に処理できます。
### Aspose.OMR for .NET はどのような種類のマーク認識をサポートしていますか?
Aspose.OMR for .NET は、チェックボックス、バブル、グリッドなど、さまざまなマーク認識タイプをサポートしています。
### 特定のフォームに合わせて OMR テンプレートをカスタマイズすることは可能ですか?
もちろんです。Aspose.OMR テンプレート エディターを使用して OMR テンプレートを作成およびカスタマイズし、正確な要件に合わせて調整できます。
### Aspose.OMR for .NET は、傾斜した画像をサポートしていますか?
はい、Aspose.OMR for .NET には、歪んだ画像や回転した画像を処理する機能が含まれており、正確なマーク認識を保証します。
### Aspose.OMR for .NET のサポートとリソースはどこで見つかりますか?
サポート、ドキュメント、コミュニティの交流については、[Aspose.OMR フォーラム](https://forum.aspose.com/c/omr/38)そして[公式文書](https://reference.aspose.com/omr/net/).