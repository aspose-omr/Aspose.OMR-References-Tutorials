---
title: Realizar OMR en imágenes en .NET
linktitle: Realizar OMR en imágenes en .NET
second_title: Aspose.OMR API .NET
description: Aprenda a realizar el reconocimiento óptico de marcas en imágenes en .NET usando Aspose.OMR para .NET. ¡Agilice la extracción de datos de formularios basados en imágenes!
type: docs
weight: 11
url: /es/net/omr-operations/perform-omr-on-images/
---
En este tutorial, lo guiaremos a través del proceso de realizar el reconocimiento óptico de marcas (OMR) en imágenes en .NET utilizando la biblioteca Aspose.OMR para .NET. OMR es una técnica utilizada para reconocer y extraer datos de áreas marcadas en imágenes, lo que la hace invaluable para tareas como encuestas, evaluaciones y recopilación de datos.
## Requisitos previos
Antes de comenzar, asegúrese de tener los siguientes requisitos previos:
1. Visual Studio: asegúrese de tener Visual Studio instalado en su sistema.
2.  Aspose.OMR para la biblioteca .NET: descargue e instale la biblioteca Aspose.OMR para .NET desde[lanzamientos](https://releases.aspose.com/omr/net/).
3. Conocimientos básicos de .NET: familiarícese con el marco .NET y el lenguaje de programación C#.
## Importar espacios de nombres
Comience importando los espacios de nombres necesarios:
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
Dividamos el código de ejemplo en varios pasos para mayor claridad:
## Paso 1: definir la plantilla y las rutas de las imágenes del usuario
Primero, especifique las rutas para la plantilla OMR y las imágenes de usuario:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## Paso 2: preparar la entrada y la salida
Prepare los directorios de entrada y salida para el procesamiento OMR:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
```
## Paso 3: Inicializar el motor OMR
Inicialice el motor Aspose.OMR para comenzar a procesar:
```csharp
OmrEngine engine = new OmrEngine();
```
## Paso 4: Cargar plantilla
Cargue la plantilla OMR en el procesador de plantillas:
```csharp
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## Paso 5: iterar a través de imágenes de usuario
Repita cada imagen de usuario para realizar OMR:
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string imagePath = Path.Combine(testFolderPath, UserImages[i]);
    string csvResult = templateProcessor.RecognizeImage(imagePath).GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"), csvResult);
    Console.WriteLine("Result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(UserImages[i]) + ".csv"));
}
```
## Paso 6: Conclusión
Ha realizado con éxito el reconocimiento óptico de marcas en imágenes en .NET utilizando Aspose.OMR para .NET. Esta capacidad agiliza la extracción de datos de imágenes, facilitando diversas aplicaciones como encuestas y evaluaciones.
## Conclusión
En conclusión, la biblioteca Aspose.OMR para .NET proporciona una solución poderosa para tareas de reconocimiento óptico de marcas en aplicaciones .NET. Si sigue los pasos descritos en este tutorial, puede integrar perfectamente la funcionalidad OMR en sus proyectos, lo que permite una extracción eficiente de datos de imágenes.
## Preguntas frecuentes
### ¿Puede Aspose.OMR para .NET manejar varias imágenes simultáneamente?
Sí, Aspose.OMR para .NET admite el procesamiento por lotes de múltiples imágenes, lo que permite un manejo eficiente de grandes conjuntos de datos.
### ¿Qué tipos de reconocimiento de marcas admite Aspose.OMR para .NET?
Aspose.OMR para .NET admite varios tipos de reconocimiento de marcas, incluidas casillas de verificación, burbujas y cuadrículas.
### ¿Es posible personalizar las plantillas OMR para que coincidan con formularios específicos?
Por supuesto, puede crear y personalizar plantillas OMR utilizando el editor de plantillas Aspose.OMR, adaptándolas a sus requisitos exactos.
### ¿Aspose.OMR para .NET ofrece soporte para imágenes sesgadas?
Sí, Aspose.OMR para .NET incluye funciones para manejar imágenes torcidas y rotadas, lo que garantiza un reconocimiento preciso de las marcas.
### ¿Dónde puedo encontrar soporte y recursos para Aspose.OMR para .NET?
 Para obtener soporte, documentación e interacción con la comunidad, visite el[Foro Aspose.OMR](https://forum.aspose.com/c/omr/38) y[documentación oficial](https://reference.aspose.com/omr/net/).