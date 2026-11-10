# ATCC Genome Portal (AGP) November 2026 RNA-seq Data Correction Release Notes

**Release Date:** 10NOV2026  
**Release Type:** Corrective (data correction)  
**Release Version:** 1.1  
**Data Affected:** [FPKM and TPM values corrected for 707 human and 54 mouse](../AGP-assets/2026-Q4/2026-Nov-RNA-seq-Data-Correction-CHANGELOG.xlsx)  
**New Datasets:** None

## 1. Overview

This is a corrective release, all read count files have been replaced. It corrects the normalized expression values in the RNA-seq merged count files for existing cell biology pages and fixes the catalog assignment of two sets of samples.

---

## 2. Release Highlights

- **FPKM and TPM values corrected** for **745** cell biology catalog numbers (692 human, 53 mouse), raw counts did not change.
- **2 sets of samples moved to the correct catalog numbers**: 5 replicates of CCL-120.1 and 4 replicates of CRL-11268G-1.
- **No new datasets** are included in this release.

---

## 3. Impact and Required Actions

- **Please re-download** any merged count file you obtained before this release if you use the FPKM or TPM values.

---

## 4. Data Corrections: Cell Biology

### 4.1 Corrected FPKM and TPM Values

Each merged count file reports, for every gene, raw counts plus FPKM and TPM normalized values. In the previously released files, the gene lengths used to calculate FPKM and TPM were applied to the wrong genes. As a result, **FPKM and TPM values were incorrect for the genes in every merged count file**. All files were recalculated using the correct length for each gene.

- **Raw counts are unchanged.** Only the FPKM and TPM columns changed.

### 4.2 Catalog Number Corrections

Two groups of samples had been released under the catalog number of a related cell line. They are now listed under the correct catalog number, with the correct cell line name, and their merged count files were renamed to match.

| Samples | Previously listed as | Now listed as |
|--------|--------|--------|
| CCL-120.1 (BR1 to BR5) | CCL-120 (CCRF-SB) | CCL-120.1 (CCRF-HSB-2) |
| CRL-11268G-1 (BR1 to BR4) | CRL-11268 (293T/17) | CRL-11268G-1 (OAT1 HEK 293T/17) |

The genuine CCL-120 and CRL-11268 samples are unchanged.

---

## 5. Bioinformatics Pipeline Updates

The AGP counts pipeline now assigns gene lengths by gene ID, labels replicates sequenced in more than one run by run date and applies the catalog corrections above whenever new samples are processed.

- **Mouse gene lengths** are now calculated as the total length of the non-overlapping exon regions of each gene. Human gene lengths are calculated from the RefSeq annotation (GRCh38.p14), as before.

---

## 6. Validation and Quality Control

- The corrected values were checked against an independent recalculation from the RefSeq annotations (GRCh38.p14 for human, GRCm39 for mouse). In every file the FPKM and TPM values match, apart from the one gene noted in Section 7 (Known Issues), and the TPM values sum to 1,000,000 in every sample.

---

## 7. Known Issues

- **PEG10 gene length:** in the human files, the length used for PEG10 is 45 bp (0.68%) shorter than its annotated length because of how the annotation represents this gene's transcripts, so its FPKM and TPM values are about 0.68% higher than a calculation from the full annotation would give. This will be corrected in a future release.

---

## 8. Support and Resources

For questions about this release or the ATCC Genome Portal:

### Resources

- [ATCC Genome Portal](https://genomes.atcc.org/)
- [About the ATCC Genome Portal](https://www.atcc.org/applications/reference-quality-data/discover-the-atcc-genome-portal)
- The Data Use Agreement, which covers the use of all data available from the AGP, can be found online here: [Data Use Agreement | ATCC](https://www.atcc.org/policies/product-use-policies/data-use-agreement)

### Contact

- nextgen@atcc.org
