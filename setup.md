---
title: "Setup"
---

<!-- 
Note for Training Developers:
We provide instructions for commonly-used software as commented sections below.
Uncomment the sections relevant for your materials, and add additional instructions where needed (e.g. specific packages used).
Note that we use tabsets to provide instructions for all three major operating systems.
-->



::: {.callout-tip}
## Workshop Attendees

If you are attending one of our workshops, we will provide a training environment with all of the required software and data.  
If you want to setup your own computer to run the analysis demonstrated on this course, you can follow the instructions below.
:::

Note that we use tabsets to provide instructions for all three major operating systems. However, as much as possible we advice you use a Linux system, as our training environment is built on that.


## [Installing conda](https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html#regular-installation)

We will perform a fresh installation of the conda package using the `miniconda` installation option.


:::{.callout-note}

If you already have Miniconda or Anaconda installed, and you just want to upgrade, you should not proceed to making a fresh installation. Just use `conda update` to update your existing version of conda.

```bash
conda update conda
```

After updatiing conda, you can proceed to the instructions from number 8 to install mamba into the base environment from the conda-forge channel.

:::


::::: {.panel-tabset group="os"}

### Windows

Follow this [link](https://docs.conda.io/projects/conda/en/latest/user-guide/install/windows.html) to install miniconda and this [link](https://mamba.readthedocs.io/en/latest/installation.html) to install mamba on your windows system.


<!--FIXME: Note: Windows users can use WSL2 (see @wsl).-->


### Mac OS

Open a terminal and follow the following instructions:

1. Navigate to your home directory:

```bash
cd ~
```

2. Download the *Miniconda3* installer for mac by running: 

```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-x86_64.sh
```

:::{.callout-note}
### M processor users

For M1 processor users, you will need to run the below command:

```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-arm64.sh
```

:::

3. Run the installation script just downloaded: 

```bash
bash Miniconda3-latest-MacOSX-x86_64.sh
```

4. Follow the installation instructions accepting default options (answering 'yes' to any questions)
- If you are unsure about any setting, accept the defaults. You can change them later.

5. To make the changes take effect, close and then re-open your terminal window.

6. Test your installation.
- In your terminal window, run the command `conda list`:

```bash
conda list
```
- A list of installed packages appears if it has been installed correctly.

7. Remove the installation script as it is no longer needed if successfully installed:

```bash
rm Miniconda3-latest-MacOSX-x86_64.sh
```

8. Run the following command to add channels:

```bash
conda config --add channels defaults; conda config --add channels bioconda; conda config --add channels conda-forge; conda config --set channel_priority strict
```

This adds two *channels* (sources of software) useful for bioinformatics and data science applications.

9. Install [Mamba](https://anaconda.org/conda-forge/mamba) into the base environment from the conda-forge channel with the below command:

```bash
conda install mamba -n base -c conda-forge
```

10. Run this to initiate mamba:

```bash
mamba init
```

### Linux

Open a terminal and follow the following instructions:

1. Navigate to your home directory:

```bash
cd ~
```

2. Download the *Miniconda3* installer for Linux by running: 

```bash
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
```

3. Run the installation script just downloaded: 

```bash
bash Miniconda3-latest-Linux-x86_64.sh
```

4. Follow the installation instructions accepting default options (answering 'yes' to any questions)
- If you are unsure about any setting, accept the defaults. You can change them later.

5. To make the changes take effect, close and then re-open your terminal window.

6. Test your installation.
- In your terminal window, run the command `conda list`:

```bash
conda list
```
- A list of installed packages appears if it has been installed correctly.

7. Remove the installation script as it is no longer needed if successfully installed:

```bash
rm Miniconda3-latest-Linux-x86_64.sh
```

8. Run the following command to add channels:

```bash
conda config --add channels defaults; conda config --add channels bioconda; conda config --add channels conda-forge; conda config --set channel_priority strict
```

This adds two *channels* (sources of software) useful for bioinformatics and data science applications.

9. Install [Mamba](https://anaconda.org/conda-forge/mamba) into the base environment from the conda-forge channel with the below command:

```bash
conda install mamba -n base -c conda-forge
```

10. Run this to initiate mamba:

```bash
mamba init
```
:::::



## Creating [conda environments](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html) for the workshop

:::::{.panel-tabset group="os"}

### Windows

Content will soon be uploaded.

<!--FIXME: This will be verified and released later


:::{.callout}
### creating the `qc` environment and installing required packages

Open a terminal, make sure you are in the conda base environment and run this command to install all required packages and their dependencies:

```bash
mamba create -n qc fastq-scan=1.0.0 fastqc=0.11.9 fastp=0.23.2 kraken2=2.1.2 bracken=2.7 multiqc=1.13a
```

This creates an environment called `qc` with the specified package versions and their dependencies.


**NB.** The tools `fastq-scan and bracken` runs python scripts which require python libraries pandas, json, glob.  
Use the below command to install the packages in the `qc` environment:

```bash
conda install pandas -n qc -c conda-forge 
```

We will activate and use this environment in [chapter 4](./materials/04-sequence_qc/4.1-sequence_qc.md) --- [Sequencing Quality Control](./materials/04-sequence_qc/4.1-sequence_qc.md).
:::


:::{.callout}
### creating the `mapping` environment and installing required packages

run this command to install all required packages and their dependencies:

```bash
mamba create -n mapping bwa=0.7.17 samtools=1.15 bcftools=1.14 pysam=0.16.0.1 biopython=1.78
```

This creates an environment called `mapping` with the specified package versions and their dependencies.

We will activate and use this environment in [chapter 5](./materials/05-short_read_mapping/5.1-short_read_mapping.md) --- [Short Read Mapping](./materials/05-short_read_mapping/5.1-short_read_mapping.md).
:::


:::{.callout}
### creating the `genotyping` environment and installing required packages

run this command to install all required packages and their dependencies:

```bash
mamba create -n genotyping mlst=2.22.1 seroba=1.0.2 spotyping=2.1-3 tb-profiler=4.1.1 ariba=2.14.6
```

This creates an environment called `genotyping` with the specified package versions and their dependencies.

We will activate and use this environment in [chapter 11](./materials/11-genotyping/11.1-genotyping.md) --- [Bacterial Genotyping and Drug Resistance Prediction](./materials/11-genotyping/11.1-genotyping.md).
:::

:::{.callout-note}
### Specify version of toool to install

As you may see, all the tools installed have specified version numbers added to the tool names in the format `tool=version_numer`. This allows us to install the exact version of tools used for the training.

For your personal use, if you wish to use the latest version of these tools, just omit specifying the version z-version_number` and the latest version of the tool will hopefully be installed.
:::
-->


### Mac OS

:::{.callout}
### creating the `qc` environment and installing required packages

Open a terminal, make sure you are in the conda base environment and run this command to install all required packages and their dependencies:

```bash
mamba create -n qc fastq-scan=1.0.0 fastqc=0.11.9 fastp=0.23.2 kraken2=2.1.2 bracken=2.7 multiqc=1.13a
```

This creates an environment called `qc` with the specified package versions and their dependencies.


**NB.** The tools `fastq-scan and bracken` runs python scripts which require python libraries pandas, json, glob.  
Use the below command to install the packages in the `qc` environment:

```bash
conda install pandas=1.4.3 -n qc -c conda-forge 
```

We will activate and use this environment in [chapter 4](./materials/04-sequence_qc/4.1-sequence_qc.md) --- [Sequencing Quality Control](./materials/04-sequence_qc/4.1-sequence_qc.md).
:::


:::{.callout}
### creating the `mapping` environment and installing required packages

run this command to install all required packages and their dependencies:

```bash
mamba create -n mapping bwa=0.7.17 samtools=1.15 bcftools=1.14 pysam=0.16.0.1 biopython=1.78
```

This creates an environment called `mapping` with the specified package versions and their dependencies.

We will activate and use this environment in [chapter 5](./materials/05-short_read_mapping/5.1-short_read_mapping.md) --- [Short Read Mapping](./materials/05-short_read_mapping/5.1-short_read_mapping.md).
:::


:::{.callout}
### creating the `genotyping` environments and installing required packages

**NB.** For the genotyping and AMR prediction, we will create five different environments because some tools require specific versions of python and other related packages hence we cannot install all the packages in a single environment.

We will thus, create each environment seperately with the following names:

1. mlst
2. seroba
3. spoligotyping
4. tbprofiler
5. ariba

run the following commands to create the specified environment and install all required packages and their dependencies for:

> mlst:

```bash
mamba create -n mlst mlst=2.22.1
```

> seroba:

```bash
mamba create -n seroba seroba=1.0.2
```

> spoligotyping:

```bash
mamba create -n spoligotyping spotyping=2.1
```

> tbprofiler:

```bash
mamba create -n tbprofiler tb-profiler=4.1.1
```

> ariba:

```bash
mamba create -n ariba ariba=2.14.6
```

These create the specified environment names `mlst`, `seroba`, `spoligotyping`, `tbprofiler` and `ariba` with the specified package versions and their dependencies.

We will activate and use these environments in [chapter 11](./materials/11-genotyping/11.1-genotyping.md) --- [Bacterial Genotyping and Drug Resistance Prediction](./materials/11-genotyping/11.1-genotyping.md).
:::

:::{.callout-note}
### Specify version of toool to install

As you may see, all the tools installed have specified version numbers added to the tool names in the format `tool=version_numer`. This allows us to install the exact version of tools used for the training.

For your personal use, if you wish to use the latest version of these tools, just omit specifying the version z-version_number` and the latest version of the tool will hopefully be installed.
:::


### Linux

:::{.callout}
### creating the `qc` environment and installing required packages

Open a terminal, make sure you are in the conda base environment and run this command to install all required packages and their dependencies:

```bash
mamba create -n qc fastq-scan=1.0.0 fastqc=0.11.9 fastp=0.23.2 kraken2=2.1.2 bracken=2.7 multiqc=1.13a
```

This creates an environment called `qc` with the specified package versions and their dependencies.


**NB.** The tools `fastq-scan and bracken` runs python scripts which require python libraries pandas, json, glob.  
Use the below command to install the packages in the `qc` environment:

```bash
conda install pandas -n qc -c conda-forge 
```

We will activate and use this environment in [chapter 4](./materials/04-sequence_qc/4.1-sequence_qc.md) --- [Sequencing Quality Control](./materials/04-sequence_qc/4.1-sequence_qc.md).
:::


:::{.callout}
### creating the `mapping` environment and installing required packages

run this command to install all required packages and their dependencies:

```bash
mamba create -n mapping bwa=0.7.17 samtools=1.15 bcftools=1.14 pysam=0.16.0.1 biopython=1.78
```

This creates an environment called `mapping` with the specified package versions and their dependencies.

**NB.** Creating the pseudogenomes step runs python scripts which require some python libraries.  
Use the below command to install the packages in the `mapping` environment:

```bash
conda install pandas -n qc -c conda-forge 
```

We will activate and use this environment in [chapter 5](./materials/05-short_read_mapping/5.1-short_read_mapping.md) --- [Short Read Mapping](./materials/05-short_read_mapping/5.1-short_read_mapping.md).
:::


:::{.callout}
### creating the `genotyping` environment and installing required packages

**NB.** For the genotyping and AMR prediction, we will create five different environments because some tools require specific versions of python and other related packages hence we cannot install all the packages in a single environment.

We will thus, create each environment seperately with the following names:

1. mlst
2. seroba
3. spoligotyping
4. tbprofiler
5. ariba

run the following commands to create the specified environment and install all required packages and their dependencies for:

> mlst:

```bash
mamba create -n mlst mlst=2.22.1
```

> seroba:

```bash
mamba create -n seroba seroba=1.0.2
```

> spoligotyping:

```bash
mamba create -n spoligotyping spotyping=2.1
```

> tbprofiler:

```bash
mamba create -n tbprofiler tb-profiler=4.1.1
```

> ariba:

```bash
mamba create -n ariba ariba=2.14.6
```

These create the specified environment names `mlst`, `seroba`, `spoligotyping`, `tbprofiler` and `ariba` with the specified package versions and their dependencies.

We will activate and use these environments in [chapter 11](./materials/11-genotyping/11.1-genotyping.md) --- [Bacterial Genotyping and Drug Resistance Prediction](./materials/11-genotyping/11.1-genotyping.md).

:::


:::{.callout-note}
### Specify version of toool to install

As you may see, all the tools installed have specified version numbers added to the tool names in the format `tool=version_numer`. This allows us to install the exact version of tools used for the training.

For your personal use, if you wish to use the latest version of these tools, just omit specifying the version z-version_number` and the latest version of the tool will hopefully be installed.
:::

:::::



## Downloading databases

::::: {.panel-tabset group="os"}


:::{.callout}
### [minikraken2](https://genomebiology.biomedcentral.com/articles/10.1186/s13059-019-1891-0) database

Download the kracken database "minikraken2_v1_8GB" into the `database` directory:

```bash
wget ftp://ftp.ccb.jhu.edu/pub/data/kraken2_dbs/old/minikraken2_v1_8GB_201904.tgz
```

Uncompress the database
```bash
tar xvfz minikraken2_v1_8GB_201904.tgz 
```

If the unzipped database is not same as the one use in the workshop, rename the it to match the workshop codes used using:

```bash
mv <unzipped_database_name> minikraken2_v1_8GB
```

You can now remove the zipped downloaded database as it is no longer required

```bash
rm minikraken2_v1_8GB_201904.tgz
```

:::


:::{.callout}
### bakta database

Download the Bakta database "db.tar.gz" into the `database` directory and unzip.

:::{.callout-note}
### one step

If you have the `denove_assembly` environment activated, you can perform this step.

```bash
bakta_db download --output <output-path> 
```

If you use this option, you don't need to perform the AMRFinderPlus step as the AMR-DB will be included automatically.
:::

```bash
wget https://bakta-db.s3.computational.bio.uni-giessen.de/db.tar.gz
```

or

```bash
wget https://zenodo.org/record/7025248/files/db.tar.gz
```

Uncompress the database

```bash
tar -xzf db.tar.gz
```

Rename the database to match the workshop codes used

```bash
mv db bakta_db
```

Delete zipped file after unzipping

```bash
rm db.tar.gz
```

Download the AMRFinderPlus database

```bash
amrfinder_update --force_update --database bakta_db/amrfinderplus-db/
```

Updating an existing bakta database

```bash
bakta_db update --db <existing-db-path> [--tmp-dir <tmp-directory>]
```

:::


:::{.callout}
### [seroba](https://github.com/sanger-pathogens/seroba) database

For git users, navigate to your `database` directory and clone the git repository:

```bash
git clone https://github.com/sanger-pathogens/seroba.git
```

Copy the database from the `seroba/` to your `database` directory --- this should be your current directory:

```bash
cp -r seroba/database .
```

Delete the git repository to clean up your system:

```bash
rm -r seroba
```

Still in your `database` directory, rename the database to match the workshop codes used:

```bash
mv database seroba_db
```
:::

:::::



## Nextflow

::: {.panel-tabset group="os"}

### Windows



### Mac OS


### Linux

:::



## Singularity

::: {.panel-tabset group="os"}

### Windows

You can use _Singularity_ from the _Windows Subsystem for Linux_ (see @wsl).  
Once you setup WSL, you can follow the instructions for Linux.

### Mac OS

Singularity is [not available for Mac OS](https://docs.sylabs.io/guides/3.0/user-guide/installation.html#install-on-windows-or-mac).

### Linux

These instructions are for _Ubuntu_ or _Debian_-based distributions[^1].

[^1]: See the [Singularity documentation page](https://docs.sylabs.io/guides/3.0/user-guide/installation.html#install-on-linux) for other distributions.

```bash
sudo apt update && sudo apt upgrade && sudo apt install runc
CODENAME=$(lsb_release -c | sed 's/Codename:\t//')
wget -O singularity.deb https://github.com/sylabs/singularity/releases/download/v3.10.2/singularity-ce_3.10.2-${CODENAME}_amd64.deb
sudo dpkg -i singularity.deb
rm singularity.deb
```

:::



## Visual Studio Code

::: {.panel-tabset group="os"}

### Windows

- Go to the [Visual Studio Code download page](https://code.visualstudio.com/Download) and download the installer for your operating system. 
  Double-click the downloaded file to install the software, accepting all the default options. 
- After completing the installation, go to your Windows Menu, search for "Visual Studio Code" and launch the application. 
- Go to "_File > Preferences > Settings_", then select "_Text Editor > Files_" on the drop-down menu on the left. Scroll down to the section named "_EOL_" and choose "_\\n_" (this will ensure that the files you edit on Windows are compatible with the Linux operating system).

### Mac OS

- Go to the [Visual Studio Code download page](https://code.visualstudio.com/Download) and download the installer for Mac.
- Go to the Downloads folder and double-click the file you just downloaded to extract the application. Drag-and-drop the "Visual Studio Code" file to your "Applications" folder. 
- You can now open the installed application to check that it was installed successfully (the first time you launch the application you will get a warning that this is an application downloaded from the internet - you can go ahead and click "Open").

### Linux (Ubuntu)

- Go to the [Visual Studio Code download page](https://code.visualstudio.com/Download) and download the installer for your Linux distribution. Install the package using your system's installer.

:::



## R and RStudio

::: {.panel-tabset group="os"}

### Windows

Download and install all these using default options:

- [R](https://cran.r-project.org/bin/windows/base/release.html)
- [RTools](https://cran.r-project.org/bin/windows/Rtools/)
- [RStudio](https://www.rstudio.com/products/rstudio/download/#download)

### Mac OS

Download and install all these using default options:

- [R](https://cran.r-project.org/bin/macosx/)
- [RStudio](https://www.rstudio.com/products/rstudio/download/#download)

### Linux

- Go to the [R installation](https://cran.r-project.org/bin/linux/) folder and look at the instructions for your distribution.
- Download the [RStudio](https://www.rstudio.com/products/rstudio/download/#download) installer for your distribution and install it using your package manager.

:::



## Workshop Data
<!--FIXME: add the dropbox link to the workshop data here
You can download the data used in this course from the following link: [Dropbox - Covid Bioinformatics (zip file) ](https://www.dropbox.com/s/7or0210elos3ril/covidbioinformaticsdata.zip?dl=0). 
Note that the file is 14GB big and will become 21GB after unzipping, so make sure you have enough space on your hard disk. 

Alternatively, you can run the following commands from the terminal (make sure you `cd` into the directory where you want to save the data): 

```bash
wget -O sarsbioinformatics.zip https://www.dropbox.com/s/7or0210elos3ril/covidbioinformaticsdata.zip?dl=1
unzip -d sars_genomics_workshop sarsbioinformatics.zip
rm sarsbioinformatics.zip
cd sars_genomics_workshop
```
-->





