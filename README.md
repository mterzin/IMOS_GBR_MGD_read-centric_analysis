# Seawater Microbes in Reef Monitoring

This repository contains the code and data associated with the paper:

**Seawater Microbes in Reef Monitoring: Gene Content is a Strong Predictor of Water Chemistry Across the Great Barrier Reef**

## Overview

This project involves a read-based metagenomics analysis applied to taxonomic and functional profiling of seawater microbiomes in offshore Great Barrier Reef (GBR) reefs. The study investigates the roles of environmental filtering and functional redundancy in shaping reef bacterioplankton communities, both at taxonomic and functional levels.

## Pipeline Description

1. **Quality Checking and Filtering:**
   - **FastQC** (version 0.11.3) was used to perform initial quality checks on demultiplexed raw reads. ([FastQC](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/))
   - **Trimmomatic** (version 0.38) was used for quality filtering to trim barcodes/adapters and remove low-quality bases (Phred <20). ([Trimmomatic](http://www.usadellab.org/cms/?page=trimmomatic))

2. **Alignment:**
   - Quality-filtered reads were aligned against the NCBI nr database using **DIAMOND** (version 2.0.9). ([DIAMOND](https://github.com/bbuchfink/diamond))
   - For each read, the top match reported by DIAMOND with an e-value of <10^-5 was retained to ensure high-quality annotations.

3. **Community Profiling:**
   - Resulting DIAMOND files (in daa format) were imported into **MEGAN** (version 6.23.0) for community profiling. ([MEGAN](http://www.megasoftware.net/))
   - Raw microbial abundance counts were exported from MEGAN for genus-level taxonomic and functional (GO-terms) composition.

4. **Data Analysis:**
   - The exported data were imported into **R Studio** (version 1.4.1717) for further analysis and visualization. ([R Studio](https://posit.co/download/rstudio-desktop/#download))

## Requirements

- **FastQC**: Version 0.11.3
- **Trimmomatic**: Version 0.38
- **DIAMOND**: Version 2.0.9
- **MEGAN**: Version 6.23.0
- **R Studio**: Version 1.4.1717

## Installation

To get started with the analysis, follow these steps:

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/your-repository.git
