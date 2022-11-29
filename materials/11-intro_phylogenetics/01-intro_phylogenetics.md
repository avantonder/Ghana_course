---
title: "Introduction to Phylogenetics"
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

## Multiple sequence alignment

## Phylogenetic tree inference

## Visualization of phylogenetic trees

There are many programs that can be used to visualise phylogenetic trees.

## Exercise

## Phylogenetic tree inference 

There are a number of different tools for phylogenetic inference via maximum-likelihood and some of the most popular tools used for phylogenetic inference are [`FastTree`](http://www.microbesonline.org/fasttree/), [`IQ-Tree`](http://www.iqtree.org/) and [`RAxML-NG`](https://github.com/amkozlov/raxml-ng). For this practical, we're going to use `IQ-Tree`.

First, create a directory for the `IQ-tree` analysis and copy the alignment created by `nf-core/bactmap` into the new directory:

```bash
mkdir -p results/iqtree

cp results/bactmap/pseudogenomes/aligned_pseudogenomes.fas results/iqtree
```
Phylogenetic inference software such as `IQ-tree` typically takes as input an alignment of just the variant sites in a multiple sequence alignment.  So, before running `IQ-tree`, we need to extract the variant sites from the masked alignment.  To ensure that the branch lengths are correctly scaled, we also need to tell `IQ-tree` how many invariant or constant sites there are in our multiple sequence alignment.  To do both those things, we can use a tool called [`snp-sites`](https://github.com/sanger-pathogens/snp-sites). Run the following commands in the `results/iqtree`directory:

```bash
snp-sites \
    aligned_pseudogenomes.fas \
    -o aligned_pseudogenomes_snps.fas

snp-sites \
    -C aligned_pseudogenomes.fas \
    > constant_sites.txt
```

Now we can run `IQ-tree` using the two files we just created with `snp-sites` as input:

```bash
iqtree \
    -fconst $(cat constant_sites.txt) \
    -s aligned_pseudogenomes_snps.fas \
    -nt auto \
    -ntmax 8 \
    -mem 8G \
    -m GTR \
    -bb 1000
```

The meaning of the options used is:

- `--fconst $(cat constant_sites.txt)` tells `IQ-tree` to extract the number of invariant sites from the file we created using `SNP-sites`
- `-s aligned_pseudogenomes_snps.fas` is the the variant site alignment
- `-nt auto` autodetects the number of available cores
- `-ntmax 8` is the maximal number of cores to use
- `-mem 8G` is the maximal RAM usage in GB
- `-m GTR` tells `IQ-tree` to use the General time reversible model of nucleotide substitution
- `-bb 1000` is the number of ultrafast bootstraps to run

We can look at the output directory (`results/iqtree`) to see the various  output files created by `IQ-tree`:

- `aligned_pseudogenomes_snps.fas.iqtree` is a text file containing a report of the IQ-Tree run, including a representation of the tree in text format.
- `aligned_pseudogenomes_snps.fas.treefile` is the estimated tree in NEWICK format. We can use this file with other programs, such as [`FigTree`](http://tree.bio.ed.ac.uk/software/figtree/), to visualise our tree. 
- `aligned_pseudogenomes_snps.fas.log` is the log file containing the messages that were also printed on the screen. 
- `aligned_pseudogenomes_snps.fas.bionj` is the initial tree estimated by neighbour joining (NEWICK format).
- `aligned_pseudogenomes_snps.fas.mldist` is the maximum likelihood distances between every pair of sequences.
- `aligned_pseudogenomes_snps.fas.ckp.gz` is this is a "checkpoint" file, which IQ-Tree uses to resume a run in case it was interrupted (e.g. if you are estimating very large trees and your job fails half-way through).

## Credit
Information on this page has been adapted and modified from the following source(s):
