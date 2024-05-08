---
title: Realizar un recálculo de OMR en .NET
linktitle: Realizar un recálculo de OMR en .NET
second_title: Aspose.OMR API .NET
description: Aprenda a realizar un nuevo cálculo del reconocimiento óptico de marcas en .NET utilizando Aspose.OMR para .NET. ¡Mejore la precisión de los datos de las imágenes escaneadas!
type: docs
weight: 12
url: /es/net/omr-operations/perform-omr-recalculation/
---
En este tutorial, lo guiaremos a través del proceso de realizar el recálculo del reconocimiento óptico de marcas (OMR) en .NET utilizando la biblioteca Aspose.OMR para .NET. El recálculo de OMR le permite ajustar los resultados del reconocimiento según umbrales personalizados, lo que mejora la precisión de la extracción de datos de las imágenes escaneadas.
## Requisitos previos
Antes de continuar, asegúrese de tener los siguientes requisitos previos:
1. Visual Studio: instale Visual Studio en su sistema para el desarrollo .NET.
2.  Aspose.OMR para la biblioteca .NET: descargue e instale la biblioteca Aspose.OMR para .NET desde[página web oficial](https://releases.aspose.com/omr/net/).
3. Conocimientos básicos de .NET: familiarícese con el marco .NET y el lenguaje de programación C#.
## Importar espacios de nombres
Comience importando los espacios de nombres necesarios:
```csharp
using Aspose.OMR.Api;
using Aspose.OMR.Model;
using System;
using System.Diagnostics;
using System.IO;
```
Dividamos el código de ejemplo en pasos detallados:
## Paso 1: definir rutas de plantilla e imagen
Especifique las rutas para la plantilla OMR y las imágenes de usuario:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## Paso 2: configurar carpetas
Prepare los directorios de entrada y salida para el procesamiento OMR:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
int CustomThreshold = 40; // Definir umbral personalizado
```
## Paso 3: Inicializar el motor y el procesador de plantillas
Inicialice el motor Aspose.OMR y obtenga el procesador de plantilla:
```csharp
OmrEngine engine = new OmrEngine();
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## Paso 4: Procesar imágenes de usuario
Repita cada imagen de usuario para realizar un recálculo de OMR:
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string image = UserImages[i];
    string imagePath = Path.Combine(testFolderPath, image);
    Console.WriteLine("\n\rProcessing image: " + imagePath);
    // Medir el tiempo de desempeño
    Stopwatch sw = Stopwatch.StartNew();
    // Reconocer imagen
    RecognitionResult result = templateProcessor.RecognizeImage(imagePath);
    sw.Stop();
    Console.WriteLine("Recognition time: " + sw.Elapsed);
    // Exportar resultados de reconocimiento a CSV
    string stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"), stringRes);
    Console.WriteLine("Result Exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"));
    sw.Restart();
    // Realizar un nuevo cálculo de OMR con un umbral personalizado
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
## Paso 5: Conclusión
Ha realizado con éxito el nuevo cálculo del reconocimiento de marcas ópticas en .NET utilizando Aspose.OMR para .NET. Esta función le permite ajustar los resultados del reconocimiento en función de umbrales personalizados, lo que mejora la precisión de los datos.
## Conclusión
En conclusión, la biblioteca Aspose.OMR para .NET proporciona herramientas poderosas para tareas de reconocimiento óptico de marcas en aplicaciones .NET. Si sigue los pasos descritos en este tutorial, podrá integrar perfectamente las capacidades de recálculo de OMR en sus proyectos, mejorando la precisión de la extracción de datos de las imágenes escaneadas.
## Preguntas frecuentes
### ¿Qué es el recálculo de OMR y por qué es importante?
El recálculo de OMR es el proceso de ajustar los resultados del reconocimiento en función de umbrales personalizados. Es importante para mejorar la precisión de la extracción de datos de imágenes escaneadas, especialmente en escenarios donde el reconocimiento estándar puede no ser suficiente.
### ¿En qué se diferencia el recálculo de OMR del reconocimiento estándar?
El recálculo de OMR permite realizar ajustes más precisos en los resultados del reconocimiento mediante la aplicación de umbrales personalizados, mientras que el reconocimiento estándar sigue algoritmos predefinidos sin intervención del usuario.
### ¿Se puede automatizar el recálculo de OMR en aplicaciones .NET?
Sí, el recálculo de OMR se puede automatizar en aplicaciones .NET integrando la biblioteca Aspose.OMR para .NET y utilizando su API para procesar imágenes y ajustar los resultados del reconocimiento.
### ¿Qué factores se deben considerar al determinar el umbral personalizado para el recálculo de OMR?
Se deben considerar factores como la calidad de la imagen, la densidad de las marcas y el nivel deseado de precisión al determinar el umbral personalizado para el recálculo de OMR.
### ¿Dónde puedo encontrar recursos adicionales y soporte para Aspose.OMR para .NET?
 Para obtener documentación, soporte e interacción con la comunidad, visite el[Foro Aspose.OMR](https://forum.aspose.com/c/omr/38) y[documentación oficial](https://reference.aspose.com/omr/net/).