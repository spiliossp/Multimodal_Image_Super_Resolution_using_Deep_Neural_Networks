README - MULTIMODAL IMAGE SUPER RESOLUTION USING DEEP NEURAL NETWORKS

Documentation Language: (1 - English, 2 - Ελληνικά)

=========================   	English	(1/2)	    =============================

ABSTRACT

This thesis addresses the problem of super-resolution in medical magnetic resonance imaging (MRI) through an innovative approach that combines sparse representation theory with deep unfolding techniques. The Learned Multimodal Convolutional Sparse Coding (LMCSC) system implements a dual-branch architecture that leverages complementary information from different MRI sequences to generate high-resolution images.

KEY ACHIEVEMENTS:
- PSNR: 41.77 dB (improvement of +0.83 dB over state-of-the-art)
- Exceptional convergence speed in just 15-50 training epochs
- Interpretable architecture based on deep unfolding

PROJECT STRUCTURE

Multimodal_Image_Super_Resolution_using_Deep_Neural_Networks/
    README_multimodal_sr_en_gr.md
    Diploma_Thesis/ - Thesis document (PDF)
    Images/ - Image results folder
        Convolutional_ACSC_model/ - Baseline LISTA results
        CoEvolving_LMCSC_model/
        Original_LMCSC_model/
    Implementations/ - Implementation code
        Convolutional_LISTA_ACSC.ipynb
        CoEvolving_LMCSC_scalable_logs.ipynb
        Original_and_CoEvolving_LMCSC_basics.ipynb
        Original_LMCSC.ipynb
        README_implementations_en_gr.md

DETAILED MODEL STRUCTURE

Convolutional_ACSC_model/ - Baseline single-modality implementation

Original_LMCSC_model/
    50_test_cases/
    graphs/
    test_results/

CoEvolving_LMCSC_model/
    graphs/
    test_results/

QUICK START

REQUIREMENTS:
- Python 3.8+
- PyTorch
- CUDA-compatible GPU
- Libraries: Implementations/requirements.txt

INSTALLATION:
1. git clone https://github.com/spiliossp/Multimodal_Image_Super_Resolution_using_Deep_Neural_Networks.git
2. cd Multimodal_Image_Super_Resolution_using_Deep_Neural_Networks
3. pip install -r Implementations/requirements.txt

USAGE:

RECOMMENDED LEARNING SEQUENCE:
1. Baseline LISTA:
   jupyter notebook Implementations/Convolutional_LISTA_ACSC.ipynb

2. Basic Multimodal Concepts:
   jupyter notebook Implementations/Original_and_CoEvolving_LMCSC_basics.ipynb

3. Original LMCSC Training:
   jupyter notebook Implementations/Original_LMCSC.ipynb

4. CoEvolving LMCSC Training:
   jupyter notebook Implementations/CoEvolving_LMCSC_scalable_logs.ipynb

ARCHITECTURE

BASELINE LISTA MODEL
Single-Modality Approach - Processes only the input image without side information.

FEATURES:
- ACSC module only (Approximate Convolutional Sparse Coding)
- No side information
- Fundamental implementation for understanding the architecture
- Essential first learning step

LeSITA LMCSC MODEL
Sequential Approach - Side information (T1W) is processed first and then guides the super-resolution of the input image (T2W).

FEATURES:
- 3 unfolding stages
- 85 filters per layer
- 7x7 convolutional kernels
- Parameters: γ = 0.1 (sparsity), μ = 0.1 (coupling)

CoEvolving LeSITA LMCSC MODEL
Co-evolving Approach - Both sparse representations of the images evolve in parallel with dynamic interaction.

IMPROVEMENTS:
- Co-evolving architecture
- Enhanced texture preservation
- Dynamic interaction between U,Z representations

RESULTS

QUANTITATIVE RESULTS:
LISTA Baseline: ~40.65 dB PSNR, Single modality, Basic implementation
LeSITA LMCSC: 41.77 dB PSNR, 3 Stages, Sequential processing
CoEvolving LMCSC: 41.36 dB PSNR, 2 Stages, Co-evolving architecture

COMPARISON WITH STATE-OF-THE-ART:
BICUBIC: 28.5 dB
SRCNN: 32.1 dB
VDSR: 34.2 dB
EDSR: 36.8 dB
Our LISTA (Baseline): ~40.65 dB
Our LMCSC: 41.77 dB

TRAINING METRICS:
- Training Epochs: 15-50
- Batch Size: 32 (training), 8 (evaluation)
- Learning Rate: 1e-4
- Optimizer: Adam
- Average Time per Epoch: 238 seconds

DETAILED FOLDER GUIDE

IMAGES FOLDER
Contains results and visualizations from the models:
- LISTA/: Baseline single-modality implementation results (1 image)
- 50_test_cases/: Test cases for 50 blurred low-resolution input images
- graphs/: Training plots (loss, PSNR, learning rate)
- test_results/: Evaluation results and metrics

