---
title: Execute OMR em imagens em .NET
linktitle: Execute OMR em imagens em .NET
second_title: API Aspose.OMR .NET
description: Aprenda como realizar o reconhecimento de marca óptica em imagens em .NET usando Aspose.OMR para .NET. Simplifique a extração de dados de formulários baseados em imagens!
type: docs
weight: 11
url: /pt/net/omr-operations/perform-omr-on-images/
---
Neste tutorial, orientaremos você no processo de execução do reconhecimento de marca óptica (OMR) em imagens no .NET usando a biblioteca Aspose.OMR para .NET. OMR é uma técnica usada para reconhecer e extrair dados de áreas marcadas em imagens, tornando-a inestimável para tarefas como pesquisas, avaliações e coleta de dados.
## Pré-requisitos
Antes de começarmos, certifique-se de ter os seguintes pré-requisitos:
1. Visual Studio: certifique-se de ter o Visual Studio instalado em seu sistema.
2.  Biblioteca Aspose.OMR for .NET: Baixe e instale a biblioteca Aspose.OMR for .NET do[lançamentos](https://releases.aspose.com/omr/net/).
3. Conhecimento básico de .NET: Familiarize-se com o framework .NET e a linguagem de programação C#.
## Importar namespaces
Comece importando os namespaces necessários:
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
Vamos dividir o código de exemplo em várias etapas para maior clareza:
## Etapa 1: definir caminhos de modelo e imagem do usuário
Primeiro, especifique os caminhos para o modelo OMR e as imagens do usuário:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## Etapa 2: preparar entrada e saída
Prepare os diretórios de entrada e saída para processamento do OMR:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
```
## Etapa 3: inicializar o mecanismo OMR
Inicialize o mecanismo Aspose.OMR para iniciar o processamento:
```csharp
OmrEngine engine = new OmrEngine();
```
## Etapa 4: carregar modelo
Carregue o modelo OMR no processador de modelo:
```csharp
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## Etapa 5: iterar por meio de imagens do usuário
Itere através de cada imagem do usuário para realizar o OMR:
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string imagePath = Path.Combine(testFolderPath, UserImages[i]);
    string csvResult = templateProcessor.RecognizeImage(imagePath).GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"), csvResult);
    Console.WriteLine("Result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"));
}
```
## Etapa 6: Conclusão
Você executou com êxito o reconhecimento de marca óptica em imagens em .NET usando Aspose.OMR para .NET. Esse recurso agiliza a extração de dados de imagens, facilitando diversas aplicações, como pesquisas e avaliações.
## Conclusão
Concluindo, a biblioteca Aspose.OMR for .NET fornece uma solução poderosa para tarefas de reconhecimento de marca óptica em aplicativos .NET. Seguindo as etapas descritas neste tutorial, você pode integrar perfeitamente a funcionalidade OMR em seus projetos, permitindo a extração eficiente de dados de imagens.
## perguntas frequentes
### O Aspose.OMR for .NET pode lidar com várias imagens simultaneamente?
Sim, o Aspose.OMR for .NET oferece suporte ao processamento em lote de várias imagens, permitindo o manuseio eficiente de grandes conjuntos de dados.
### Que tipos de reconhecimento de marca o Aspose.OMR for .NET suporta?
Aspose.OMR for .NET oferece suporte a vários tipos de reconhecimento de marcas, incluindo caixas de seleção, bolhas e grades.
### É possível personalizar modelos de OMR para corresponder a formulários específicos?
Com certeza, você pode criar e personalizar modelos OMR usando o Aspose.OMR Template Editor, adaptando-os exatamente às suas necessidades.
### O Aspose.OMR for .NET oferece suporte para imagens distorcidas?
Sim, o Aspose.OMR for .NET inclui recursos para lidar com imagens distorcidas e giradas, garantindo um reconhecimento preciso da marca.
### Onde posso encontrar suporte e recursos para Aspose.OMR for .NET?
 Para suporte, documentação e interação com a comunidade, visite o[Fórum Aspose.OMR](https://forum.aspose.com/c/omr/38) e[documentação oficial](https://reference.aspose.com/omr/net/).