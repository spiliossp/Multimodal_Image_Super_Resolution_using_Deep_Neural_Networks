# README - Multimodal Image Super-Resolution using Deep Neural Networks

**Authors:** Spilios Spiliopoulos (4495), Evaggelia Tsiligianni

---

## ENGLISH

This document briefly describes the implementation notebooks of the Diploma Thesis:

### 1. Original_and_CoEvolving_LeSITA_basics.ipynb
- **Complexity:** Moderate
- **Type:** Skeleton (Blueprint)
- Contains the blueprint of the LeSITA algorithm, with the necessary modifications for the CoEvolving implementation
- This notebook presents an indicative, clean end-to-end processing flow
- It should be studied first in order to understand the next two notebooks
- Includes only the essential functions, without extra systems for scalability and logging
- Does not include experiments or results

### 2. Original_LeSITA.ipynb
- **Complexity:** Moderate
- **Type:** Implementation of the original LeSITA algorithm
- Primarily follows the methodology of your publications
- Includes modifications deemed necessary for algorithm efficiency, as detailed in the thesis (Image Super-Resolution Using Deep Neural Networks)
- Includes a system for visualizing results and immediate side-by-side comparison
- The experiments and results in the notebook are exactly the same as those reported in the thesis

### 3. CoEvolving_LeSITA_scalable_logs.ipynb
- **Complexity:** High
- **Type:** Implementation of the LeSITA algorithm with the CoEvolving approach
- Includes all the aforementioned features of Original_LeSITA.ipynb
- The experiments and results in the notebook are exactly the same as those reported in the thesis

#### **Tip:**
This notebook is the most complete and includes all the necessary systems for scalability and logging, so it can be used in a production environment. It implements the following automated systems as extra features and goes beyond the research scope of the thesis.

#### **EXTRA FEATURES:**

**Automated Systems:**
- Automatic directory management and file organization
- Intelligent model detection with recursive search
- Complete checkpoint system with resume-training capability
- Enhanced logging with real-time visualization
- Adaptive learning rate with meta-learning
- Multi-mode testing with comprehensive analysis
- Smart normalization for optimized visualization
- Interactive user interface with error handling
- Flexible training pipeline with quick-start options
- Performance comparison with paper benchmarks

**Additional Features:**
- Includes all scalability features for production use
- Full automation from training to final evaluation

#### **Extra Goal:**
The system was designed for full autonomy and professional use, with minimal user intervention requirements.

#### **Important Notes:**
- For better understanding the last notebook, it is recommended to study the previous two first
- The last notebook is quite extensive and there may be areas for improvement
- For further information or questions, feel free to contact me at: sphliossp@gmail.com

---

## ΕΛΛΗΝΙΚΑ

Στο συγκεκριμένο αρχείο περιγράφονται συνοπτικά τα notebooks της Διπλωματικής Εργασίας:

### 1. Original_and_CoEvolving_LeSITA_basics.ipynb
- **Πολυπλοκότητα:** Μεσαία
- **Τύπος:** Σκελετός (Σχεδιάγραμμα)
- Περιέχει το σχεδιάγραμμα του αλγορίθμου LeSITA, με τις απαραίτητες τροποποιήσεις για την υλοποίηση του CoEvolving
- Το συγκεκριμένο notebook παρουσιάζει ενδεικτικά ολόκληρη τη ροή επεξεργασίας, σε καθαρή μορφή
- Μπορεί να μελετηθεί ώστε να γίνουν κατανοητά τα επόμενα δύο
- Περιέχει μόνο τις απαραίτητες λειτουργίες, χωρίς επιπλέον συστήματα επεκτασιμότητας και καταγραφής
- Δεν περιέχει πειράματα και αποτελέσματα