IMPLEMENTATIONS FOLDER
Main implementation code:
- Convolutional_LISTA_ACSC.ipynb: Baseline single-modality implementation (FIRST STEP)
- Original_and_CoEvolving_LMCSC_basics.ipynb: Comparison and analysis
- Original_LMCSC.ipynb: Original LMCSC algorithm implementation
- CoEvolving_LMCSC_scalable_logs.ipynb: CoEvolving version with logging

DATASET

MS-MRI DATASET (Multiple Sclerosis MRI)
- Training: 21,920 samples (685 batches x 32)
- Evaluation: 230 samples (29 batches x 8)
- Dimensions: 128x128 → 512x512 (4x super-resolution)
- Image Types: T1W, T2W, FLAIR

DATA STRUCTURE:
T1W/TARGET - High-res T1 (side information)
T2W/LRINPUT - Low-res T2 (input)
T2W/TARGET - High-res T2 (ground truth)

TECHNICAL DETAILS

PREPROCESSING PIPELINE:
1. Normalization: [0,1] (division by 255)
2. Data Enrichment:
   - Rotations: 0°, 90°, 180°, 270°
   - Horizontal/Vertical flips
   - Synchronized augmentation applied to both image types
3. Batching: Efficient GPU processing

DEEP UNFOLDING APPROACH:
- ACSC Module: Approximate Convolutional Sparse Coding for guidance
- LMCSC Module: Learned Multimodal CSC with LeSITA operator
- Reconstruction Module: Final image synthesis

METHOD EVOLUTION:
1. LISTA: Baseline single-modality (ACSC only)
2. LeSITA: Multimodal with sequential processing (ACSC + LMCSC)
3. CoEvolving: Advanced multimodal with parallel processing

REFERENCES

THESIS:
"Image Super-Resolution Using Deep Neural Networks"
Spilios Spiliopoulos, 2025

KEY REFERENCES:
- Marivani et al., "Learned multimodal convolutional sparse coding for guided image super-resolution," ICIP 2019
- Tsiligianni & Deligiannis, "Deep coupled-representation learning for sparse linear inverse problems with side information," IEEE SPL 2019

CONTACT

AUTHOR: Spilios Spiliopoulos (sphliossp@gmail.com)
SUPERVISOR: Pavlos-Lysimachos Kontis
CONTRIBUTIONS: Evaggelia Tsiligianni
INSTITUTION: University of Ioannina - Department of Computer Science & Engineering

LICENSE

This work was implemented as part of a diploma thesis. For use and distribution, please contact the authors.

KEYWORDS: Image Super-Resolution, Multimodal Medical Imaging, Sparse Representations, Deep Unfolding, Convolutional Sparse Coding, MRI, Interpretable AI, Artificial Intelligence, Deep Neural Networks, Convolutional Neural Networks, Machine Learning, Optimization, Fine-tuning, Automated System, Data Enrichment, Data Visualization.

=========================   	Ελληνικά	(2/2)	    =============================

ΠΕΡΙΛΗΨΗ

Αυτή η διπλωματική εργασία αντιμετωπίζει το πρόβλημα της υπερανάλυσης ιατρικών εικόνων μαγνητικής τομογραφίας (MRI) μέσω μιας καινοτόμου προσέγγισης που συνδυάζει τη θεωρία των αραιών αναπαραστάσεων με τεχνικές βαθιάς αναδίπλωσης. Το σύστημα Learned Multimodal Convolutional Sparse Coding (LMCSC) υλοποιεί μια διπλού-κλάδου αρχιτεκτονική που αξιοποιεί τη συμπληρωματική πληροφορία από διαφορετικές MRI sequences για την παραγωγή εικόνων υψηλής ανάλυσης.

ΚΥΡΙΑ ΕΠΙΤΕΥΓΜΑΤΑ:
- PSNR: 41.77 dB (βελτίωση +0.83 dB από state-of-the-art)
- Εξαιρετική ταχύτητα σύγκλισης σε μόλις 15-50 εποχές εκπαίδευσης
- Ερμηνεύσιμη αρχιτεκτονική βασισμένη σε deep unfolding

ΔΟΜΗ PROJECT

Multimodal_Image_Super_Resolution_using_Deep_Neural_Networks/
    README_multimodal_sr_en_gr.md
    Diploma_Thesis/ - Διπλωματική εργασία (PDF)
    Images/ - Φάκελος εικόνων
        Convolutional_ACSC_model/ - Αποτελέσματα Baseline LISTA
        CoEvolving_LMCSC_model/
        Original_LMCSC_model/
    Implementations/ - Κώδικας υλοποίησης
        Other/ - Βοηθητικά αρχεία
        Convolutional_LISTA_ACSC.ipynb
        CoEvolving_LMCSC_scalable_logs.ipynb
        Original_and_CoEvolving_LMCSC_basics.ipynb
        Original_LMCSC.ipynb
        README_implementations_en_gr.md

ΑΝΑΛΥΤΙΚΗ ΔΟΜΗ

Convolutional_ACSC/ - Baseline single-modality implementation

Original_LMCSC_model/
    50_test_cases/
    graphs/
    test_results/

CoEvolving_LMCSC_model/
    graphs/
    test_results/

ΓΡΗΓΟΡΗ ΕΚΚΙΝΗΣΗ

