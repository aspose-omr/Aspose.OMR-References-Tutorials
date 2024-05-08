---
title: Εκτελέστε επανυπολογισμό OMR στο .NET
linktitle: Εκτελέστε επανυπολογισμό OMR στο .NET
second_title: Aspose.OMR .NET API
description: Μάθετε πώς να εκτελείτε εκ νέου υπολογισμό της Αναγνώρισης οπτικών σημάτων στο .NET χρησιμοποιώντας το Aspose.OMR για .NET. Βελτιώστε την ακρίβεια των δεδομένων από σαρωμένες εικόνες!
type: docs
weight: 12
url: /el/net/omr-operations/perform-omr-recalculation/
---
Σε αυτό το σεμινάριο, θα σας καθοδηγήσουμε στη διαδικασία εκτέλεσης επανυπολογισμού Optical Mark Recognition (OMR) στο .NET χρησιμοποιώντας τη βιβλιοθήκη Aspose.OMR για .NET. Ο επανυπολογισμός OMR σάς επιτρέπει να προσαρμόζετε τα αποτελέσματα αναγνώρισης βάσει προσαρμοσμένων ορίων, βελτιώνοντας την ακρίβεια της εξαγωγής δεδομένων από σαρωμένες εικόνες.
## Προαπαιτούμενα
Πριν προχωρήσετε, βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις:
1. Visual Studio: Εγκαταστήστε το Visual Studio στο σύστημά σας για ανάπτυξη .NET.
2.  Aspose.OMR for .NET Library: Κατεβάστε και εγκαταστήστε τη βιβλιοθήκη Aspose.OMR για .NET από το[επίσημη ιστοσελίδα](https://releases.aspose.com/omr/net/).
3. Βασικές γνώσεις .NET: Εξοικειωθείτε με το .NET Framework και τη γλώσσα προγραμματισμού C#.
## Εισαγωγή χώρων ονομάτων
Ξεκινήστε εισάγοντας τους απαραίτητους χώρους ονομάτων:
```csharp
using Aspose.OMR.Api;
using Aspose.OMR.Model;
using System;
using System.Diagnostics;
using System.IO;
```
Ας αναλύσουμε το παράδειγμα κώδικα σε λεπτομερή βήματα:
## Βήμα 1: Ορισμός προτύπων και διαδρομών εικόνας
Καθορίστε τις διαδρομές για το πρότυπο OMR και τις εικόνες χρήστη:
```csharp
string TemplateName = @"Sheet.omr";
string[] UserImages = new string[] { "Sheet1.jpg", "Sheet2.jpg" };
```
## Βήμα 2: Ρύθμιση φακέλων
Προετοιμάστε τους καταλόγους εισόδου και εξόδου για επεξεργασία OMR:
```csharp
string testFolderPath = "Your Document Directory";
string templatePath = Path.Combine(testFolderPath, TemplateName);
string outputPath = "Your Output Directory";
int CustomThreshold = 40; // Ορίστε προσαρμοσμένο όριο
```
## Βήμα 3: Εκκινήστε τον επεξεργαστή μηχανής και προτύπων
Εκκινήστε τον κινητήρα Aspose.OMR και αποκτήστε τον επεξεργαστή προτύπου:
```csharp
OmrEngine engine = new OmrEngine();
TemplateProcessor templateProcessor = engine.GetTemplateProcessor(templatePath);
Console.WriteLine("Template loaded.");
```
## Βήμα 4: Επεξεργασία εικόνων χρήστη
Επαναλάβετε σε κάθε εικόνα χρήστη για να εκτελέσετε εκ νέου υπολογισμό OMR:
```csharp
for (int i = 0; i < UserImages.Length; i++)
{
    string image = UserImages[i];
    string imagePath = Path.Combine(testFolderPath, image);
    Console.WriteLine("\n\rProcessing image: " + imagePath);
    // Μετρήστε τον χρόνο απόδοσης
    Stopwatch sw = Stopwatch.StartNew();
    // Αναγνώριση εικόνας
    RecognitionResult result = templateProcessor.RecognizeImage(imagePath);
    sw.Stop();
    Console.WriteLine("Recognition time: " + sw.Elapsed);
    // Εξαγωγή αποτελεσμάτων αναγνώρισης σε CSV
    string stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"), stringRes);
    Console.WriteLine("Result Exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + ".csv"));
    sw.Restart();
    // Εκτελέστε εκ νέου υπολογισμό OMR με προσαρμοσμένο όριο
    Console.WriteLine("\n\rPerforming recalculation\n\r");
    templateProcessor.Recalculate(result, CustomThreshold);
    sw.Stop();
    Console.WriteLine("Recalculation time: " + sw.Elapsed);
    // Εξαγωγή επανυπολογισμένων αποτελεσμάτων
    stringRes = result.GetCsv();
    File.WriteAllText(Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"), stringRes);
    Console.WriteLine("Recalculation result exported. Path: " + Path.Combine(outputPath, Path.GetFileNameWithoutExtension(image) + "_Recalculated.csv"));
}
```
## Βήμα 5: Συμπέρασμα
Πραγματοποιήσατε επιτυχώς επανυπολογισμό Optical Mark Recognition στο .NET χρησιμοποιώντας το Aspose.OMR για .NET. Αυτή η δυνατότητα σάς επιτρέπει να προσαρμόσετε τα αποτελέσματα αναγνώρισης με βάση προσαρμοσμένα όρια, βελτιώνοντας την ακρίβεια των δεδομένων.
## συμπέρασμα
Συμπερασματικά, η βιβλιοθήκη Aspose.OMR για .NET παρέχει ισχυρά εργαλεία για εργασίες αναγνώρισης οπτικών σημάτων σε εφαρμογές .NET. Ακολουθώντας τα βήματα που περιγράφονται σε αυτό το σεμινάριο, μπορείτε να ενσωματώσετε απρόσκοπτα τις δυνατότητες επανυπολογισμού OMR στα έργα σας, βελτιώνοντας την ακρίβεια της εξαγωγής δεδομένων από σαρωμένες εικόνες.
## Συχνές Ερωτήσεις
### Τι είναι ο επανυπολογισμός OMR και γιατί είναι σημαντικός;
Ο επανυπολογισμός OMR είναι η διαδικασία προσαρμογής των αποτελεσμάτων αναγνώρισης βάσει προσαρμοσμένων ορίων. Είναι σημαντικό για τη βελτίωση της ακρίβειας της εξαγωγής δεδομένων από σαρωμένες εικόνες, ειδικά σε σενάρια όπου η τυπική αναγνώριση μπορεί να μην αρκεί.
### Πώς διαφέρει ο επανυπολογισμός OMR από την τυπική αναγνώριση;
Ο επανυπολογισμός OMR επιτρέπει πιο λεπτές προσαρμογές στα αποτελέσματα αναγνώρισης με την εφαρμογή προσαρμοσμένων ορίων, ενώ η τυπική αναγνώριση ακολουθεί προκαθορισμένους αλγόριθμους χωρίς παρέμβαση του χρήστη.
### Μπορεί ο επανυπολογισμός OMR να αυτοματοποιηθεί σε εφαρμογές .NET;
Ναι, ο επανυπολογισμός OMR μπορεί να αυτοματοποιηθεί σε εφαρμογές .NET ενσωματώνοντας τη βιβλιοθήκη Aspose.OMR για .NET και χρησιμοποιώντας το API του για την επεξεργασία εικόνων και την προσαρμογή των αποτελεσμάτων αναγνώρισης.
### Ποιοι παράγοντες πρέπει να λαμβάνονται υπόψη κατά τον καθορισμό του προσαρμοσμένου ορίου για τον επανυπολογισμό OMR;
Παράγοντες όπως η ποιότητα εικόνας, η πυκνότητα σήμανσης και το επιθυμητό επίπεδο ακρίβειας θα πρέπει να λαμβάνονται υπόψη κατά τον καθορισμό του προσαρμοσμένου ορίου για τον επανυπολογισμό OMR.
### Πού μπορώ να βρω πρόσθετους πόρους και υποστήριξη για το Aspose.OMR για .NET;
 Για τεκμηρίωση, υποστήριξη και αλληλεπίδραση με την κοινότητα, επισκεφθείτε τη διεύθυνση[Φόρουμ Aspose.OMR](https://forum.aspose.com/c/omr/38) και[επίσημη τεκμηρίωση](https://reference.aspose.com/omr/net/).