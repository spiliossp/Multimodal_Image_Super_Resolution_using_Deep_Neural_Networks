README - MULTIMODAL IMAGE SUPER RESOLUTION USING DEEP NEURAL NETWORKS

ΠΕΡΙΛΗΨΗ / ABSTRACT

Αυτή η διπλωματική εργασία αντιμετωπίζει το πρόβλημα της υπερανάλυσης ιατρικών εικόνων μαγνητικής τομογραφίας (MRI) μέσω μιας καινοτόμου προσέγγισης που συνδυάζει τη θεωρία των αραιών αναπαραστάσεων με τεχνικές βαθιάς αναδίπλωσης. Το σύστημα Learned Multimodal Convolutional Sparse Coding (LMCSC) υλοποιεί μια διπλού-κλάδου αρχιτεκτονική που αξιοποιεί τη συμπληρωματική πληροφορία από διαφορετικές MRI sequences για την παραγωγή εικόνων υψηλής ανάλυσης.

ΚΥΡΙΑ ΕΠΙΤΕΥΓΜΑΤΑ:
- PSNR: 41.77 dB (βελτίωση +0.83 dB από state-of-the-art)
- Εξαιρετική ταχύτητα σύγκλισης σε μόλις 15-50 εποχές εκπαίδευσης
- Ερμηνεύσιμη αρχιτεκτονική βασισμένη σε deep unfolding

ΔΟΜΗ PROJECT

Multimodal_Image_Super_Resolution_using_Deep_Neural_Networks/
    Diploma_Thesis/ - Διπλωματική εργασία (PDF)
    Images/ - Φάκελος εικόνων
        LISTA/ - Αποτελέσματα baseline LISTA
        CoEvolving_LeSITA_LMCSC_model/
        LeSITA_LMCSC_model/
    Implementation/ - Κώδικας υλοποίησης
        Other/ - Βοηθητικά αρχεία
        LISTA.ipynb
        CoEvolving_LeSITA_scalable_logs.ipynb
        Original_and_CoEvolving_LeSITA_basics.ipynb
        Original_LeSITA.ipynb
        README_en_gr.txt

ΑΝΑΛΥΤΙΚΗ ΔΟΜΗ MODELS

LISTA/ - Baseline single-modality implementation
    1 εικόνα αποτελέσματος

LeSITA_LMCSC_model/
    50_test_cases/
    graphs/
    test_results/

CoEvolving_LeSITA_LMCSC_model/
    graphs/
    test_results/

ΓΡΗΓΟΡΗ ΕΚΚΙΝΗΣΗ

ΑΠΑΙΤΗΣΕΙΣ:
- Python 3.8+
- PyTorch
- CUDA-compatible GPU
- Libraries: requirements.txt 

ΕΓΚΑΤΑΣΤΑΣΗ:
1. git clone https://github.com/spiliossp/Multimodal_Image_Super_Resolution_using_Deep_Neural_Networks.git
2. cd Multimodal_Image_Super_Resolution_using_Deep_Neural_Networks
3. pip install -r requirements.txt

ΧΡΗΣΗ:

ΣΕΙΡΑ ΕΚΜΑΘΗΣΗΣ (Προτεινόμενη):
1. Baseline LISTA:
   jupyter notebook Implementation/LISTA.ipynb

2. Βασικές Έννοιες Multimodal:
   jupyter notebook Implementation/Original_and_CoEvolving_LeSITA_basics.ipynb

3. Εκπαίδευση Original LeSITA:
   jupyter notebook Implementation/Original_LeSITA.ipynb

4. Εκπαίδευση CoEvolving LeSITA:
   jupyter notebook Implementation/CoEvolving_LeSITA_scalable_logs.ipynb

ΑΡΧΙΤΕΚΤΟΝΙΚΗ

BASELINE LISTA MODEL
Single-Modality Approach - Επεξεργάζεται μόνο την εικόνα εισόδου χωρίς βοηθητική πληροφορία.

ΧΑΡΑΚΤΗΡΙΣΤΙΚΑ:
- Μόνο ACSC module (Aproximate Convolutional Sparse Coding)
- Χωρίς side information
- Θεμελιώδης υλοποίηση για κατανόηση της αρχιτεκτονικής
- Απαραίτητο πρώτο βήμα εκμάθησης

LeSITA LMCSC MODEL
Sequential Approach - Η βοηθητική πληροφορία (T1W) επεξεργάζεται πρώτα και στη συνέχεια καθοδηγεί την υπερανάλυση της εικόνας εισόδου (T2W).

ΧΑΡΑΚΤΗΡΙΣΤΙΚΑ:
- 3 στάδια αναδίπλωσης
- 85 φίλτρα ανά στρώμα
- Συνελικτικοί πυρήνες 7x7
- Παράμετροι: γ = 0.1 (sparsity), μ = 0.1 (coupling)

CoEvolving LeSITA LMCSC MODEL
Co-evolving Approach - Οι δύο τύποι αραιών αναπαραστάσεων των εικόνων εξελίσσονται παράλληλα με δυναμική αλληλεπίδραση.

ΒΕΛΤΙΩΣΕΙΣ:
- Συν-εξελισσόμενη αρχιτεκτονική
- Βελτιωμένη διατήρηση υφών
- Δυναμική αλληλεπίδραση μεταξύ U,Z αναπαραστάσεων

ΑΠΟΤΕΛΕΣΜΑΤΑ

