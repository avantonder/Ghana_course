---
title: "Assembly and Annotation"
---

**Teaching: -- min** || **Exercises: -- min**

## Overview

:::::{.callout}

:::{.callout-important icon=false}
### Questions:
- What is *de novo* genome assembly?
- How do I assemble my genome?
- How do I assess the quality of my genome?
- What is genome annotation?
- How do I annotate my genome?
:::

:::{.callout-important icon=false}
### Learning Objectives:
- Understand what *de novo* genome assembly is and how it differs from reference-based assembly.
- Assemble sequence data with `shovill`
- Generate metrics for your assembly with `quast`.
- Annotate your genome with `bakta`
:::

:::{.callout-tip}
### Keypoints:
- List keypoints here
:::
:::::

## *de novo* genome assembly

There are two approaches for genome assembly: reference-based (or comparative)  or *de novo*.  In a reference-based assembly, we use a reference genome as a guide to map our sequence data to and thus reassemble our sequence this way.  Alternatively, we can create a 'new' (*de novo*) assembly that does not rely on a map or reference and more closely reflects the actual genome structure of the isolate that was sequenced.
![Genome assembly](../fig/genome-assembly.jpeg)

Short read/long read

## Genome assemblers

Several tools are available for *de novo* genome assembly depending on whether you're trying to assemble short-read sequence data, long reads or else a combination of both.  Two of the most commonly used assemblers for short-read Illumina data are `Velvet` and `SPAdes`.  SPAdes has become the *de facto* standard de novo genome assembler for Illumina whole genome sequencing data of bacteria and is a major improvement over previous assemblers like Velvet. However, some of its components can be slow and it traditionally did not handle overlapping paired-end reads well.  `Shovill` is a pipeline which uses `SPAdes` at its core, but alters the steps before and after the primary assembly step to get similar results in less time. Shovill also supports other assemblers like `SKESA`, `Velvet` and `Megahit`.  The basic command for running `Shovill` is as follows:

```bash
shovill --outdir <OUTDIR> --R1 <FWD FASTQ> --R2 <REV FASTQ>
```

The meaning of the options used is:

- `outdir` is the directory to write the output files to.
- `--R1` and `--R2` the forward and reverse sequence files for your sample.

The following files will be created:

- `contigs.fa`	The final assembly you should use
- `shovill.log`	Full log file for bug reporting
- `shovill.corrections`	List of post-assembly corrections
- `contigs.gfa`	Assembly graph
- `spades.fasta`	Raw assembled contigs

:::::{.callout-important icon=false}
### ***Exercise:*** Run shovill

:::{.callout collapse="true"}
### ***Solution:***

:::
:::::

## Assembly QC

Before we do any further analyses with our assemblies, we need to assess the quality.  To do this we use a tool called `QUAST` which generates a number of useful metrics for assemblies.  The basic command for running `QUAST` is as follows:

```bash
quast.py --output-dir <OUTDIR> <ASSEMBLY>  
```
The meaning of the option used is:

- `--output-dir` is the directory to write the output files to.

The following files will be created:

- `report.txt` assessment summary in plain text format
- `report.tsv` tab-separated version of the summary, suitable for spreadsheets (Google Docs, Excel, etc)
- `report.tex` LaTeX version of the summary
- `icarus.html` Icarus main menu with links to interactive viewers 
- `report.pdf` all other plots combined with all tables (file is created if - matplotlib python library is installed),
- `report.html` HTML version of the report with interactive plots inside
- `transposed_report.txt` transposed assessment summary in plain text format
- `transposed_report.tsv` transposed tab-separated version of the summary
- `transposed_report.tex` transposed LaTeX version of the summary

:::::{.callout-important icon=false}
### ***Exercise:*** Run quast on your shovill assembly

:::{.callout collapse="true"}
### ***Solution:***

:::
:::::

## Annotation with bakta

:::::{.callout-important icon=false}
### ***Exercise:*** Run bakta to annotate your assembly

:::{.callout collapse="true"}
### ***Solution:***

:::
:::::

## Credit
Information on this page has been adapted and modified from the following source(s):
https://github.com/Joseph7e/MDIBL-T3-WGS-Tutorial#genome-assembly