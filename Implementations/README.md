README - IMPLEMENTATION DETAILS

Documentation Language: (1 - English, 2 - Ελληνικά)

=========================	English	(1/2)	=============================

* Multimodal Image Super-Resolution using Deep Neural Networks
By: Spilios Spiliopoulos (4495), Pavlos-Lysimachos Kontis, Evaggelia Tsiligianni

This document briefly describes the implementation notebooks of the Diploma Thesis:

1. Convolutional_LISTA_ACSC.ipynb:

- Complexity: Basic
- Foundation (baseline implementation)
- Contains the basic implementation of the standard LISTA algorithm (ACSC module only).
- Processes single-modality input without side information or multimodal guidance.
- Serves as the fundamental building block for understanding the subsequent multimodal approaches.
- This notebook should be studied first as it provides the essential foundation for understanding the more complex notebooks.
- Includes clean, straightforward implementation without additional complexity layers.
- Essential prerequisite for comprehending the multimodal extensions.
- Flow: Single_LR_Input -> ACSC (3 unfolding stages) -> Sparse_Representations -> Reconstruction -> SR_Output

2. Original_and_CoEvolving_LMCSC_basics.ipynb:

- Complexity: Moderate
- Skeleton (blueprint)
- The ACSC model is responsible for finding sparse representations of the high-resolution side information image (T1W HR - Side Information).
- The LMCSC model is responsible for finding sparse representations of the main low-resolution input image (T2W LR - Main Input) based on sparse representations from ACSC.
- The classic LMCSC model:
    * Receives the T1W HR side information image, computes sparse representations Z through the ACSC model (3 stages).
    * Results from the FINAL STAGE of ACSC (sparse Z) are sent as input to the LMCSC network.
    * Finally, the LMCSC model receives the main T2W LR image in parallel, combining information from both input images, analyzes them through each unfolding stage and ultimately finds sparse representations U of the main input image.
- Flow: T1W_HR (side info) -> ACSC (3 stages) -> Sparse_Z + T2W_LR (main input) -> LMCSC (3 stages) -> Sparse_U -> Reconstruction -> T2W_HR (super-resolved)
- Contains the blueprint of the LeSITA algorithm, with the necessary modifications for the CoEvolving implementation.
- This notebook presents an indicative, clean end-to-end processing flow.
- It should be studied after LISTA.ipynb to understand the transition to multimodal processing.
- Includes only the essential functions, without extra systems for scalability and logging.
- Does not include experiments or results.

3. Original_LMCSC.ipynb:

- Complexity: Moderate
- The ACSC model processes the T1W HR side information image and extracts sparse representations Z.
- The LMCSC model is responsible for finding sparse representations U of the main T2W LR input image, based on sparse representations Z received from the ACSC model.
- The classic LMCSC model operates sequentially:
    * First, T1W HR is fed into ACSC and sparse representations Z are computed through 3 unfolding stages.
    * Then, results from the FINAL STAGE of ACSC (Z) are transferred to the LMCSC network.
    * LMCSC receives the main T2W LR image in parallel, combines information from both sources, and through 3 unfolding stages computes sparse representations U.
- The LMCSC model depends entirely on the ACSC model (sequential dependency).
- Flow: T1W_HR -> ACSC (3 stages) -> Final_Z → LMCSC (T2W_LR + Final_Z, 3 stages) -> Sparse_U -> Reconstruction -> T2W_HR
- Implementation of the original LeSITA algorithm.
- Primarily follows the methodology of your publications.
- Includes modifications deemed necessary for algorithm efficiency, as detailed in the thesis (Image Super-Resolution Using Deep Neural Networks).
- Includes a system for visualizing results and immediate side-by-side comparison.
- The experiments and results in the notebook are exactly the same as those reported in the thesis.

4. CoEvolving_LMCSC_scalable_logs.ipynb:

- Complexity: High
- The CoEvolving LMCSC model is responsible for simultaneous finding of sparse representations for both images (T1W HR and T2W LR) with bidirectional information exchange.
- The main difference from the classic LMCSC model is that sparse representations Z and U for each input image evolve gradually and in parallel at each unfolding stage.
- CoEvolving Architecture:
    * At each stage, ACSC processes T1W HR and updates the Z representation.
    * In parallel, LMCSC processes T2W LR using the current Z and updates the U representation.
    * The process repeats for 2 total stages (instead of 3+3 in sequential).
- In this way, information exchange between sparse representations of the two input images is bidirectional and dynamic.
- Observed differences: Output image textures are captured better and more visibly compared to the classic LMCSC. However, optimal PSNR results are achieved with the classic LMCSC model.
- Flow: (T1W_HR, T2W_LR) -> [ACSC_stage1 -> Z1, LMCSC_stage1 -> U1] -> [ACSC_stage2 -> Z2, LMCSC_stage2 -> U2] -> Final_U -> Reconstruction -> T2W_HR
- Implementation of the LeSITA algorithm with the CoEvolving approach.
- Includes all the aforementioned features of original_LMCSC.ipynb.
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
Convolutional_LISTA_ACSC.ipynb → Original_and_CoEvolving_LMCSC_basics.ipynb → Original_LMCSC.ipynb → CoEvolving_LMCSC_scalable_logs.ipynb
- The progression from single-modality to multimodal processing is crucial for comprehension.
- The last notebook is quite extensive and there may be areas for improvement.
- For further information or questions, please feel free to contact me at: sphliossp@gmail.com

