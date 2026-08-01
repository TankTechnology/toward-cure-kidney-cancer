# Toward Cure Kidney Cancer

> **Bit by bit, toward recovery. Step by step, toward lasting survival. Until the day we conquer kidney cancer.**
>
> 涓滴之力，助患者康复；跬步之积，致长久生存；同心同行，必战胜肾癌。

A curated list of authoritative datasets, computational resources, and top-conference papers on **kidney cancer (renal cell carcinoma, RCC)** — from a computer science perspective. Our goal: accelerate computational research that helps defeat kidney cancer.

Kidney cancer accounts for ~2% of global cancer diagnoses; clear cell RCC (ccRCC) is the most common and lethal subtype. Computation — medical imaging, computational pathology, and multi-omics — is becoming a decisive weapon against it. This repo collects the resources you need to join that fight.

**Contents**

- [Datasets](#datasets)
  - [Segmentation Challenges (CT)](#segmentation-challenges-ct)
  - [Genomics & Multi-omics](#genomics--multi-omics)
  - [Imaging Collections (TCIA)](#imaging-collections-tcia)
  - [Multi-modal Datasets](#multi-modal-datasets)
  - [2D Classification Datasets](#2d-classification-datasets)
  - [Histopathology (WSI) Datasets](#histopathology-wsi-datasets)
  - [Single-cell Atlases](#single-cell-atlases)
- [Papers](#papers)
  - [MICCAI](#miccai)
  - [CVPR / ICCV / ECCV / NeurIPS / ICLR](#cvpr--iccv--eccv--neurips--iclr)
  - [ISBI / AAAI](#isbi--aaai)
- [Landmark Journal Papers](#landmark-journal-papers)
  - [Nature family](#nature-family)
  - [Science family](#science-family)
  - [Cell family](#cell-family)
  - [Clinical & Imaging AI journals](#clinical--imaging-ai-journals)
- [Tools & Code](#tools--code)
- [Contributing](#contributing)

---

## Datasets

### Segmentation Challenges (CT)

The KiTS challenge series is the standard benchmark for kidney and kidney tumor segmentation.

| Dataset | Scale | Modality / Annotations | Links |
|---|---|---|---|
| **KiTS19** | 300 contrast-enhanced CTs (210 train / 90 test) | Late arterial phase CT; voxel-level kidney + tumor masks, clinical context, surgical outcomes | [Challenge](https://kits19.grand-challenge.org/) · [Code](https://github.com/neheller/kits19) · [Paper](https://arxiv.org/abs/1904.00445) |
| **KiTS21** | 300 CTs | Corticomedullary-phase CT; adds **renal cyst** label; triple annotations per ROI; external-institution test set | [Challenge](https://kits21.kits-challenge.org/) · [Code](https://github.com/neheller/kits21) · [Paper](https://arxiv.org/abs/2307.01984) |
| **KiTS23** | 599 CTs (489 train / 110 test) | Multi-phase CT; kidney / tumor / cyst masks with multi-reader majority vote | [Challenge](https://kits-challenge.org/kits23/) · [Code](https://github.com/neheller/kits23) |
| **KNIGHT** | CT + clinical (companion to KiTS21) | Preoperative risk-group classification of kidney tumor patients | [Code](https://github.com/neheller/KNIGHT) |
| **KIPA 2022** | 70+ contrast CTs | Kidney parsing: kidney, tumor, renal artery, renal vein | [Challenge](https://kipa22.grand-challenge.org) |
| **AbdomenCT-1K** | 1,112 CTs | Liver/kidney/spleen/pancreas organ masks + kidney tumor subtask (incorporates KiTS) | [Code & Data](https://github.com/JunMa11/AbdomenCT-1K) |

### Genomics & Multi-omics

| Resource | Contents | Links |
|---|---|---|
| **TCGA-KIRC / KIRP / KICH** | The three TCGA kidney projects (~530 clear cell, ~290 papillary, ~66 chromophobe tumors): RNA-seq, miRNA, WXS, methylation, CNV, clinical | [GDC Portal](https://portal.gdc.cancer.gov/) · [UCSC Xena mirror](https://xenabrowser.net/datapages/) |
| **CPTAC ccRCC** | Proteogenomic cohort (110 tumor / 84 normal): ~10k proteins, phosphoproteome + genomics + transcriptome. Landmark paper: Clark et al., *Cell* 2019 | [Proteomic Data Commons (PDC000127)](https://pdc.cancer.gov/pdc/browse/filters/pdc_study_id:PDC000127%7CPDC000128%7CPDC000129%7CPDC000130) · genomic side at GDC project CPTAC-3 |

### Imaging Collections (TCIA)

Radiology collections matched to the genomic cohorts above, hosted on The Cancer Imaging Archive (also available via NCI Imaging Data Commons).

- **TCGA-KIRC** — 267 subjects, CT/MR/CR, linked to clinical & genomics. [Collection](https://www.cancerimagingarchive.net/collection/tcga-kirc/) · [DOI](https://doi.org/10.7937/K9/TCIA.2016.V6PBVTDR)
- **TCGA-KIRP** — papillary RCC imaging. [Collection](https://www.cancerimagingarchive.net/collection/tcga-kirp/)
- **TCGA-KICH** — chromophobe RCC imaging. [Collection](https://www.cancerimagingarchive.net/collection/tcga-kich/)
- **CPTAC-CCRCC** — CT/MR + histopathology from the CPTAC-3 ccRCC cohort, linkable to PDC proteomics. [Collection](https://www.cancerimagingarchive.net/collection/cptac-ccrcc/) · [IDC mirror](https://portal.imaging.datacommons.cancer.gov/collections/cptac_ccrcc/)

### Multi-modal Datasets

- **MMIST-ccRCC** — 618 ccRCC patients with CT + MRI, histopathology (WSI), genomics, and clinical data, with single-/multi-modal benchmarks. [Dataset page](https://multi-modal-ist.github.io/datasets/ccRCC/) · [Paper (MICCAI 2024)](https://arxiv.org/abs/2405.01658)

### 2D Classification Datasets

- **CT KIDNEY DATASET: Normal-Cyst-Tumor-Stone** — 12,446 CT slices (5,077 normal / 3,709 cyst / 2,283 tumor / 1,377 stone), axial + coronal, contrast and non-contrast. Open download on [Kaggle](https://www.kaggle.com/datasets/nazmul0087/ct-kidney-dataset-normal-cyst-tumor-and-stone).
- **KAUH Kidney Tumor Dataset** — 8,400 CT images from 120 patients (tumor vs normal, with benign/malignant labels). Paper: Alzu'bi et al., *J. Healthcare Engineering* 2022, [DOI](https://doi.org/10.1155/2022/3861161). ⚠️ No open download portal; available via the authors.

### Histopathology (WSI) Datasets

- **Dartmouth Kidney Cancer Histology Dataset (DHMC)** — 563 H&E-stained FFPE whole-slide images (484 resection + 79 biopsy slides, scanned at 20x, distributed at 5x), labeled by two pathologists' consensus for predominant RCC subtype: clear cell, papillary, chromophobe, and oncocytoma, with train/val/test splits. Companion paper: Zhu et al., *Scientific Reports* 2021. [Dataset page](https://bmirds.github.io/KidneyCancer/) (access via request form) · companion code: [DeepSlide](https://github.com/BMIRDS/DeepSlide)

### Single-cell Atlases

- **Advanced ccRCC single-cell atlas (SCP1288)** — scRNA-seq of tumor + immune cells from advanced RCC patients on immunotherapy (Bi et al., *Cancer Cell* 2021). [Broad Single Cell Portal](https://singlecell.broadinstitute.org/single_cell/study/SCP1288/)

---

## Papers

### MICCAI

**Challenge reports & datasets (KiTS series)**

- [The state of the art in kidney and kidney tumor segmentation in contrast-enhanced CT imaging: Results of the KiTS19 Challenge](https://arxiv.org/abs/1912.01054) — Heller, Isensee, Maier-Hein et al., *MedIA* 2021. Meta-analysis of 106 teams; the canonical KiTS19 analysis.
- [The KiTS19 Challenge Data: 300 Kidney Tumor Cases with Clinical Context, CT Semantic Segmentations, and Surgical Outcomes](https://arxiv.org/abs/1904.00445) — Heller et al., 2019. The KiTS19 dataset descriptor.
- [The KiTS21 Challenge: Automatic segmentation of kidneys, renal tumors, and renal cysts in corticomedullary-phase CT](https://arxiv.org/abs/2307.01984) — Heller et al., *MedIA* 2023. KiTS21 official report.
- KiTS21 Proceedings (LNCS, Springer 2022) — 21 participant papers. [DOI](https://doi.org/10.1007/978-3-030-98385-7)
- KiTS23 Proceedings (LNCS 14540, Springer 2024) — KiTS23 participant papers. [DOI](https://doi.org/10.1007/978-3-031-54806-2)

**Segmentation methods**

- [An attempt at beating the 3D U-Net](https://arxiv.org/abs/1908.02182) — Isensee & Maier-Hein, 2019. **KiTS19 winner**; residual-encoder 3D U-Net, precursor of nnU-Net.
- [Kidney tumor segmentation using an ensembling multi-stage deep learning approach](https://arxiv.org/abs/1909.00735) — Santini et al., 2019. Top KiTS19 submission; multi-stage 2.5D residual U-Net ensemble.
- A coarse-to-fine framework for the 2021 Kidney and Kidney Tumor Segmentation Challenge — Zhao et al. **KiTS21 winner** (avg. Dice 0.908). In [KiTS21 Proceedings](https://doi.org/10.1007/978-3-030-98385-7), pp. 53–58.
- [Automated 3D Segmentation of Kidneys and Tumors in MICCAI KiTS 2023 Challenge](https://arxiv.org/abs/2310.04110) — Myronenko et al. (NVIDIA). **KiTS23 winner** using MONAI Auto3DSeg.
- [Exploring 3D U-Net Training Configurations and Post-Processing Strategies for MICCAI 2023 KiTS](https://arxiv.org/abs/2312.05528) — Uhm et al. KiTS23 2nd place, nnU-Net-based.

**Computational pathology**

- Instance-Based Vision Transformer for Subtyping of Papillary Renal Cell Carcinoma in Histopathological Image — Gao et al., MICCAI 2021. i-ViT with nucleus-centered instance patches for type-1 vs type-2 pRCC subtyping on 171 WSIs. [DOI](https://doi.org/10.1007/978-3-030-87237-3_29)

### CVPR / ICCV / ECCV / NeurIPS / ICLR

Foundation models and universal segmentation models where kidney tumor is an explicit task or training target.

- [DoDNet: Learning to Segment Multi-Organ and Tumors from Multiple Partially Labeled Datasets](https://openaccess.thecvf.com/content/CVPR2021/html/Zhang_DoDNet_Learning_To_Segment_Multi-Organ_and_Tumors_From_Multiple_Partially_Labeled_CVPR_2021_paper.html) — CVPR 2021. Dynamic on-demand network trained on 8 partially labeled datasets incl. **KiTS**; segments kidney + kidney tumor. [arXiv](https://arxiv.org/abs/2011.10216)
- [CLIP-Driven Universal Model for Organ Segmentation and Tumor Detection](https://arxiv.org/abs/2301.00785) — ICCV 2023. Text-prompted universal CT model: 25 organs + 6 tumor types **including kidney tumor**. [Code](https://github.com/ljwztc/CLIP-Driven-Universal-Model)
- [SegVol: Universal and Interactive Volumetric Medical Image Segmentation](https://arxiv.org/abs/2311.13385) — NeurIPS 2024 (spotlight). 3D foundation segmentation model; training data includes **KiTS23**. [Proceedings](https://papers.nips.cc/paper_files/paper/2024/hash/c7c7cf10082e454b9662a686ce6f1b6f-Abstract-Conference.html)
- [ScribblePrompt: Fast and Flexible Interactive Segmentation for Any Biomedical Image](https://arxiv.org/abs/2312.07381) — ECCV 2024. Interactive scribble/click/box segmentation trained on 65 datasets incl. **KiTS**. [Proceedings](https://www.ecva.net/papers/eccv_2024/papers_ECCV/papers/05664.pdf)
- [VISTA3D: A Unified Segmentation Foundation Model for 3D Medical Imaging](https://arxiv.org/abs/2406.05285) — CVPR 2025. NVIDIA/MONAI 3D CT foundation model (127 automatic classes + interactive + zero-shot), trained on 11,454 CT volumes incl. kidney/kidney-tumor collections. [Proceedings](https://openaccess.thecvf.com/content/CVPR2025/papers/He_VISTA3D_A_Unified_Segmentation_Foundation_Model_For_3D_Medical_Imaging_CVPR_2025_paper.pdf)
- [AMOS: A Large-Scale Abdominal Multi-Organ Benchmark for Versatile Medical Image Segmentation](https://proceedings.neurips.cc/paper_files/paper/2022/hash/ee604e1bedbd069d9fc9328b7b9584be-Paper-Datasets_and_Benchmarks.pdf) — NeurIPS 2022 (Datasets & Benchmarks). 500 CT + 100 MRI, 15 abdominal organs incl. kidneys. [Data](https://zenodo.org/record/7155725)

### ISBI / AAAI

**IEEE ISBI**

- Towards an Interpretable Radiomics Model for Classifying Renal Cell Carcinomas Subtypes: A Radiogenomics Assessment — ISBI 2019. Interpretable radiomics differentiating ccRCC from non-ccRCC, with radiogenomics correlation. [DOI](https://doi.org/10.1109/ISBI.2019.8759592)
- A Triple-Stage Self-Guided Network for Kidney Tumor Segmentation — ISBI 2020. Coarse-to-fine CNN on KiTS19. [DOI](https://doi.org/10.1109/ISBI45749.2020.9098609)
- An Efficient Hybrid Model for Kidney Tumor Segmentation in CT Images — ISBI 2020. Memory-efficient hybrid 2D/3D model. [DOI](https://doi.org/10.1109/ISBI45749.2020.9098325)
- A New Computer-Aided Diagnostic (CAD) System for Precise Identification of Renal Tumors — ISBI 2021. [DOI](https://doi.org/10.1109/ISBI48211.2021.9433865)
- Automated Small Kidney Cancer Detection in Non-Contrast Computed Tomography — ISBI 2024. Detection pipeline for renal cancer in non-contrast CT. [DOI](https://doi.org/10.1109/ISBI56570.2024.10635401)
- Rethinking Intermediate Layers Design in Knowledge Distillation for Kidney and Liver Tumor Segmentation — ISBI 2024. [DOI](https://doi.org/10.1109/ISBI56570.2024.10635141)
- Leveraging Foundation Models for Clinically Instructed Tumor Image Synthesis in Renal Cell Carcinoma — ISBI 2025. Clinically-conditioned RCC image synthesis for augmentation. [DOI](https://doi.org/10.1109/ISBI60581.2025.10980760)
- Comparative Analysis of Unsupervised and Supervised Autoencoders for Nuclei Classification in Clear Cell Renal Cell Carcinoma Images — ISBI 2025. Automated nuclei classification for ISUP/WHO grading. [DOI](https://doi.org/10.1109/ISBI60581.2025.10981207)

**AAAI**

- Unpaired Multi-Domain Stain Transfer for Kidney Histopathological Images — AAAI 2022. Unpaired multi-stain virtual staining (H&E/MAS/PAS/PASM) for kidney pathology. [Paper](https://ojs.aaai.org/index.php/AAAI/article/view/20054)

> Honest note: IJCAI and KDD (2019–2025) have no kidney-cancer-specific papers that we could verify — their "kidney" hits are kidney-exchange optimization. This is a gap, and arguably an opportunity.

---

## Landmark Journal Papers

The high-impact journal literature that computational kidney cancer research is built on — molecular atlases, single-cell maps, and clinical AI. (All entries verified against Crossref / PubMed metadata.)

### Nature family

- [Comprehensive molecular characterization of clear cell renal cell carcinoma](https://doi.org/10.1038/nature12222) — TCGA Research Network, *Nature* 2013. The foundational multi-omics atlas of ccRCC; the reference dataset for nearly all downstream computational RCC work.
- [Pan-Renal Cell Carcinoma classification and survival prediction from histopathology images using deep learning](https://doi.org/10.1038/s41598-019-46718-3) — Tabibu et al., *Scientific Reports* 2019. Early, widely cited CNN study: RCC subtyping + survival prediction directly from TCGA WSIs.
- [nnU-Net: a self-configuring method for deep learning-based biomedical image segmentation](https://doi.org/10.1038/s41592-020-01008-z) — Isensee et al., *Nature Methods* 2021. The de-facto standard segmentation framework; validated on (and winning) KiTS19.
- [Data-efficient and weakly supervised computational pathology on whole-slide images](https://doi.org/10.1038/s41551-020-00682-w) — Lu et al., *Nature Biomedical Engineering* 2021. CLAM: attention-based MIL for gigapixel WSIs, with RCC subtyping (ccRCC/pRCC/chRCC) as a core benchmark.
- [Development and evaluation of a deep neural network for histologic classification of renal cell carcinoma on biopsy and surgical resection slides](https://doi.org/10.1038/s41598-021-86540-4) — Zhu et al., *Scientific Reports* 2021. RCC subtype classification on biopsy + resection slides (the Dartmouth DHMC dataset).
- [A single-cell map of dynamic chromatin landscapes of immune cells in renal cell carcinoma](https://doi.org/10.1038/s43018-022-00391-0) — Kourtis et al., *Nature Cancer* 2022. scATAC-seq atlas of the RCC immune microenvironment, linking chromatin dynamics to immunotherapy response.
- [A multi-classifier system integrated by clinico-histology-genomic analysis for predicting recurrence of papillary renal cell carcinoma](https://doi.org/10.1038/s41467-024-50369-y) — Huang et al., *Nature Communications* 2024. Multimodal (WSI + lncRNA + clinicopathologic) classifier for pRCC recurrence; code publicly released.
- [A multimodal AI model for precision prognosis in clear cell renal cell carcinoma: A multicenter study](https://doi.org/10.1038/s41746-025-02034-x) — Zang et al., *npj Digital Medicine* 2025. Fuses clinical data, contrast-enhanced CT, and WSI features; outperforms Leibovich/UISS and KEYNOTE-564 stratification.
- [Artificial Intelligence Links CT Images to Pathologic Features and Survival Outcomes of Renal Masses](https://doi.org/10.1038/s41467-025-56784-z) — Xiong et al., *Nature Communications* 2025. Multicenter deep-learning system predicting malignancy, WHO/ISUP grade, and survival from preoperative CT.
- [A disease-centric vision-language foundation model for precision oncology in kidney cancer](https://doi.org/10.1038/s41467-026-74175-w) — Tao et al., *Nature Communications* 2026. Kidney-cancer-specific vision-language foundation model for radiologic diagnosis and prognostication.

### Science family

- [Genomic correlates of response to immune checkpoint therapies in clear cell renal cell carcinoma](https://doi.org/10.1126/science.aan5951) — Miao et al., *Science* 2018. Landmark WES study linking PBRM1 loss to checkpoint-blockade response; one of the most reused immunogenomics datasets in the field.
- [Single-cell transcriptomes from human kidneys reveal the cellular identity of renal tumors](https://doi.org/10.1126/science.aat1699) — Young et al., *Science* 2018. First large scRNA-seq atlas of fetal/adult kidney and renal tumors; established the proximal-tubule cell-of-origin of ccRCC.
- [VHL substrate transcription factor ZHX2 as an oncogenic driver in clear cell renal cell carcinoma](https://doi.org/10.1126/science.aap8411) — Zhang et al., *Science* 2018. Integrative genomic screening identifying ZHX2 as a VHL-regulated driver.
- [Aberrant activation of m6A demethylase FTO renders HIF2α-low/− clear cell renal cell carcinoma sensitive to BRD9 inhibitors](https://doi.org/10.1126/scitranslmed.abf6045) — Zhang et al., *Science Translational Medicine* 2021. Epigenomic/m6A profiling revealing a synthetic-lethal therapeutic axis.
- [Accurate detection of benign and malignant renal tumor subtypes with MethylBoostER: An epigenetic marker-driven learning framework](https://doi.org/10.1126/sciadv.abn9828) — Rossi et al., *Science Advances* 2022. ML classifier on DNA-methylation signatures for renal tumor subtyping, with cell-free DNA early-detection application.
- [Intratumoral mycobiome heterogeneity influences the tumor microenvironment and immunotherapy outcomes in renal cell carcinoma](https://doi.org/10.1126/sciadv.adu1727) — Mou et al., *Science Advances* 2025. Multi-cohort computational analysis of fungal communities in RCC and immunotherapy response.
- [Single-cell epigenetic profiling reveals a tumor-intrinsic interferon response program in ccRCC tied to poor prognosis and BAP1 loss](https://doi.org/10.1126/sciadv.adv5457) — Camp et al., *Science Advances* 2026. Single-cell multi-omics linking BAP1 loss to an interferon program in ccRCC.

### Cell family

- [An Immune Atlas of Clear Cell Renal Cell Carcinoma](https://doi.org/10.1016/j.cell.2017.04.016) — Chevrier et al., *Cell* 2017. Landmark high-dimensional CyTOF immune atlas of ccRCC; foundational TME reference.
- [Multilevel Genomics-Based Taxonomy of Renal Cell Carcinoma](https://doi.org/10.1016/j.celrep.2016.02.024) — Chen et al., *Cell Reports* 2016. TCGA integrative multi-platform clustering defining nine RCC subtypes.
- [Timing the Landmark Events in the Evolution of Clear Cell Renal Cell Cancer: TRACERx Renal](https://doi.org/10.1016/j.cell.2018.02.020) — Mitchell et al., *Cell* 2018. Multi-region phylogenetic reconstruction timing ccRCC driver events.
- [Deterministic Evolutionary Trajectories Influence Primary Tumor Growth: TRACERx Renal](https://doi.org/10.1016/j.cell.2018.03.043) — Turajlic et al., *Cell* 2018. Multi-region genomics defining evolutionary subtypes that predict clinical course.
- [The Cancer Genome Atlas Comprehensive Molecular Characterization of Renal Cell Carcinoma](https://doi.org/10.1016/j.celrep.2018.03.075) — Ricketts et al., *Cell Reports* 2018. Pan-RCC TCGA analysis across ccRCC, papillary, and chromophobe.
- [Integrated Proteogenomic Characterization of Clear Cell Renal Cell Carcinoma](https://doi.org/10.1016/j.cell.2019.10.007) — Clark et al., *Cell* 2019. The CPTAC proteogenomic landmark (103 treatment-naive ccRCC); data via PDC/cBioPortal/LinkedOmics.
- [Tumor and Immune Reprogramming during Immunotherapy in Advanced Renal Cell Carcinoma](https://doi.org/10.1016/j.ccell.2021.02.015) — Bi et al., *Cancer Cell* 2021. scRNA-seq of metastatic RCC pre/post immune checkpoint blockade (dataset: SCP1288).
- [Progressive Immune Dysfunction with Advancing Disease Stage in Renal Cell Carcinoma](https://doi.org/10.1016/j.ccell.2021.02.013) — Braun et al., *Cancer Cell* 2021. Large scRNA-seq + TCR atlas of immune dysfunction across RCC stages.
- [Single-Cell Sequencing Links Multiregional Immune Landscapes and Tissue-Resident T Cells in ccRCC to Tumor Topology and Therapy Efficacy](https://doi.org/10.1016/j.ccell.2021.03.007) — Krishna et al., *Cancer Cell* 2021. Multiregional scRNA + TCR sequencing (167k cells) linking immune topology to ICB response.
- [Single-Cell Protein Activity Analysis Identifies Recurrence-Associated Renal Tumor Macrophages](https://doi.org/10.1016/j.cell.2021.04.038) — Obradovic et al., *Cell* 2021. VIPER-based protein activity inference on a ccRCC TME atlas.
- [Mapping Single-Cell Transcriptomes in the Intra-Tumoral and Associated Territories of Kidney Cancer](https://doi.org/10.1016/j.ccell.2022.11.001) — Li et al., *Cancer Cell* 2022. Multiregional single-cell atlas across tumor core, interface, normal tissue, and blood.
- [Histopathologic and Proteogenomic Heterogeneity Reveals Features of Clear Cell Renal Cell Carcinoma Aggressiveness](https://doi.org/10.1016/j.ccell.2022.12.001) — Li et al., *Cancer Cell* 2023. CPTAC follow-up: 305 tumor segments integrating histopathology, proteogenomics, and metabolomics.

### Clinical & Imaging AI journals

- [Clear Cell Renal Cell Carcinoma: Discrimination from Other Renal Cell Carcinoma Subtypes and Oncocytoma at Multiphasic Multidetector CT](https://doi.org/10.1148/radiol.13112617) — Young et al., *Radiology* 2013. The foundational quantitative-imaging paper for non-invasive renal mass characterization.
- [Application of Machine Learning Models to Predict Recurrence After Surgical Resection of Nonmetastatic Renal Cell Carcinoma](https://doi.org/10.1016/j.euo.2022.07.007) — Khene et al., *European Urology Oncology* 2023. Multicenter ML models outperforming standard clinicopathologic scores for post-surgery recurrence.
- [Multimodal Recurrence Scoring System for Prediction of Clear Cell Renal Cell Carcinoma Outcome: A Discovery and Validation Study](https://doi.org/10.1016/S2589-7500(23)00095-X) — Gui et al., *The Lancet Digital Health* 2023. Multimodal (clinical + histopathology) deep-learning recurrence score with external validation.
- [Deep Learning Assessment of Small Renal Masses at Contrast-enhanced Multiphase CT](https://doi.org/10.1148/radiol.232178) — Dai et al., *Radiology* 2024. Deep-learning identification of benign small renal masses, externally tested at five independent hospitals.

> Honest note: we could not verify any RCC-central computational paper in *JAMA Oncology* or *Lancet Oncology* (2019–2025); *Cell Genomics*, *Patterns*, and *Med* likewise have none we could confirm. Another set of gaps — and opportunities.

---

## Tools & Code

**Segmentation frameworks**

- [nnU-Net](https://github.com/MIC-DKFZ/nnUNet) — Self-configuring segmentation framework (*Nature Methods* 2021). An nnU-Net ensemble won KiTS19; it dominates the KiTS lineage.
- [MONAI](https://github.com/Project-MONAI/MONAI) — PyTorch-based medical imaging AI framework (Core / Label / Deploy); its Auto3DSeg won KiTS23.

**Computational pathology (WSI)**

- [CLAM](https://github.com/mahmoodlab/CLAM) — Weakly-supervised attention-based MIL for whole-slide classification (*Nature BME* 2021); includes RCC subtyping (ccRCC/pRCC/chRCC) experiments on TCGA.
- [dlrcc](https://github.com/cilcmc/dlrcc) — Deep learning for RCC: subtype classification + ccRCC survival prediction from 6,340 TCGA WSIs, with demo notebooks.

**Genomics**

- [TCGAbiolinks](https://github.com/BioinformaticsFMRP/TCGAbiolinks) — The standard R/Bioconductor package to query, download, and analyze GDC/TCGA data — the usual entry point for TCGA-KIRC multi-omics.

**Diagnosis & prognosis**

- [Survival_CTplusClinical](https://github.com/mahootiha-maryam/Survival_CTplusClinical) — Multimodal deep learning for personalized RCC prognosis, integrating CT with clinical data (*Cancers* 2023).
- [deep-kidney-cancer](https://github.com/khuhm/deep-kidney-cancer) — Deep learning for end-to-end kidney cancer diagnosis on multi-phase abdominal CT.

---

## Contributing

Contributions welcome — datasets, papers, tools, or corrections. Please open an issue or PR. Guidelines:

1. **Verify before you add**: every entry must have a working link to an official source (arXiv, DOI, conference proceedings, or official repo).
2. Kidney cancer must be a **real component** of the work (task, dataset, or evaluation) — not an incidental mention.
3. Follow the existing format: title — authors, venue + year, one-line description, links.
