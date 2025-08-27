Documentation Language: (1 - English, 2 - Ελληνικά)

=========================	English	(1/2)	=============================

* Multimodal Image Super-Resolution using Deep Neural Networks
By: Spilios Spiliopoulos (4495), Pavlos-Lysimachos Kontis, Evaggelia Tsiligianni

This document briefly describes the implementation notebooks of the Diploma Thesis:

1. LISTA.ipynb:

- Complexity: Basic
- Foundation (baseline implementation)
- Contains the basic implementation of the standard LISTA algorithm (ACSC module only).
- Processes single-modality input without side information or guidance.
- Serves as the fundamental building block for understanding the subsequent multimodal approaches.
- This notebook should be studied first as it provides the essential foundation for understanding the more complex notebooks.
- Includes clean, straightforward implementation without additional complexity layers.
- Essential prerequisite for comprehending the multimodal extensions.

2. Original_and_CoEvolving_LeSITA_basics.ipynb:

- Complexity: Moderate
- Skeleton (blueprint)
- Contains the blueprint of the LeSITA algorithm, with the necessary modifications for the CoEvolving implementation.
- This notebook presents an indicative, clean end-to-end processing flow.
- It should be studied after LISTA.ipynb to understand the transition to multimodal processing.
- Includes only the essential functions, without extra systems for scalability and logging.
- Does not include experiments or results.

3. Original_LeSITA.ipynb:

- Complexity: Moderate
- Implementation of the original LeSITA algorithm.
- Primarily follows the methodology of your publications.
- Includes modifications deemed necessary for algorithm efficiency, as detailed in the thesis (Image Super-Resolution Using Deep Neural Networks).
- Includes a system for visualizing results and immediate side-by-side comparison.
- The experiments and results in the notebook are exactly the same as those reported in the thesis.

4. CoEvolving_LeSITA_scalable_logs.ipynb:

- Complexity: High
- Implementation of the LeSITA algorithm with the CoEvolving approach.
- Includes all the aforementioned features of original_LeSITA.ipynb.
- The experiments and results in the notebook are exactly the same as those reported in the thesis.

Tip:
- This notebook is the most complete and includes all the necessary systems for scalability and logging, so it can be used in a production environment.
- It implements the following automated systems as extra features and goes beyond the research scope of the thesis.

Extra Features:

--------------------- Automated Systems ---------------------
• Automatic directory management and file organization 
• Intelligent model detection with recursive search 
• Complete checkpoint system with resume-training capability 
• Enhanced logging with real-time visualization 
• Adaptive learning rate with meta-learning 
• Multi-mode testing with comprehensive analysis 
• Smart normalization for optimized visualization 
• Interactive user interface with error handling 
• Flexible training pipeline with quick-start options 
• Performance comparison with paper benchmarks

- Includes all scalability features for production use
- Full automation from training to final evaluation

Extra Goal:
The system was designed for full autonomy and professional use, with minimal user intervention requirements.

Attention:
- For better understanding the advanced notebooks, it is recommended to study them in order: 
LISTA.ipynb → Original_and_CoEvolving_LeSITA_basics.ipynb → Original_LeSITA.ipynb → CoEvolving_LeSITA_scalable_logs.ipynb
- The progression from single-modality to multimodal processing is crucial for comprehension.
- The last notebook is quite extensive and there may be areas for improvement.

---

Contact Information: sphliossp@gmail.com

=========================	Ελληνικά (2/2)	=============================

Πολυτροπική Υπέρ-Ανάλυση Εικόνας με Βαθιά Νευρωνικά Δίκτυα
Από: Σπήλιος Σπηλιόπουλος (4495), Παύλος-Λυσίμαχος Κόντης, Ευαγγελία Τσιλιγιάννη

Στο συγκεκριμένο αρχείο περιγράφονται συνοπτικά τα notebooks της Διπλωματικής Εργασίας:

1. LISTA.ipynb:

- Πολυπλοκότητα: Βασική
- Θεμέλιο (baseline υλοποίηση)
- Περιέχει τη βασική υλοποίηση του τυπικού αλγόριθμου LISTA (μόνο ACSC module).
- Επεξεργάζεται είσοδο μονής τροπικότητας χωρίς βοηθητική πληροφορία ή καθοδήγηση.
- Χρησιμεύει ως το θεμελιώδες δομικό στοιχείο για την κατανόηση των επόμενων πολυτροπικών προσεγγίσεων.
- Αυτό το notebook πρέπει να μελετηθεί πρώτα καθώς παρέχει τη βασική βάση για την κατανόηση των πιο σύνθετων notebooks.
- Περιλαμβάνει καθαρή, απλή υλοποίηση χωρίς επιπρόσθετα στρώματα πολυπλοκότητας.
- Απαραίτητη προϋπόθεση για την κατανόηση των πολυτροπικών επεκτάσεων.

2. Original_and_CoEvolving_LeSITA_basics.ipynb:

