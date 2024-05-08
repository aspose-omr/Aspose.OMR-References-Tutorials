---
title: Execute o recálculo do OMR em .NET
linktitle: Execute o recálculo do OMR em .NET
second_title: API Aspose.OMR .NET
description: Aprenda como realizar o recálculo do reconhecimento de marca óptica em .NET usando Aspose.OMR para .NET. Melhore a precisão dos dados das imagens digitalizadas!
type: docs
weight: 12
url: /pt/net/omr-operations/perform-omr-recalculation/
---
Neste tutorial, orientaremos você no processo de execução do recálculo do Optical Mark Recognition (OMR) no .NET usando a biblioteca Aspose.OMR for .NET. O recálculo do OMR permite ajustar os resultados do reconhecimento com base em limites personalizados, melhorando a precisão da extração de dados das imagens digitalizadas.
## Pré-requisitos
Antes de prosseguir, certifique-se de ter os seguintes pré-requisitos:
1. Visual Studio: instale o Visual Studio em seu sistema para desenvolvimento .NET.
2.  Biblioteca Aspose.OMR for .NET: Baixe e instale a biblioteca Aspose.OMR for .NET do[website oficial](https://releases.aspose.com/omr/net/).
3. Conhecimento básico de .NET: Familiarize-se com o framework .NET e a linguagem de programação C#.
## Importar namespaces
Comece importando os namespaces necessários:
```csharp
using Aspose.OMR.Api;
using Aspose.OMR.Model;
using System;
using System.Diagnostics;
using System.IO;
```
Vamos dividir o código de exemplo em etapas detalhadas:
## Etapa 1: definir caminhos de modelo e imagem
Especifique os caminhos para o modelo OMR e as imagens do usuário:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## Etapa 2: configurar pastas
Prepare os diretórios de entrada e saída para processamento do OMR:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
int CustomThreshold = 40; // Definir limite personalizado
```
## Etapa 3: inicializar o mecanismo e o processador de modelo
Inicialize o mecanismo Aspose.OMR e obtenha o processador de modelo:
```csharp
OmrEngine engine = new OmrEngine();
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## Etapa 4: processar imagens do usuário
Itere através de cada imagem do usuário para realizar o recálculo do OMR:
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string image = UserImages[i];
    string imagePath = Path.Combine(testFolderPath, image);
    Console.WriteLine("\n\rProcessing image: " + imagePath);
    // Meça o tempo de desempenho
    Stopwatch sw = Stopwatch.StartNew();
    // Reconhecer imagem
    RecognitionResult result = templateProcessor.RecognizeImage(imagePath);
    sw.Stop();
    Console.WriteLine("Recognition time: " + sw.Elapsed);
    // Exportar resultados de reconhecimento para CSV
    string stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"), stringRes);
    Console.WriteLine("Result Exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"));
    sw.Restart();
    // Execute o recálculo do OMR com limite personalizado
    Console.WriteLine("\n\rPerforming recalculation\n\r");
    templateProcessor.Recalculate(result, CustomThreshold);
    sw.Stop();
    Console.WriteLine("Recalculation time: " + sw.Elapsed);
    // Exportar resultados recalculados
    stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"), stringRes);
    Console.WriteLine("Recalculation result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"));
}
```
## Etapa 5: Conclusão
Você executou com êxito o recálculo do reconhecimento de marca óptica no .NET usando Aspose.OMR para .NET. Este recurso permite ajustar os resultados de reconhecimento com base em limites personalizados, melhorando a precisão dos dados.
## Conclusão
Concluindo, a biblioteca Aspose.OMR for .NET fornece ferramentas poderosas para tarefas de reconhecimento de marca óptica em aplicativos .NET. Seguindo as etapas descritas neste tutorial, você pode integrar perfeitamente os recursos de recálculo de OMR em seus projetos, melhorando a precisão da extração de dados de imagens digitalizadas.
## perguntas frequentes
### O que é o recálculo do OMR e por que é importante?
O recálculo do OMR é o processo de ajuste dos resultados de reconhecimento com base em limites personalizados. É importante para melhorar a precisão da extração de dados de imagens digitalizadas, especialmente em cenários onde o reconhecimento padrão pode não ser suficiente.
### Como o recálculo do OMR difere do reconhecimento padrão?
recálculo do OMR permite ajustes mais precisos nos resultados de reconhecimento aplicando limites personalizados, enquanto o reconhecimento padrão segue algoritmos predefinidos sem intervenção do usuário.
### O recálculo do OMR pode ser automatizado em aplicativos .NET?
Sim, o recálculo do OMR pode ser automatizado em aplicativos .NET integrando a biblioteca Aspose.OMR for .NET e utilizando sua API para processar imagens e ajustar resultados de reconhecimento.
### Que fatores devem ser considerados ao determinar o limite personalizado para recálculo do OMR?
Fatores como qualidade de imagem, densidade de marca e nível de precisão desejado devem ser considerados ao determinar o limite personalizado para recálculo de OMR.
### Onde posso encontrar recursos adicionais e suporte para Aspose.OMR for .NET?
 Para documentação, suporte e interação com a comunidade, visite o[Fórum Aspose.OMR](https://forum.aspose.com/c/omr/38) e[documentação oficial](https://reference.aspose.com/omr/net/).