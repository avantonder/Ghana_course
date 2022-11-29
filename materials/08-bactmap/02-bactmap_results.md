---
title: "nf-core/bactmap Results"
---

**Teaching: -- min** || **Exercises: -- min**

## Overview

:::::{.callout}

:::{.callout-important icon=false}
### Questions:
- List Question here
:::

:::{.callout-important icon=false}
### Learning Objectives:
- List learning objectives here
:::

:::{.callout-tip}
### Keypoints:
- List keypoints here
:::
:::::

We can look at the output directory (`results/bactmap`) to see the various directories containing output files created by `nf-core/bactmap`:

- `bwa/index` contains the index of the reference sequence
- `fastp` contains the results of the trimming and adapter removal performed by `fastp`
- `fastqc` contains QC metrics for the fastq files generated with `fastQC`
- `multiqc` contains a html file containing summaries of the various outputs
- `pipeline_info` contains information about the pipeline run
- `pseudogenomes` contains consensus fasta files for each sample which have the sample variants compared to the reference included.  The alignment we'll use for the next step can also be found in this directory (`aligned_pseudogenomes.fas`)
- `rasusa` contains the subsampled post-trimmed fastq files
- `samtools` contains the sorted bam files and indices created by `bwa` and `samtools` as part of the mapping process
- `snpsites` contains a variant alignment file created from `aligned_pseudogenomes.fas` that can be used as input for tree inference tools
- `variants` contains filtered `vcf` files which contain the variants for each sample













## Credit
Information on this page has been adapted and modified from the following source(s):
