---
title: "The nf-core/bactmap pipeline"
---

**Teaching: -- min** || **Exercises: -- min**

## Overview

:::::{.callout}

:::{.callout-important icon=false}
### Questions:
- What is nf-core/bactmap?
- How can I produce a multiple sequence alignment of TB sequences?
:::

:::{.callout-important icon=false}
### Learning Objectives:
- Use `nf-core/bactmap` to produce a multiple sequence alignment.
:::

:::{.callout-tip}
### Keypoints:
- To build a phylogenetic tree we need a _multiple sequence alignment_ of the sequences we want to infer a tree from. 
- Alignments are usually done against a reference genome.
- We can use the pipeline `nf-core/bactmap` to produce a multiple sequence alignment.
:::
:::::

## TB dataset

We will be analysing a dataset of 83 TB genomes previously analysed by Prince as part of his PhD.

::: {.callout-note}
#### Data for this section

We will work from the course files folder called `08-bactmap`, which contains the following files: 

- `reference/MTB_ANC_unwrapped.fasta` is the reference genome
- `data` is the directory containing the fastq files we're going to map to the reference genome
:::

::: {.callout-note}
#### MTBC ancestral sequence

What is the reference and how was it generated
:::

## Installing nextflow

## Setting up the nextflow config file

## Running nf-core/bactmap to generate an alignment

The first step in building a phylogenetic tree is to generate a multiple sequence alignment.  To do this, we're going to map the sequence data for our 83 TB genomes to a reference, in this case the MTBC inferred ancestral sequence, using the `nf-core/bactmap` pipeline.

First create a directory a directory for the output:

```bash
mkdir -p results/bactmap
```

Now create a `samplesheet.csv` file containing the sample IDs and the location of the files to be mapped:

```bash
python fastq_dir_to_samplesheet.py \
    data \
    samplesheet.csv \
    -r1 _1.fastq.gz \
    -r2 _2.fastq.gz
```

The meaning of the options used is:

- `data` is the directory containing the fastq files
- `samplesheet.csv` the name of the input file for `nf-core/bactmap`
- `-r1` and `-r2` the suffixes of the forward and reverse sequence files. By default the `fastq_dir_to_samplesheet.py` script will use everything before this to create the sample IDs

Now run the `nf-core/bactmap` command to generate a reference-based alignment:

```bash
nextflow run nf-core/bactmap \
    -profile singularity \
    --input samplesheet.csv \
    --reference reference/MTB_ANC_unwrapped.fasta \
    --genome_size 4.3mb \
    --outdir results/bactmap
```

`nf-core/bactmap` has a number of optional arguments but for now these are the ones we're going to use:

- `nextflow run` is the software and option we're going to use to run the `nf-core/bactmap` pipeline
- `-profile singularity` tells `nextflow` to pull `singularity` containers for each tool in the pipeline.  We could also use `docker` or `conda`
- `--input samplesheet.csv` tells `nextflow` which samples to analyse and where they're located
- `--reference reference/MTB_ANC_unwrapped.fasta` is the reference sequence we're going to map our samples to
- `--genome_size 4.3mb` is used by the pipeline to calculate the approximate genome coverage in the fastq files. By default the pipeline uses a tool called `rasusa` to subsample the fastq files so the genome coverage is <= 100X
- `--outdir results/bactmap` is the directory we're going to save the outputs from `nf-core/bactmap` to 

Visit the [`nf-core/bactmap`](https://nf-co.re/bactmap) page for further information on running the pipeline with different options.

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