### 2. Original_LeSITA.ipynb
- **Πολυπλοκότητα:** Μεσαία
- **Τύπος:** Υλοποίηση του αρχικού αλγορίθμου LeSITA
- Ακολουθεί κυρίως τη μεθοδολογία των δικών σας δημοσιεύσεων
- Περιέχει τροποποιήσεις που κρίθηκαν απαραίτητες για την αποδοτικότητα του αλγορίθμου, όπως ακριβώς περιγράφεται αναλυτικά στη διπλωματική εργασία (Υπέρ-Ανάλυση Εικόνας με Βαθιά Νευρωνικά Δίκτυα)
- Περιλαμβάνει σύστημα απεικόνισης των αποτελεσμάτων και άμεση σύγκριση δίπλα-δίπλα
- Τα πειράματα και τα αποτελέσματα που περιέχονται στο notebook είναι ακριβώς τα ίδια με αυτά που περιγράφονται στη διπλωματική εργασία

### 3. CoEvolving_LeSITA_scalable_logs.ipynb
- **Πολυπλοκότητα:** Υψηλή
- **Τύπος:** Υλοποίηση του αλγορίθμου LeSITA με προσέγγιση CoEvolving
- Περιέχει όλα τα προαναφερθέντα χαρακτηριστικά του Original_LeSITA.ipynb
- Τα πειράματα και τα αποτελέσματα που περιέχονται στο notebook είναι ακριβώς τα ίδια με αυτά που περιγράφονται στη διπλωματική εργασία

#### **Συμβουλή:**
Αυτό το notebook είναι το πιο πλήρες και περιέχει όλα τα απαραίτητα συστήματα για επεκτασιμότητα και καταγραφή, ώστε να μπορεί να χρησιμοποιηθεί σε περιβάλλον παραγωγής. Υλοποιεί τα παρακάτω αυτοματοποιημένα συστήματα ως επιπλέον χαρακτηριστικά και υπερβαίνει τους ερευνητικούς σκοπούς της εργασίας.

#### **ΕΠΙΠΛΕΟΝ ΧΑΡΑΚΤΗΡΙΣΤΙΚΑ:**

**Αυτοματοποιημένα Συστήματα:**
- Αυτόματη διαχείριση καταλόγων και οργάνωση αρχείων
- Έξυπνη ανίχνευση μοντέλων με αναδρομική αναζήτηση
- Πλήρες σύστημα αποθήκευσης προόδου με δυνατότητα συνέχισης εκπαίδευσης
- Ενισχυμένη καταγραφή με απεικόνιση σε πραγματικό χρόνο
- Προσαρμοστικός ρυθμός μάθησης με μετα-εκμάθηση
- Δοκιμές πολλαπλών τρόπων με ολοκληρωμένη ανάλυση
- Έξυπνη κανονικοποίηση για βελτιστοποιημένη απεικόνιση
- Διαδραστική διεπαφή χρήστη με χειρισμό σφαλμάτων
- Ευέλικτη ροή εκπαίδευσης με επιλογές γρήγορης εκκίνησης
- Σύγκριση επίδοσης με σημεία αναφοράς δημοσιεύσεων

**Επιπλέον Δυνατότητες:**
- Περιέχει όλα τα χαρακτηριστικά επεκτασιμότητας για χρήση σε παραγωγή
- Πλήρης αυτοματοποίηση από την εκπαίδευση έως την τελική αξιολόγηση

#### **Επιπλέον Στόχος:**
Το σύστημα σχεδιάστηκε με στόχο την πλήρη αυτονομία και την επαγγελματική χρήση, με ελάχιστες απαιτήσεις παρέμβασης από τον χρήστη.

#### **Σημαντικές Σημειώσεις:**
- Για την κατανόηση του τελευταίου notebook, προτείνεται η μελέτη των προηγούμενων δύο πρώτα
- Το τελευταίο notebook είναι αρκετά εκτενές και ενδέχεται να υπάρχουν σημεία προς βελτίωση
- Για περαιτέρω πληροφορίες ή ερωτήσεις, μη διστάσετε να επικοινωνήσετε μαζί μου στο: sphliossp@gmail.com

---

**Contact Information:** sphliossp@gmail.com