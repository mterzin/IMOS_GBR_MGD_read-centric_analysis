Seawater Microbes in Reef Monitoring

This repository contains the code and data associated with the paper:

Seawater Microbes in Reef Monitoring: Gene Content is a Strong Predictor of Water Chemistry Across the Great Barrier Reef
Overview

This project involves a read-based metagenomics analysis applied to taxonomic and functional profiling of seawater microbiomes in offshore Great Barrier Reef (GBR) reefs. The study investigates the roles of environmental filtering and functional redundancy in shaping reef bacterioplankton communities, both at taxonomic and functional levels.
Pipeline Description

    Quality Checking and Filtering:
        FastQC (version 0.11.3) was used to perform initial quality checks on demultiplexed raw reads. (FastQC)
        Trimmomatic (version 0.38) was used for quality filtering to trim barcodes/adapters and remove low-quality bases (Phred <20). (Trimmomatic)

    Alignment:
        Quality-filtered reads were aligned against the NCBI nr database using DIAMOND (version 2.0.9). (DIAMOND)
        For each read, the top match reported by DIAMOND with an e-value of <10^-5 was retained to ensure high-quality annotations.

    Community Profiling:
        Resulting DIAMOND files (in daa format) were imported into MEGAN (version 6.23.0) for community profiling. (MEGAN)
        Raw microbial abundance counts were exported from MEGAN for genus-level taxonomic and functional (GO-terms) composition.

    Data Analysis:
        The exported data were imported into R Studio (version 1.4.1717) for further analysis and visualization. (R Studio)

Requirements

    FastQC: Version 0.11.3
    Trimmomatic: Version 0.38
    DIAMOND: Version 2.0.9
    MEGAN: Version 6.23.0
    R Studio: Version 1.4.1717

Installation

To get started with the analysis, follow these steps:

    Clone the repository:

    bash

    git clone https://github.com/yourusername/your-repository.git

    Install required tools and dependencies:
        Download and install FastQC, Trimmomatic, DIAMOND, MEGAN, and R Studio from the provided links.

    Follow the instructions in the scripts/ directory to run the analysis pipeline.

Usage

Detailed instructions on running the analysis scripts and processing the data are provided in the scripts/ directory. Ensure that all dependencies are correctly installed and configured.
References

    Andrews, S. (2010). FastQC: A quality control tool for high throughput sequence data. FastQC
    Bolger, A. M., Lohse, M., & Usadel, B. (2014). Trimmomatic: A flexible trimmer for Illumina sequence data. Bioinformatics, 30(15), 2114-2120. Trimmomatic
    Buchfink, B., Xie, C., & Huson, D. H. (2015). DIAMOND: Fast alignment of short DNA sequences to large databases. Bioinformatics, 31(16), 3057-3064. DIAMOND
    Huson, D. H., Mitra, S., Ruscheweyh, H. J., Weber, N., & Schuster, S. C. (2016). MEGAN Community Edition - Interactive exploration and analysis of large-scale microbiome sequencing data. PLOS Computational Biology, 12(6), e1004957. MEGAN
    R Core Team (2023). R: A Language and Environment for Statistical Computing. R Foundation for Statistical Computing. R

License

This project is licensed under the MIT License - see the LICENSE file for details.
Contact

For questions or issues, please contact [your email address].

Feel free to adjust the installation instructions and usage details based on the actual scripts and processes in your repository.