ΠΟΣΟΤΙΚΑ ΑΠΟΤΕΛΕΣΜΑΤΑ:
LISTA Baseline: ~35 dB PSNR, Single modality, Basic implementation
LeSITA LMCSC: 41.77 dB PSNR, 3 Στάδια, Sequential processing
CoEvolving LMCSC: 41.36 dB PSNR, 2 Στάδια, Co-evolving architecture

ΣΥΓΚΡΙΣΗ ΜΕ STATE-OF-THE-ART:
BICUBIC: 28.5 dB
SRCNN: 32.1 dB
VDSR: 34.2 dB
EDSR: 36.8 dB
Our LISTA (Baseline): ~ 40.65 dB
Our LMCSC: 41.77 dB

TRAINING METRICS:
- Εποχές Εκπαίδευσης: 15-50
- Batch Size: 32 (εκπαίδευση), 8 (αξιολόγηση)
- Learning Rate: 1e-4
- Optimizer: Adam
- Μέσος Χρόνος ανά Εποχή: 238 δευτερόλεπτα

ΑΝΑΛΥΤΙΚΟΣ ΟΔΗΓΟΣ FOLDERS

IMAGES FOLDER
Περιέχει τα αποτελέσματα και οπτικοποιήσεις των models:
- LISTA/: Baseline αποτελέσματα single-modality implementation (1 εικόνα)
- 50_test_cases/: Περιπτώσεις ελέγχου για 50 θολωμένες εικόνες εισόδου χαμηλής ανάλυσης.
- graphs/: Γραφικές παραστάσεις εκπαίδευσης (loss, PSNR, learning rate)
- test_results/: Αποτελέσματα αξιολόγησης και metrics

IMPLEMENTATION FOLDER
Ο κύριος κώδικας υλοποίησης:
- LISTA.ipynb: Baseline single-modality implementation (ΠΡΩΤΟ ΒΗΜΑ)
- Original_and_CoEvolving_LeSITA_basics.ipynb: Σύγκριση και ανάλυση
- Original_LeSITA.ipynb: Υλοποίηση του αρχικού LeSITA algorithm
- CoEvolving_LeSITA_scalable_logs.ipynb: CoEvolving έκδοση με logging

DATASET

MS-MRI DATASET (Multiple Sclerosis MRI)
- Εκπαίδευση: 21,920 δείγματα (685 batches x 32)
- Αξιολόγηση: 230 δείγματα (29 batches x 8)
- Διαστάσεις: 128x128 → 512x512 (4x super-resolution)
- Τύποι Εικόνων: T1W, T2W, FLAIR

ΔΟΜΗ ΔΕΔΟΜΕΝΩΝ:
T1W/TARGET - High-res T1 (side information)
T2W/LRINPUT - Low-res T2 (input)
T2W/TARGET - High-res T2 (ground truth)

ΤΕΧΝΙΚΕΣ ΛΕΠΤΟΜΕΡΕΙΕΣ

PREPROCESSING PIPELINE:
1. Κανονικοποίηση: [0,1] (διαίρεση με 255)
2. Data Augmentation: 
   - Rotations: 0°, 90°, 180°, 270°
   - Horizontal/Vertical flips
   - Synchronized augmentation που εφαρμόζεται και στους δύο τύπους εικόνων
3. Batching: Αποδοτική επεξεργασία GPU

DEEP UNFOLDING APPROACH:
- ACSC Module: Aproximate Convolutional Sparse Coding για guidance
- LMCSC Module: Learned Multimodal CSC με LeSITA operator
- Reconstruction Module: Τελική ανασύνθεση εικόνας

ΕΞΕΛΙΞΗ ΜΕΘΟΔΩΝ:
1. LISTA: Baseline single-modality (μόνο ACSC)
2. LeSITA: Multimodal με sequential processing (ACSC + LMCSC)
3. CoEvolving: Advanced multimodal με parallel processing

ΑΝΑΦΟΡΕΣ

ΔΙΠΛΩΜΑΤΙΚΗ ΕΡΓΑΣΙΑ:
"Υπερανάλυση Εικόνας Με Χρήση Βαθιών Νευρωνικών Δικτύων"
Σπηλιόπουλος Σπήλιος, 2025

ΚΥΡΙΕΣ ΑΝΑΦΟΡΕΣ:
- Marivani et al., "Learned multimodal convolutional sparse coding for guided image super-resolution," ICIP 2019
- Tsiligianni & Deligiannis, "Deep coupled-representation learning for sparse linear inverse problems with side information," IEEE SPL 2019

ΕΠΙΚΟΙΝΩΝΙΑ

ΣΥΓΓΡΑΦΕΑΣ: Σπηλιόπουλος Σπήλιος  (sphliossp@gmail.com)
ΕΠΙΒΛΕΠΩΝ: Παύλος-Λυσίμαχος Κόντης  
ΣΥΝΕΙΣΦΟΡΕΣ: Ευαγγελία Τσιλιγιάννη
ΙΔΡΥΜΑ: Πανεπιστήμιο Ιωαννίνων - Τμήμα Μηχ. Η/Υ & Πληροφορικής

ΑΔΕΙΑ ΧΡΗΣΗΣ

Αυτό το έργο υλοποιήθηκε στο πλαίσιο διπλωματικής εργασίας. Για χρήση και διανομή, παρακαλώ επικοινωνήστε με τους συγγραφείς.

KEYWORDS: Image Super-Resolution, Multimodal Medical Imaging, Sparse Representations, Deep Unfolding, Convolutional Sparse Coding, MRI, Interpretable AI