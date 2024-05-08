---
title: Εκτελέστε OMR με Threshold στο .NET
linktitle: Εκτελέστε OMR με Threshold στο .NET
second_title: Aspose.OMR .NET API
description: Μάθετε πώς να εκτελείτε Optical Mark Recognition με προσαρμοσμένο όριο στο .NET χρησιμοποιώντας το Aspose.OMR για .NET. Βελτιώστε την ακρίβεια των δεδομένων από σαρωμένες εικόνες!
type: docs
weight: 13
url: /el/net/omr-operations/perform-omr-with-threshold/
---
Η Optical Mark Recognition (OMR) είναι μια κρίσιμη τεχνολογία για την εξαγωγή δεδομένων από σαρωμένες εικόνες που περιέχουν σημειωμένες περιοχές. Σε αυτό το σεμινάριο, θα διερευνήσουμε πώς να εκτελέσετε OMR με ένα προσαρμοσμένο όριο στο .NET χρησιμοποιώντας τη βιβλιοθήκη Aspose.OMR για .NET. Αυτή η δυνατότητα επιτρέπει τη λεπτομερή ρύθμιση της διαδικασίας αναγνώρισης με βάση συγκεκριμένες απαιτήσεις, βελτιώνοντας έτσι την ακρίβεια.
## Προαπαιτούμενα
Πριν εμβαθύνουμε στο σεμινάριο, βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις:
1. Visual Studio: Εγκαταστήστε το Visual Studio στο σύστημά σας για ανάπτυξη .NET.
2.  Aspose.OMR for .NET Library: Κατεβάστε και εγκαταστήστε τη βιβλιοθήκη Aspose.OMR για .NET από το[επίσημη ιστοσελίδα](https://releases.aspose.com/omr/net/).
3. Βασικές γνώσεις .NET: Εξοικειωθείτε με το .NET Framework και τη γλώσσα προγραμματισμού C#.
## Εισαγωγή χώρων ονομάτων
Ξεκινήστε εισάγοντας τους απαραίτητους χώρους ονομάτων:
```csharp
using Aspose.OMR.Api;
using System;
using System.IO;
```
Ας αναλύσουμε το παράδειγμα κώδικα σε λεπτομερή βήματα:
## Βήμα 1: Ορισμός προτύπων και διαδρομών εικόνας
Καθορίστε τις διαδρομές για το πρότυπο OMR και τις εικόνες χρήστη:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## Βήμα 2: Ορίστε προσαρμοσμένο όριο
Καθορίστε το προσαρμοσμένο όριο για την επεξεργασία OMR:
```csharp
int CustomThreshold = 40;
```
## Βήμα 3: Προετοιμάστε την είσοδο και την έξοδο
Προετοιμάστε τους καταλόγους εισόδου και εξόδου για επεξεργασία OMR:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
```
## Βήμα 4: Εκκινήστε τον επεξεργαστή μηχανής και προτύπων
Εκκινήστε τον κινητήρα Aspose.OMR και αποκτήστε τον επεξεργαστή προτύπου:
```csharp
OmrEngine engine = new OmrEngine();
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## Βήμα 5: Εκτελέστε OMR με προσαρμοσμένο όριο
Επαναλάβετε σε κάθε εικόνα χρήστη και εκτελέστε OMR με το προσαρμοσμένο όριο:
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
## συμπέρασμα
Ακολουθώντας αυτό το σεμινάριο, μάθατε πώς να εκτελείτε την αναγνώριση οπτικών σημάτων με ένα προσαρμοσμένο όριο στο .NET χρησιμοποιώντας τη βιβλιοθήκη Aspose.OMR για .NET. Αυτή η δυνατότητα σάς δίνει τη δυνατότητα να προσαρμόσετε με ακρίβεια τη διαδικασία αναγνώρισης, βελτιώνοντας έτσι την ακρίβεια της εξαγωγής δεδομένων από σαρωμένες εικόνες.
## Συχνές Ερωτήσεις
### Ποια είναι η σημασία της χρήσης ενός προσαρμοσμένου ορίου στο OMR;
Ένα προσαρμοσμένο όριο επιτρέπει στους χρήστες να προσαρμόζουν την ευαισθησία της διαδικασίας αναγνώρισης, βελτιστοποιώντας έτσι την ακρίβεια με βάση συγκεκριμένα χαρακτηριστικά και απαιτήσεις εικόνας.
### Πώς διαφέρει το OMR με προσαρμοσμένο όριο από το τυπικό OMR;
Το τυπικό OMR εφαρμόζει προκαθορισμένα όρια για την ανίχνευση σήμανσης, ενώ το OMR με προσαρμοσμένο όριο επιτρέπει στους χρήστες να ορίζουν και να βελτιώνουν τις παραμέτρους αναγνώρισης σύμφωνα με τις ανάγκες τους.
### Ποιοι παράγοντες πρέπει να λαμβάνονται υπόψη κατά τον ορισμό ενός προσαρμοσμένου ορίου για το OMR;
Παράγοντες όπως η ποιότητα εικόνας, η ένταση σήμανσης και τα επίπεδα θορύβου φόντου θα πρέπει να λαμβάνονται υπόψη κατά τον καθορισμό του κατάλληλου προσαρμοσμένου ορίου για το OMR.
### Μπορεί το OMR με προσαρμοσμένο όριο να αυτοματοποιηθεί για ομαδική επεξεργασία;
Ναι, το OMR με προσαρμοσμένο όριο μπορεί να αυτοματοποιηθεί για ομαδική επεξεργασία πολλαπλών εικόνων, διευκολύνοντας την αποτελεσματική εξαγωγή δεδομένων σε σενάρια μεγάλης κλίμακας.
### Πού μπορώ να βρω πρόσθετους πόρους και υποστήριξη για το Aspose.OMR για .NET;
 Για τεκμηρίωση, υποστήριξη και αλληλεπίδραση με την κοινότητα, επισκεφθείτε τη διεύθυνση[Φόρουμ Aspose.OMR](https://forum.aspose.com/c/omr/38) και[επίσημη τεκμηρίωση](https://reference.aspose.com/omr/net/).