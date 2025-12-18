# Breast-cancer-bulk-RNA-seq
## Project Overview

This repository contains an end-to-end bulk RNA-seq differential gene expression analysis comparing normal breast tissue with major breast cancer subtypes (ER+, HER2+, and triple-negative breast cancer). The analysis identifies subtype-specific transcriptional changes and enriched biological pathways using a reproducible, statistically robust pipeline.

### Biological Questions
1. Which genes are differentially expressed between normal breast tissue and breast cancer?
2. Which transcriptional programs distinguish ER+, HER2+, and TNBC subtypes?
3. Which gene sets and pathways are consistently enriched within each subtype?
   
### Dataset
* Data source: NCBI Sequence Read Archive (SRA)
* Data type: Paired-end bulk RNA-seq
* Reference genome: Human hg38
* Experimental groups: Normal breast tissue, ER+, HER2+, TNBC

## Methods Overview
### 1. Data Acquisition & Quality Control
* RNA-seq data downloaded using SRA-tools (Galaxy v3.1.1)
* Quality assessment performed using FastQC (Galaxy v0.12.1)
* Reads assessed for base quality, adapter contamination, and sequence duplication

### 2. Sequence Alignment
* Aligned to hg38 reference genome
* Aligner: STAR (v2.7.11a)
* Default parameters used for paired-end alignment
* Output: coordinate-sorted BAM files

### 3. Gene Expression Quantification
* Read counting performed using featureCounts (Subread v2.0.3)
* Paired-end reads counted as fragments
* Strand specificity: unstranded
* Annotation: built-in hg38 gene annotation

### 4. Differential Gene Expression Analysis
* Statistical analysis conducted in R using DESeq2
* Design matrix included cancer subtype status and batch effect correction.
* Differential expression thresholds:
Adjusted p-value (FDR) < 0.05
|log₂ fold change| ≥ 1
* Downstream visualization and summaries performed in R
(Complete workflow provided in the accompanying RMarkdown file.)

### 5. Gene Set & Pathway Enrichment Analysis
Functional interpretation of differentially expressed genes was performed using the clusterProfiler package in R.
Gene sets analyzed:
* Gene Ontology (Biological Process, Molecular Function, Cellular Component)
* KEGG pathways

#### Input:
Significantly differentially expressed genes (FDR < 0.05, |log₂FC| ≥ 1)

#### Statistical approach:
* Over-representation analysis.
* Gene set enrichment analysis
* Multiple testing correction using Benjamini–Hochberg FDR

#### Visualization:
* Dot plots and ridge plots of enriched terms
* Enrichment maps highlighting functional clusters
* Subtype-specific pathway enrichment comparisons

This analysis enabled identification of biological processes and pathways uniquely enriched in ER+, HER2+, and TNBC subtypes.

### Reproducibility
* All analyses are scripted and reproducible
* Galaxy was used for alignment and quantification
* RMarkdown document the statistical analysis

### Limitations & Future Directions
* Extension to independent validation cohorts
* Multi-omics integration

### Author
Rahmat Aderemi
MSc Zoology (Cell Biology & Genetics)
Research interests: transcriptomics, genomics, bioinformatics
