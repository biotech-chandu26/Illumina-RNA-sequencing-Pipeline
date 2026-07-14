# Illumina-RNA-sequencing-Pipeline

[![Platform](https://img.shields.io/badge/Platform-Linux-blue.svg)]()
[![Language](https://img.shields.io/badge/Language-Bash-green.svg)]()
[![Sequencing](https://img.shields.io/badge/Sequencing-Illumina-orange.svg)]()
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)]()

## Overview

This repository contains an **end-to-end automated Illumina RNA-Seq analysis pipeline** written in Bash. The pipeline performs the complete workflow starting from downloading sequencing data from the NCBI Sequence Read Archive (SRA) to generating gene expression count matrices.

The workflow has been designed for reproducible transcriptome analysis and can be adapted for any organism by supplying the appropriate reference genome and annotation.

---

## Workflow

```
                 NCBI SRA
                    │
                    ▼
              prefetch
                    │
                    ▼
            fasterq-dump
                    │
                    ▼
           Paired-end FASTQ
                    │
                    ▼
               FastQC
                    │
                    ▼
               MultiQC
                    │
                    ▼
            HISAT2 Index
                    │
                    ▼
           HISAT2 Alignment
                    │
                    ▼
                 SAM File
                    │
                    ▼
                 BAM File
                    │
                    ▼
          Sort & Index BAM
                    │
                    ▼
        Alignment Statistics
                    │
                    ▼
           featureCounts
                    │
                    ▼
         Gene Count Matrix
```

---

# Features

- Fully automated RNA-Seq workflow
- Automatic SRA download
- FASTQ extraction
- FASTQC quality assessment
- MultiQC report generation
- HISAT2 genome indexing
- Splice-aware alignment
- BAM conversion, sorting and indexing
- Alignment statistics
- Genome coverage statistics
- Gene quantification using featureCounts
- Organized directory structure
- Logging support
- Easily customizable

---

# Software Requirements

The following software should be installed.

| Software | Version |
|----------|----------|
| SRA Toolkit | Latest |
| HISAT2 | Latest |
| SAMtools | Latest |
| FastQC | Latest |
| MultiQC | Latest |
| Subread (featureCounts) | Latest |
| pigz | Latest |

---

# Installation

Clone the repository

```bash
git clone https://github.com/<username>/Illumina-RNASeq-Pipeline.git

cd Illumina-RNASeq-Pipeline
```

Make the pipeline executable

```bash
chmod +x illumina_rnaseq_pipeline.sh
```

---

# Input Files

The pipeline requires:

- RNA-Seq SRA accession
- Reference genome FASTA
- Gene annotation GTF

Example

```
SRR33408710
genome.fa
annotation.gtf
```

---

# Directory Structure

```
Illumina-RNASeq-Pipeline/

├── fastq/
├── fastqc/
├── multiqc/
├── alignment/
├── counts/
├── logs/
├── hisat2_index/
├── illumina_rnaseq_pipeline.sh
└── README.md
```

---

# Running the Pipeline

Edit the configuration section inside the script

```bash
SRR="SRR33408710"

THREADS=16

GENOME="genome.fa"

GTF="annotation.gtf"
```

Execute

```bash
./illumina_rnaseq_pipeline.sh
```

---

# Output

```
fastq/
│
├── SRR33408710_1.fastq.gz
├── SRR33408710_2.fastq.gz

fastqc/

multiqc/

alignment/

counts/

logs/
```

Important output files

| File | Description |
|------|-------------|
| flagstat.txt | Alignment statistics |
| alignment.stats | Detailed mapping statistics |
| coverage.txt | Genome coverage |
| gene_counts.txt | Gene expression counts |

---

# Pipeline Steps

1. Download sequencing data using **prefetch**
2. Convert SRA to paired-end FASTQ
3. Compress FASTQ files
4. Perform quality control using FastQC
5. Generate MultiQC report
6. Build HISAT2 genome index
7. Align reads to reference genome
8. Convert SAM to BAM
9. Sort BAM
10. Index BAM
11. Generate alignment statistics
12. Estimate genome coverage
13. Quantify gene expression using featureCounts

---

# Example Dataset

Organism

**Trichiurus japonicus**

Dataset

**SRR33408710**

Platform

**Illumina Paired-End RNA-Seq**

---

# Future Improvements

- Automatic dependency checking
- Command-line arguments
- Resume interrupted analysis
- Automatic thread detection
- Differential expression analysis using DESeq2
- Transcript assembly using StringTie
- Functional enrichment analysis
- Docker support
- Singularity support
- Nextflow implementation
- Snakemake implementation

---

# Citation

If you use this pipeline in your research, please cite the software used within the workflow.

- Kim et al. HISAT2
- Li et al. SAMtools
- Andrews. FastQC
- Ewels et al. MultiQC
- Liao et al. featureCounts

---

# Author

**Chandrajeet**

Bioinformatics Researcher

---

# License

This project is distributed under the MIT License.

---

# Acknowledgements

This pipeline makes use of the following open-source software:

- SRA Toolkit
- HISAT2
- SAMtools
- FastQC
- MultiQC
- Subread
- pigz

---

## Repository Topics

```
rna-seq
illumina
transcriptomics
bioinformatics
hisat2
featurecounts
samtools
fastqc
multiqc
bash
pipeline
genomics
```
