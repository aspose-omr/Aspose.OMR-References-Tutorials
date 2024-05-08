---
title: .NET で OMR 再計算を実行する
linktitle: .NET で OMR 再計算を実行する
second_title: Aspose.OMR .NET API
description: Aspose.OMR for .NET を使用して、.NET で光学式マーク認識の再計算を実行する方法を学びます。スキャンした画像からのデータの精度を高めます。
type: docs
weight: 12
url: /ja/net/omr-operations/perform-omr-recalculation/
---
このチュートリアルでは、Aspose.OMR for .NET ライブラリを使用して、.NET で光学式マーク認識 (OMR) 再計算を実行するプロセスについて説明します。OMR 再計算を使用すると、カスタムしきい値に基づいて認識結果を調整できるため、スキャンされた画像からのデータ抽出の精度が向上します。
## 前提条件
続行する前に、次の前提条件を満たしていることを確認してください。
1. Visual Studio: .NET 開発用にシステムに Visual Studio をインストールします。
2.  Aspose.OMR for .NETライブラリ: Aspose.OMR for .NETライブラリを以下のサイトからダウンロードしてインストールします。[公式ウェブサイト](https://releases.aspose.com/omr/net/).
3. .NET の基本知識: .NET フレームワークと C# プログラミング言語について理解します。
## 名前空間のインポート
まず、必要な名前空間をインポートします。
```csharp
using Aspose.OMR.Api;
using Aspose.OMR.Model;
using System;
using System.Diagnostics;
using System.IO;
```
サンプルコードを詳細な手順に分解してみましょう。
## ステップ1: テンプレートと画像のパスを定義する
OMR テンプレートとユーザー イメージのパスを指定します。
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## ステップ2: フォルダを設定する
OMR 処理用の入力ディレクトリと出力ディレクトリを準備します。
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
int CustomThreshold = 40; //カスタムしきい値を定義する
```
## ステップ3: エンジンとテンプレートプロセッサを初期化する
Aspose.OMR エンジンを初期化し、テンプレート プロセッサを取得します。
```csharp
OmrEngine engine = new OmrEngine();
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## ステップ4: ユーザー画像の処理
各ユーザー イメージを反復処理して OMR の再計算を実行します。
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string image = UserImages[i];
    string imagePath = Path.Combine(testFolderPath, image);
    Console.WriteLine("\n\rProcessing image: " + imagePath);
    //パフォーマンス時間を測定
    Stopwatch sw = Stopwatch.StartNew();
    //画像を認識する
    RecognitionResult result = templateProcessor.RecognizeImage(imagePath);
    sw.Stop();
    Console.WriteLine("Recognition time: " + sw.Elapsed);
    //認識結果をCSVにエクスポート
    string stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"), stringRes);
    Console.WriteLine("Result Exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"));
    sw.Restart();
    //カスタムしきい値でOMR再計算を実行する
    Console.WriteLine("\n\rPerforming recalculation\n\r");
    templateProcessor.Recalculate(result, CustomThreshold);
    sw.Stop();
    Console.WriteLine("Recalculation time: " + sw.Elapsed);
    //再計算された結果をエクスポートする
    stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"), stringRes);
    Console.WriteLine("Recalculation result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"));
}
```
## ステップ5: 結論
Aspose.OMR for .NET を使用して、.NET で光学式マーク認識の再計算が正常に実行されました。この機能を使用すると、カスタムしきい値に基づいて認識結果を微調整でき、データの精度が向上します。
## 結論
結論として、Aspose.OMR for .NET ライブラリは、.NET アプリケーションの光学式マーク認識タスク用の強力なツールを提供します。このチュートリアルで概説されている手順に従うことで、OMR 再計算機能をプロジェクトにシームレスに統合し、スキャン画像からのデータ抽出の精度を高めることができます。
## よくある質問
### OMR 再計算とは何ですか?なぜ重要ですか?
OMR の再計算は、カスタムしきい値に基づいて認識結果を調整するプロセスです。これは、特に標準的な認識では十分ではないシナリオにおいて、スキャン画像からのデータ抽出の精度を向上させるために重要です。
### OMR の再計算は標準の認識とどのように異なりますか?
OMR 再計算では、カスタムしきい値を適用することで認識結果をより細かく調整できますが、標準認識ではユーザーの介入なしに事前定義されたアルゴリズムに従います。
### .NET アプリケーションで OMR 再計算を自動化できますか?
はい、Aspose.OMR for .NET ライブラリを統合し、その API を使用して画像を処理し、認識結果を調整することで、.NET アプリケーションで OMR の再計算を自動化できます。
### OMR 再計算のカスタムしきい値を決定する際に考慮すべき要素は何ですか?
OMR 再計算のカスタムしきい値を決定する際には、画像品質、マーク密度、必要な精度レベルなどの要素を考慮する必要があります。
### Aspose.OMR for .NET に関する追加のリソースとサポートはどこで見つかりますか?
ドキュメント、サポート、コミュニティの交流については、[Aspose.OMR フォーラム](https://forum.aspose.com/c/omr/38)そして[公式文書](https://reference.aspose.com/omr/net/).