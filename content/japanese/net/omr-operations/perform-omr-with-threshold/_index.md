---
title: .NET でしきい値を使用して OMR を実行する
linktitle: .NET でしきい値を使用して OMR を実行する
second_title: Aspose.OMR .NET API
description: Aspose.OMR for .NET を使用して、.NET でカスタムしきい値を使用して光学式マーク認識を実行する方法を学びます。スキャン画像のデータ精度を向上！
type: docs
weight: 13
url: /ja/net/omr-operations/perform-omr-with-threshold/
---
光学式マーク認識 (OMR) は、マークされた領域を含むスキャン画像からデータを抽出するための重要なテクノロジです。このチュートリアルでは、Aspose.OMR for .NET ライブラリを使用して、.NET でカスタムしきい値を使用して OMR を実行する方法を検討します。この機能により、特定の要件に基づいて認識プロセスを微調整できるため、精度が向上します。
## 前提条件
チュートリアルを詳しく説明する前に、次の前提条件を満たしていることを確認してください。
1. Visual Studio: .NET 開発用にシステムに Visual Studio をインストールします。
2.  Aspose.OMR for .NETライブラリ: Aspose.OMR for .NETライブラリを以下のサイトからダウンロードしてインストールします。[公式ウェブサイト](https://releases.aspose.com/omr/net/).
3. .NET の基本知識: .NET フレームワークと C# プログラミング言語について理解します。
## 名前空間のインポート
まず、必要な名前空間をインポートします。
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
サンプルコードを詳細な手順に分解してみましょう。
## ステップ1: テンプレートと画像のパスを定義する
OMR テンプレートとユーザー イメージのパスを指定します。
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## ステップ 2: カスタムしきい値を設定する
OMR 処理のカスタムしきい値を定義します。
```csharp
int CustomThreshold = 40;
```
## ステップ 3: 入力と出力の準備
OMR 処理用の入力ディレクトリと出力ディレクトリを準備します。
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
```
## ステップ 4: エンジンとテンプレート プロセッサを初期化する
Aspose.OMR エンジンを初期化し、テンプレート プロセッサを取得します。
```csharp
OmrEngine engine = new OmrEngine();
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## ステップ 5: カスタムしきい値を使用して OMR を実行する
各ユーザー イメージを反復処理し、カスタムしきい値を使用して OMR を実行します。
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
## 結論
このチュートリアルに従うことで、Aspose.OMR for .NET ライブラリを使用して、.NET でカスタムしきい値を使用して光学式マーク認識を実行する方法を学習しました。この機能により、認識プロセスを微調整できるようになり、スキャン画像からのデータ抽出の精度が向上します。
## よくある質問
### OMR でカスタムしきい値を使用する意義は何ですか?
カスタムしきい値を使用すると、ユーザーは認識プロセスの感度を調整できるため、特定の画像の特性と要件に基づいて精度を最適化できます。
### カスタムしきい値を使用した OMR は標準の OMR とどのように異なりますか?
標準 OMR では、マーク検出に事前定義されたしきい値が適用されますが、カスタムしきい値を使用する OMR では、ユーザーがニーズに応じて認識パラメータを定義および調整できます。
### OMR のカスタムしきい値を設定する場合、どのような要素を考慮する必要がありますか?
OMR の適切なカスタムしきい値を決定する際には、画像の品質、マークの強度、背景ノイズ レベルなどの要素を考慮する必要があります。
### カスタムしきい値を持つ OMR をバッチ処理用に自動化できますか?
はい、カスタムしきい値を使用した OMR は、複数の画像のバッチ処理を自動化できるため、大規模なシナリオで効率的なデータ抽出が可能になります。
### Aspose.OMR for .NET に関する追加のリソースとサポートはどこで見つかりますか?
ドキュメント、サポート、コミュニティの交流については、[Aspose.OMR フォーラム](https://forum.aspose.com/c/omr/38)そして[公式文書](https://reference.aspose.com/omr/net/).