- Πολυπλοκότητα: Μεσαία
- Σκελετός (σχεδιάγραμμα)
- Περιέχει το σχεδιάγραμμα του αλγόριθμου LeSITA, με τις απαραίτητες τροποποιήσεις για την υλοποίηση του CoEvolving.
- Το συγκεκριμένο notebook παρουσιάζει ενδεικτικά ολόκληρη τη ροή επεξεργασίας, σε καθαρή μορφή.
- Μπορεί να μελετηθεί μετά το LISTA.ipynb για να γίνει κατανοητή η μετάβαση στην πολυτροπική επεξεργασία.
- Περιέχει μόνο τις απαραίτητες λειτουργίες, χωρίς επιπλέον συστήματα επεκτασιμότητας και καταγραφής.
- Δεν περιέχει πειράματα και αποτελέσματα.

3. Original_LeSITA.ipynb:

- Πολυπλοκότητα: Μεσαία
- Υλοποίηση του αρχικού αλγόριθμου LeSITA.
- Ακολουθεί κυρίως τη μεθοδολογία των δικών σας δημοσιεύσεων.
- Περιέχει τροποποιήσεις που κρίθηκαν απαραίτητες για την αποδοτικότητα του αλγόριθμου, όπως ακριβώς περιγράφεται αναλυτικά στη διπλωματική εργασία (Υπέρ-Ανάλυση Εικόνας με Βαθιά Νευρωνικά Δίκτυα).
- Περιλαμβάνει σύστημα απεικόνισης των αποτελεσμάτων και άμεση σύγκριση δίπλα-δίπλα.
- Τα πειράματα και τα αποτελέσματα που περιέχονται στο notebook είναι ακριβώς τα ίδια με αυτά που περιγράφονται στη διπλωματική εργασία.

4. CoEvolving_LeSITA_scalable_logs.ipynb:

- Πολυπλοκότητα: Υψηλή
- Υλοποίηση του αλγόριθμου LeSITA με προσέγγιση CoEvolving.
- Περιέχει όλα τα προαναφερθέντα χαρακτηριστικά του original_LeSITA.ipynb.
- Τα πειράματα και τα αποτελέσματα που περιέχονται στο notebook είναι ακριβώς τα ίδια με αυτά που περιγράφονται στη διπλωματική εργασία.

Συμβουλή:
- Αυτό το notebook είναι το πιο πλήρες και περιέχει όλα τα απαραίτητα συστήματα για επεκτασιμότητα και καταγραφή, ώστε να μπορεί να χρησιμοποιηθεί σε περιβάλλον παραγωγής.
- Υλοποιεί τα παρακάτω αυτοματοποιημένα συστήματα ως επιπλέον χαρακτηριστικά και υπερβαίνει τους ερευνητικούς σκοπούς της εργασίας.

Επιπλέον Χαρακτηριστικά:

---------------------------- Αυτόματα Συστήματα ----------------------------
• Αυτόματη διαχείριση καταλόγων και οργάνωση αρχείων 
• Έξυπνη ανίχνευση μοντέλων με αναδρομική αναζήτηση 
• Πλήρες σύστημα αποθήκευσης προόδου με δυνατότητα συνέχισης εκπαίδευσης 
• Ενισχυμένη καταγραφή με απεικόνιση σε πραγματικό χρόνο 
• Προσαρμοστικός ρυθμός μάθησης από το ίδιο το μοντέλο
• Δοκιμές πολλαπλών τρόπων με ολοκληρωμένη ανάλυση 
• Έξυπνη κανονικοποίηση για βελτιστοποιημένη απεικόνιση 
• Διαδραστική διεπαφή χρήστη με χειρισμό σφαλμάτων 
• Ευέλικτη ροή εκπαίδευσης με επιλογές γρήγορης εκκίνησης 
• Σύγκριση επίδοσης με σημεία αναφοράς δημοσιεύσεων

- Περιέχει όλα τα χαρακτηριστικά επεκτασιμότητας για χρήση σε παραγωγή
- Πλήρης αυτοματοποίηση από την εκπαίδευση έως την τελική αξιολόγηση

Επιπλέον Στόχος:
Το σύστημα σχεδιάστηκε με στόχο την πλήρη αυτονομία και την επαγγελματική χρήση, με ελάχιστες απαιτήσεις παρέμβασης από τον χρήστη.

Σημαντικές Σημειώσεις:
- Για την κατανόηση των προχωρημένων notebooks, προτείνεται η μελέτη τους με σειρά: 
LISTA.ipynb → Original_and_CoEvolving_LeSITA_basics.ipynb → Original_LeSITA.ipynb → CoEvolving_LeSITA_scalable_logs.ipynb
- Η εξέλιξη από τη μονο-τροπική στην πολυτροπική επεξεργασία είναι κρίσιμη για την κατανόηση.
- Το τελευταίο notebook είναι αρκετά εκτενές και ενδέχεται να υπάρχουν σημεία προς βελτίωση.
- Για περαιτέρω πληροφορίες ή ερωτήσεις, μη διστάσετε να επικοινωνήσετε μαζί μου στο: sphliossp@gmail.com

---

Πληροφορίες Επικοινωνίας: sphliossp@gmail.com