---

Contact Information: sphliossp@gmail.com

=========================	Ελληνικά (2/2)	=============================

Πολυτροπική Υπέρ-Ανάλυση Εικόνας με Βαθιά Νευρωνικά Δίκτυα
Από: Σπήλιος Σπηλιόπουλος (4495), Παύλος-Λυσίμαχος Κόντης, Ευαγγελία Τσιλιγιάννη

Στο συγκεκριμένο αρχείο περιγράφονται συνοπτικά τα notebooks της Διπλωματικής Εργασίας:

1. Convolutional_LISTA_ACSC.ipynb:

- Πολυπλοκότητα: Βασική
- Θεμέλιο (baseline υλοποίηση)
- Περιέχει τη βασική υλοποίηση του τυπικού αλγόριθμου LISTA (μόνο ACSC module).
- Επεξεργάζεται είσοδο μονής τροπικότητας χωρίς βοηθητική πληροφορία ή multimodal καθοδήγηση.
- Χρησιμεύει ως το θεμελιώδες δομικό στοιχείο για την κατανόηση των επόμενων πολυτροπικών προσεγγίσεων.
- Αυτό το notebook πρέπει να μελετηθεί πρώτα καθώς παρέχει τη βασική βάση για την κατανόηση των πιο σύνθετων notebooks.
- Περιλαμβάνει καθαρή, απλή υλοποίηση χωρίς επιπρόσθετα στρώματα πολυπλοκότητας.
- Απαραίτητη προϋπόθεση για την κατανόηση των πολυτροπικών επεκτάσεων.
- Flow: Single_LR_Input -> ACSC (3 unfolding stages) -> Sparse_Representations -> Reconstruction -> SR_Output

2. Original_and_CoEvolving_LMCSC_basics.ipynb:

- Πολυπλοκότητα: Μεσαία
- Σκελετός (σχεδιάγραμμα)
- Το μοντέλο ACSC είναι υπεύθυνο για την εύρεση αραιών αναπαραστάσεων της βοηθητικής εικόνας υψηλής ανάλυσης (T1W HR - Side Information).
- Το μοντέλο LMCSC είναι υπεύθυνο για την εύρεση αραιών αναπαραστάσεων της κύριας εικόνας εισόδου χαμηλής ανάλυσης (T2W LR - Main Input) με βάση τις αραιές αναπαραστάσεις από το ACSC.
- Το κλασσικό LMCSC μοντέλο:
    * Δέχεται την βοηθητική εικόνα T1W HR, υπολογίζει τις αραιές αναπαραστάσεις Z μέσω του ACSC μοντέλου (3 στάδια).
    * Τα αποτελέσματα του ΤΕΛΙΚΟΥ ΣΤΑΔΙΟΥ ACSC (sparse Z) στέλνονται ως είσοδο στο LMCSC δίκτυο.
    * Τέλος, το LMCSC μοντέλο δέχεται παράλληλα ως είσοδο την κύρια εικόνα T2W LR, συνδυάζοντας πληροφορία από τις 2 εικόνες εισόδου, τις αναλύει μέσα από κάθε στάδιο αναδίπλωσης και τελικά βρίσκει τις αραιές αναπαραστάσεις U της κύριας εικόνας εισόδου.
- Flow: T1W_HR (side info) -> ACSC (3 stages) -> Sparse_Z + T2W_LR (main input) -> LMCSC (3 stages) -> Sparse_U -> Reconstruction -> T2W_HR (super-resolved)
- Περιέχει το σχεδιάγραμμα του αλγόριθμου LeSITA, με τις απαραίτητες τροποποιήσεις για την υλοποίηση του CoEvolving.
- Το συγκεκριμένο notebook παρουσιάζει ενδεικτικά ολόκληρη τη ροή επεξεργασίας, σε καθαρή μορφή.
- Μπορεί να μελετηθεί μετά το LISTA.ipynb για να γίνει κατανοητή η μετάβαση στην πολυτροπική επεξεργασία.
- Περιέχει μόνο τις απαραίτητες λειτουργίες, χωρίς επιπλέον συστήματα επεκτασιμότητας και καταγραφής.
- Δεν περιέχει πειράματα και αποτελέσματα.

3. Original_LMCSC.ipynb:

