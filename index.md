---
title: "Introduction to Bacterial Genomics"
author: "Andries van Tonder, Prince Asare"
date: today
---

:::{.panel-tabset}

# Introduction to Bacterial Genomics

## Overview 

This course will teach you how to begin analysing whole genome sequencing data from bacterial isolates. We will introduce many of the software tools commonly used when analysing bacterial genomes and provide an outline of workflows such as quality control, short read mapping and phylogenetic tree inference. Along the way, you will gain foundational bioinformatic skills, including the use of the Unix command line and learn to write simple scripts to ensure your analysis is reproducible.

::: {.callout-tip}

### Learning Objectives:

By the end of this course, learners should be able to:

- Understand what the main technologies used for high throughput sequencing are.
- Use the Unix command line to navigate a filesystem, manipulate files, launch programs and write scripts for reproducible analysis.
- Recognise the structure of common sequence file formats in bioinformatics and run basic quality control tools on them.
- Use mapping tools to map short read sequence data to a reference genome, call variants and visualize the results of the mapping process.
- Understand how to create a *de novo* assembly, assess the quality of the assembly and annotate the genome using a pre-compiled database of annotations.
- Manage and install bioinformatics software using _Conda_ and set up _Nextflow_ workflows.
- Use Nextflow pipelines from the nf-core community and map sequence data from several isolates to a reference genome with the bactmap pipeline.
- Understand the different approaches to constructing a phylogenetic tree as well build and visualize a phylogeny.
- Run different genotyping tools to predict characteristics such as serotypes and antimicrobial resistance.
- Understand what high performance computing is and how this can be used to analyse large numbers of genomes efficiently and quickly.
:::


### Target Audience

This course is aimed at life scientists interested in the bioinformatic analysis of bacterial genomes.

### Prerequisites

We assume no prior bioinformatics experience or experience with the tools introduced in this course.  An elementary knowledge of molecular and bacterial biology is assumed (concepts such as: DNA, RNA, SNPs).


## Authors

About the authors:

- **Andries van Tonder**
  <a href="https://orcid.org/0000-0002-4380-5250" target="_blank"><i class="fa-brands fa-orcid" style="color:#a6ce39"></i></a> 
  <a href="https://github.com/avantonder" target="_blank"><i class="fa-brands fa-github" style="color:#4078c0"></i></a>  
  _Affiliation_: Department of Veterinary Medicine, University of Cambridge  
  _Roles_: writing - original draft; conceptualisation; coding
- **Prince Asare**
  <a href="https://orcid.org/0000-0003-0673-5967" target="_blank"><i class="fa-brands fa-orcid" style="color:#a6ce39"></i></a>
  <a href="https://github.com/princeasregh" target="_blank"><i class="fa-brands fa-github" style="color:#4078c0"></i></a>  
  _Affiliation_: Noguchi Memorial Institute for Medical Research, University of Ghana  
  _Roles_: writing - original draft; conceptualisation; coding


## Citation

You can cite these materials as:

Asare P and van Tonder A. (2023) "Introduction to bacterial genomics", https://avantonder.github.io/Ghana_course/

Or in BibTeX format:

```
@Misc{,
  author = {Asare, Prince and van Tonder, Andries},
  title = {avantonder.github.io/Ghana_course/: Introduction to bacterial genomics},
  month = {January},
  year = {2023},
  url = {https://avantonder.github.io/Ghana_course/},
}
```


## Acknowledgements

These materials have been developed as a collaboration between the [Department of Veterinary Medicine](https://www.vet.cam.ac.uk/) at the University of Cambridge and the [Noguchi Memorial Institute for Medical Research](https://noguchi.org.gh/) at the University of Ghana.

We also thank the wider community for publicly sharing training resources, including: 

- The excellent training courses put together by University of [Cambridge Bioinformatics Training Facility](https://github.com/cambiotraining/)
- The [Carpentries](https://carpentries.org/) project

:::