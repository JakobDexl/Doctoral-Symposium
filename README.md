# Lessons from autoPET

**Benchmarking, Failure Analysis and Clinical Validity of Automated Lesion Segmentation in Whole-Body PET/CT**

*Jakob Dexl* — MICCAI Doctoral Symposium 2026

Department of Radiology, LMU University Hospital, LMU Munich · Munich Center for Machine Learning (MCML)

📄 **[Paper (PDF)](./paper.pdf)**

---

## TL;DR

Deep learning can segment PET/CT lesions on curated data. My thesis asks two questions that curated benchmarks leave open: **does it generalize to clinical variation**, and **does segmentation accuracy predict clinical usefulness?** Using the autoPET challenges as controlled experiments and a downstream NSCLC staging study, I find:

- Current methods remain sensitive to clinically relevant distribution shifts (centers, pediatric populations, PSMA tracer).
- The dominant failure mode is false positives from physiological uptake and anatomy underrepresented in training, not poor lesion detection.
- Patient characteristics explain **61%** of unexplained DSC variance; the choice of algorithm explains **1.3%**.
- Segmentation accuracy is a poor predictor of staging errors: a physician staging solely from automated masks reached the wrong UICC stage in **99 / 306** NSCLC cases, 63 of which flipped treatment intent between curative and palliative.

## Research Questions

1. How well do current lesion segmentation algorithms generalize across clinically relevant distribution shifts, including centers, patient populations, and PET tracers?
2. Which factors fundamentally limit this generalization, and how should they be studied and benchmarked?
3. To what extent does segmentation performance translate into other clinical tasks like staging?

## Overview

|                 | Setting                      | Design                                                       | Key result                                                   |
| --------------- | ---------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **autoPET2**    | Single-source generalization | Train on FDG from one center, test on 5 target domains (center, pathology, pediatric, PSMA) | DSC 0.50 · FPV 87.8 mL · FNV 8.4 mL · sensitivity high, false positives dominate |
| **autoPET3**    | Compositional generalization | Partially crossed center × tracer; withheld combinations at test time; data-centric track | DSC 0.66 · FPV 2.8 mL · FNV 3.2 mL · oversegmentation persists off-diagonal |
| **NSCLC study** | Segmentation for staging     | Top autoPET3 model → physician stages 306 patients from masks alone | 207 / 306 UICC staged correctly · accuracy ≠ utility         |

## Publications

### Core thesis papers

| Paper                                                        | Role          | Venue                               | Link                                               |
| ------------------------------------------------------------ | ------------- | ----------------------------------- | -------------------------------------------------- |
| AutoPET Challenge on Fully Automated Lesion Segmentation in Oncologic PET/CT Imaging, Part 2: Domain Generalization | First author  | *Journal of Nuclear Medicine*, 2025 | [DOI](https://doi.org/10.2967/jnumed.125.270260)   |
| The autoPET3 Challenge: Automated Lesion Segmentation in Whole-Body PET/CT – Multitracer Multicenter Generalization | First author  | Under review, 2026                  | [arXiv](https://doi.org/10.48550/arXiv.2605.05775) |
| Artificial intelligence for TNM staging in NSCLC: A critical appraisal of segmentation utility in [18F]FDG PET/CT | Second author | *Eur J Nucl Med Mol Imaging*, 2026  | [DOI](https://doi.org/10.1007/s00259-025-07677-2)  |

### Datasets and continuation

| Paper                                                        | Role         | Venue                               | Link                                              |
| ------------------------------------------------------------ | ------------ | ----------------------------------- | ------------------------------------------------- |
| A Whole-Body PSMA-PET/CT dataset with manually annotated tumor lesions | Co-author    | *Scientific Data*, 2026             | [DOI](https://doi.org/10.1038/s41597-026-07821-z) |
| From Automation to Collaboration: The autoPET/CT-IV Challenge on Interactive Lesion Segmentation in Whole-Body PET/CT and Longitudinal CT | Co-organizer | 2026                                | [SSRN](https://doi.org/10.2139/ssrn.6841479)      |
| Results from the autoPET challenge on fully automated lesion segmentation in oncologic PET/CT imaging (autoPET I) | —            | *Nature Machine Intelligence*, 2024 | [DOI](https://doi.org/10.1038/s42256-024-00912-9) |

## Challenges

| Edition       | Focus                                            | Venue       | Website                                                      |
| ------------- | ------------------------------------------------ | ----------- | ------------------------------------------------------------ |
| autoPET I     | Proof of concept, whole-body FDG-PET/CT          | MICCAI 2022 | [autopet.grand-challenge.org](https://autopet.grand-challenge.org/Description/) |
| autoPET II    | Domain generalization                            | MICCAI 2023 | [autopet-ii.grand-challenge.org](https://autopet-ii.grand-challenge.org/) |
| autoPET III   | Multitracer multicenter generalization           | MICCAI 2024 | [autopet-iii.grand-challenge.org](https://autopet-iii.grand-challenge.org/) |
| autoPET/CT IV | Interactive lesion segmentation, longitudinal CT | MICCAI 2025 | [autopet-iv.grand-challenge.org](https://autopet-iv.grand-challenge.org/) |
| autoPET V     | Clinician-in-the-loop interactive segmentation   | MICCAI 2026 | [autopet-v.grand-challenge.org](https://autopet-v.grand-challenge.org/) |

Series homepage: [autopet.org](https://www.autopet.org/)

## Citation

```bibtex
@inproceedings{dexl2026lessons,
  title     = {Lessons from autoPET: Benchmarking, Failure Analysis and Clinical Validity
               of Automated Lesion Segmentation in Whole-Body PET/CT},
  author    = {Dexl, Jakob},
  booktitle = {MICCAI Doctoral Symposium},
  year      = {2026}
}
```

## Contact

Jakob Dexl · jakob.dexl@lmu.de