ΑΠΑΙΤΗΣΕΙΣ:
- Python 3.8+
- PyTorch
- CUDA-compatible GPU
- Libraries: Implementations/requirements.txt 

ΕΓΚΑΤΑΣΤΑΣΗ:
1. git clone https://github.com/spiliossp/Multimodal_Image_Super_Resolution_using_Deep_Neural_Networks.git
2. cd Multimodal_Image_Super_Resolution_using_Deep_Neural_Networks
3. pip install -r Implementations/requirements.txt

ΧΡΗΣΗ:

ΣΕΙΡΑ ΕΚΜΑΘΗΣΗΣ (Προτεινόμενη):
1. Baseline LISTA:
   jupyter notebook Implementations/Convolutional_LISTA_ACSC.ipynb

2. Βασικές Έννοιες Multimodal:
   jupyter notebook Implementations/Original_and_CoEvolving_LMCSC_basics.ipynb

3. Εκπαίδευση Original LMCSC:
   jupyter notebook Implementations/Original_LMCSC.ipynb

4. Εκπαίδευση CoEvolving LMCSC:
   jupyter notebook Implementations/CoEvolving_LMCSC_scalable_logs.ipynb

ΑΡΧΙΤΕΚΤΟΝΙΚΗ

BASELINE LISTA MODEL
Single-Modality Approach - Επεξεργάζεται μόνο την εικόνα εισόδου χωρίς βοηθητική πληροφορία.

ΧΑΡΑΚΤΗΡΙΣΤΙΚΑ:
- Μόνο ACSC module (Approximate Convolutional Sparse Coding)
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
LISTA Baseline: ~40.65 dB PSNR, Single modality, Basic implementation
LeSITA LMCSC: 41.77 dB PSNR, 3 Στάδια, Sequential processing
CoEvolving LMCSC: 41.36 dB PSNR, 2 Στάδια, Co-evolving architecture

ΣΥΓΚΡΙΣΗ ΜΕ STATE-OF-THE-ART:
BICUBIC: 28.5 dB
SRCNN: 32.1 dB
VDSR: 34.2 dB
EDSR: 36.8 dB
Our LISTA (Baseline): ~40.65 dB
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
- 50_test_cases/: Περιπτώσεις ελέγχου για 50 θολωμένες εικόνες εισόδου χαμηλής ανάλυσης
- graphs/: Γραφικές παραστάσεις εκπαίδευσης (loss, PSNR, learning rate)
- test_results/: Αποτελέσματα αξιολόγησης και metrics

IMPLEMENTATIONS FOLDER
Ο κύριος κώδικας υλοποίησης:
- Convolutional_LISTA_ACSC.ipynb: Baseline single-modality implementation (ΠΡΩΤΟ ΒΗΜΑ)
- Original_and_CoEvolving_LMCSC_basics.ipynb: Σύγκριση και ανάλυση
- Original_LMCSC.ipynb: Υλοποίηση του αρχικού LMCSC algorithm
- CoEvolving_LMCSC_scalable_logs.ipynb: CoEvolving έκδοση με logging

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
2. Εμπλουτισμός Δεδομένων: 
   - Rotations: 0°, 90°, 180°, 270°
   - Horizontal/Vertical flips
   - Synchronized augmentation που εφαρμόζεται και στους δύο τύπους εικόνων
3. Batching: Αποδοτική επεξεργασία GPU

DEEP UNFOLDING APPROACH:
- ACSC Module: Approximate Convolutional Sparse Coding για guidance
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

ΣΥΓΓΡΑΦΕΑΣ: Σπηλιόπουλος Σπήλιος (sphliossp@gmail.com)
ΕΠΙΒΛΕΠΩΝ: Παύλος-Λυσίμαχος Κόντης  
ΣΥΝΕΙΣΦΟΡΕΣ: Ευαγγελία Τσιλιγιάννη
ΙΔΡΥΜΑ: Πανεπιστήμιο Ιωαννίνων - Τμήμα Μηχ. Η/Υ & Πληροφορικής

ΑΔΕΙΑ ΧΡΗΣΗΣ

Αυτό το έργο υλοποιήθηκε στο πλαίσιο διπλωματικής εργασίας. Για χρήση και διανομή, παρακαλώ επικοινωνήστε με τους συγγραφείς.

ΛΕΞΕΙΣ ΚΛΕΙΔΙΑ: Υπερανάλυση Εικόνας, Πολυτροπική Ιατρική Απεικόνιση, Αραιές Αναπαραστάσεις, Βαθιά Αναδίπλωση, Συνελικτική Αραιή Κωδικοποίηση, Μαγνητική Τομογραφία, Ερμηνεύσιμη Τεχνητή Νοημοσύνη, Τεχνητή Νοημοσύνη, Βαθιά Νευρωνικά Δίκτυα, Συνελικτικά Νευρωνικά Δίκτυα, Μηχανική Μάθηση, Βελτιστοποίηση, Λεπτοστόχαστη Ρύθμιση, Αυτοματοποιημένο Σύστημα, Εμπλουτισμός Δεδομένων, Οπτικοποίηση Δεδομένων