- Πολυπλοκότητα: Μεσαία
- Το μοντέλο ACSC επεξεργάζεται την βοηθητική εικόνα T1W HR και εξάγει αραιές αναπαραστάσεις Z.
- Το μοντέλο LMCSC είναι υπεύθυνο για την εύρεση αραιών αναπαραστάσεων U της κύριας εικόνας εισόδου T2W LR, με βάση τις αραιές αναπαραστάσεις Z που δέχεται από το μοντέλο ACSC.
- Το κλασσικό LMCSC μοντέλο λειτουργεί σειριακά:
    * Πρώτα η T1W HR εισάγεται στο ACSC και υπολογίζονται οι αραιές αναπαραστάσεις Z μέσω 3 σταδίων αναδίπλωσης.
    * Στη συνέχεια, τα αποτελέσματα του ΤΕΛΙΚΟΥ ΣΤΑΔΙΟΥ του ACSC (Z) μεταβιβάζονται στο LMCSC δίκτυο.
    * Το LMCSC δέχεται παράλληλα την κύρια εικόνα T2W LR, συνδυάζει πληροφορία από τις δύο πηγές, και μέσω 3 σταδίων αναδίπλωσης υπολογίζει τις αραιές αναπαραστάσεις U.
- Το μοντέλο LMCSC εξαρτάται πλήρως από το μοντέλο ACSC (sequential dependency).
- Flow: T1W_HR -> ACSC (3 stages) -> Final_Z → LMCSC (T2W_LR + Final_Z, 3 stages) -> Sparse_U -> Reconstruction -> T2W_HR
- Υλοποίηση του αρχικού αλγόριθμου LeSITA.
- Ακολουθεί κυρίως τη μεθοδολογία των δικών σας δημοσιεύσεων.
- Περιέχει τροποποιήσεις που κρίθηκαν απαραίτητες για την αποδοτικότητα του αλγόριθμου, όπως ακριβώς περιγράφεται αναλυτικά στη διπλωματική εργασία (Υπέρ-Ανάλυση Εικόνας με Βαθιά Νευρωνικά Δίκτυα).
- Περιλαμβάνει σύστημα απεικόνισης των αποτελεσμάτων και άμεση σύγκριση δίπλα-δίπλα.
- Τα πειράματα και τα αποτελέσματα που περιέχονται στο notebook είναι ακριβώς τα ίδια με αυτά που περιγράφονται στη διπλωματική εργασία.

4. CoEvolving_LMCSC_scalable_logs.ipynb:

- Πολυπλοκότητα: Υψηλή
- Το μοντέλο CoEvolving LMCSC είναι υπεύθυνο για την ταυτόχρονη εύρεση αραιών αναπαραστάσεων και των δύο εικόνων (T1W HR και T2W LR) με αμφίδρομη ανταλλαγή πληροφορίας.
- Η κύρια διαφορά με το κλασσικό LMCSC μοντέλο είναι ότι οι αραιές αναπαραστάσεις Z και U για κάθε εικόνα εισόδου εξελίσσονται σταδιακά και παράλληλα σε κάθε στάδιο αναδίπλωσης.
- Αρχιτεκτονική CoEvolving:
    * Σε κάθε στάδιο, το ACSC επεξεργάζεται την T1W HR και ενημερώνει τη Z αναπαράσταση.
    * Παράλληλα, το LMCSC επεξεργάζεται την T2W LR χρησιμοποιώντας την τρέχουσα Z και ενημερώνει την U αναπαράσταση.
    * Η διαδικασία επαναλαμβάνεται για 2 συνολικά στάδια (αντί για 3+3 στο sequential).
- Κατά αυτόν τον τρόπο, η ανταλλαγή πληροφορίας μεταξύ των αραιών αναπαραστάσεων των δύο εικόνων εισόδων είναι αμφίδρομη και δυναμική.
- Παρατηρούμενες διαφορές: Οι υφές της εικόνας εξόδου αποτυπώνονται καλύτερα και πιο ορατά σε σχέση με το κλασσικό LMCSC. Ωστόσο, τα βέλτιστα αποτελέσματα PSNR επιτυγχάνονται με το κλασσικό LMCSC μοντέλο.
- Flow: (T1W_HR, T2W_LR) -> [ACSC_stage1 -> Z1, LMCSC_stage1 -> U1] -> [ACSC_stage2 -> Z2, LMCSC_stage2 -> U2] -> Final_U -> Reconstruction -> T2W_HR
- Υλοποίηση του αλγόριθμου LeSITA με προσέγγιση CoEvolving.
- Περιέχει όλα τα προαναφερθέντα χαρακτηριστικά του original_LMCSC.ipynb.
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
Convolutional_LISTA_ACSC.ipynb → Original_and_CoEvolving_LMCSC_basics.ipynb → Original_LMCSC.ipynb → CoEvolving_LMCSC_scalable_logs.ipynb
- Η εξέλιξη από τη μονο-τροπική στην πολυτροπική επεξεργασία είναι κρίσιμη για την κατανόηση.
- Το τελευταίο notebook είναι αρκετά εκτενές και ενδέχεται να υπάρχουν σημεία προς βελτίωση.
- Για περαιτέρω πληροφορίες ή ερωτήσεις, μη διστάσετε να επικοινωνήσετε μαζί μου στο: sphliossp@gmail.com

---

Πληροφορίες Επικοινωνίας: sphliossp@gmail.com