# Breast-cancer-bulk-RNA-seq
Comparing gene expression counts between normal breast tissue and breast cancer subtypes (ER+, ER/PR, HER2+ and TNBC). 
Breast cancer is the most commonly diagnosed cancer among Nigerian women. It is estimated that 1 in 8 women worldwide will be diagnosed with breast cancer during their lifetime, and Nigeria is no exception, with the disease accounting for around 30-40% of cancers in women. The aim of this study is to see which genes are upregulated and downregulated between the normal breast cells and breast cancer cells.

## Data acquisition and quality control-
Bulk RNA-seq data was sourced from NCBI SRA and were downloaded on to Galaxy platform (usegalaxy.org) (sra-tool Version 3.1.1+galaxy1). FastQC on galaxy (Version 0.12.1) was run on the generated pair end reads to check for presence of adapter sequences and if the reads were of good quality.  

## Sequence alignment-
Paired end reads with satisfactory quality were aligned to the human reference genome hg38 with the STAR (Version 2.7.11a) mapper on Galaxy using the default parameters on galaxy.

## Gene expression counts-
The expression counts for the resulting BAM were quantified using featureCount (subread version 2.0.3) on Galaxy. The specified strand information was unstranded and the paired end reads were counted as one fragment. The gene annotation file was the featureCount built in for human hg38 genome.

## Differential gene expression analysis-
The differential gene expression analysis was carried out using DESeq2 package on R. Steps are in the RMarkdown document.
