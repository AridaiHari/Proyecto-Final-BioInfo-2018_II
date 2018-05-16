This README describe the pipeline to follow for do basic population genomic analysis using SNPs.

The README  is part of a bioinformatic project that contains scripts for organize a project, for donwload genomic data from a repository, for analyze this kind of data and for do some graphics. All for make a reproducible bioinformatic proyect.

---

#### Directories
The working directory `finalproyect_/bin` contains all the scripts for run the differents softwares used. Each script is numbered in the order followed. There are repeated numbers diffrentiated by a letter beacuse we separated the scripts for each dataset (<span style="color:red">*Acanthurus olivaceus*</span>, <span style="color:purple">*Acanthurus reversus*</span> and the <span style="color:cyan">two together</span>, in this way we try to make the analysis of each species independent.

The working directory `finalproyect_/data` contains the original data set, the inputs required for each software and the outputs generated. The files are organized in the directories corresponding to the species name.

The working directory `finalproyect_/Plots` contains the figures obtained with Fastxtools and R.

---

#### Scripts and functions

The script `0_Installation.sh` is for donwload and install all the softwares required and his dependencies, less those available by biocontainers. Those softwares were working in docker. This script assumes that the finalproject_ directory exist. Also, inside finalproject_ the directory with the scripts already exist (bin).

The script `1_Preparation.sh` is for donwload the sequences of *Dryad* and rename them for do the project.

The script `2a_VerifyPreprocess_ARE.sh` utilize the <span style="color:purple">*Acanthurus reversus*</span> sequences. This script is for verify the quality of sequences and realize a quality filter. Organize the outputs in their correspondent directory. We use the docker umages of  **FastQC** and **fastxtools**, available in Biocontainers.

The script `2b_VerifyPreprocess_OLI.sh` utilize the <span style="color:red">*Acanthurus olivaceus*</span> sequences. This script is for verify the quality of sequences and realize a quality filter.Organize the outputs in their correspondent directory. 

The script `3_ReferenceGenome.sh` donwload and save the genome sequence of <span style="color:green">*Sebastes steindachneri*</span>.

The script `4a_EnsambleReference_ARE.sh` use the software ** *Ipyrad* ** to assemble the  <span style="color:purple">*Acanthurus reversus*</span> sequences with reference genome. For this analysis we use the previous cleaned sequences. The output is a VCF file. All the assemblies was visualized in Tassel.

The script `4b_EnsambleReference_OLI.sh` use the software ** *Ipyrad* ** to assemble the <span style="color:red">*Acanthurus olivaceus*</span> sequences with reference genome.

The script `4c_EnsambleReference_Re_Ol.sh` use the software ** *Ipyrad* ** to assemble the <span style="color:cyan">two genomes together</span> with reference genome.

###### *In`finalproyect_/data` directory we include all the params set that We try but the script was developped with the final params. This comment clause apply for 4a, 4b and 4c*

The script `5a_exploratoryAnalysis_ARE.R` identify genetics cluster with exploratory methods. We analize the variation of <span style="color:purple">*Acanthurus reversus*</span> with Principal Components Analysis (*PCA*) and Discriminant Analysis of Pincipal Components (*DAP*C). This analysis were made with the R packages **SNPRelate** and **adegenet**. The input of SNPRelate was a VCF file but for adegenet we use a Genepop. The Genepop was obtained with PGDSpider.

The script `5b_exploratoryAnalysis_OLI.R` identify genetics cluster with exploratory methods. We analize the variation of <span style="color:red">*Acanthurus olivaceus*</span> *PCA* and *DAPC*.

The script `6a_populationParams_ARE.sh` calculates depth by site and by individual. Also calculates population statistics as nucleotide diversity, heterocygosity, Hardy-Weinberg equilibrium and linkage desequilibrium of <span style="color:purple">*Acanthurus reversus*</span>. For this step we use the docker image **VCFtools**

The script `6a_populationParams_ARE.sh` calculates depth by site and by individual. Also calculates the same population statistics for <span style="color:red">*Acanthurus olivaceus*</span>.

- - -

#### Further information


For more information about params and technical specifications of this softwares

[Biocontainers](https://github.com/BioContainers/containers),[Docker](https://www.docker.com/), [FastQC](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/), [Fastxtools](http://hannonlab.cshl.edu/fastx_toolkit/), [Ipyrad](http://ipyrad.readthedocs.io/index.html), [PGDSpider](http://www.cmpg.unibe.ch/software/PGDSpider/), [R](https://www.r-project.org) ([adegenet](https://cran.r-project.org/web/packages/adegenet/adegenet.pdf), [SNPRelate](http://www.bioconductor.org/packages/release/bioc/manuals/SNPRelate/man/SNPRelate.pdf)), [Tassel](http://www.maizegenetics.net/tassel), [VCFtools](http://vcftools.sourceforge.net/).

This project is written by Gabriela Aridai Borja Martínez (madreporita@ciencias.unam.mx)