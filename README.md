# This repository contains the code and data associated with the paper:
## Seawater Microbes in Reef Monitoring: Gene Content is a Strong Predictor of Water Chemistry Across the Great Barrier Reef

### Authors and Affiliations

- **Marko Terzin**  
  Australian Institute of Marine Science, PMB no3 Townsville MC, Townsville QLD 4810  
  College of Science and Engineering, James Cook University, Townsville, 4811  
  AIMS@JCU, James Cook University, Townsville QLD 4811

- **Steven J. Robbins**  
  Australian Centre for Ecogenomics, University of Queensland, St Lucia, QLD 4072

- **Sara C. Bell**  
  Australian Institute of Marine Science, PMB no3 Townsville MC, Townsville QLD 4810

- **Kim-Anh Lê Cao**  
  Melbourne Integrative Genomics and School of Mathematics and Statistics, University of Melbourne, Melbourne, Parkville VIC 3052

- **Renee K. Gruber**  
  Australian Institute of Marine Science, PMB no3 Townsville MC, Townsville QLD 4810

- **Pedro R. Frade**  
  Natural History Museum Vienna, 1010 Vienna, Austria

- **Nicole S. Webster**  
  Australian Institute of Marine Science, PMB no3 Townsville MC, Townsville QLD 4810  
  Australian Centre for Ecogenomics, University of Queensland, St Lucia, QLD 4072  
  Institute for Marine and Antarctic Studies, University of Tasmania, TAS, 7001

- **Yun Kit Yeoh**  
  Australian Institute of Marine Science, PMB no3 Townsville MC, Townsville QLD 4810  
  AIMS@JCU, James Cook University, Townsville QLD 4811

- **David G. Bourne**  
  Australian Institute of Marine Science, PMB no3 Townsville MC, Townsville QLD 4810  
  College of Science and Engineering, James Cook University, Townsville, 4811  
  AIMS@JCU, James Cook University, Townsville QLD 4811

- **Patrick W. Laffy**  
  Australian Institute of Marine Science, PMB no3 Townsville MC, Townsville QLD 4810  
  AIMS@JCU, James Cook University, Townsville QLD 4811


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

1. Download and install FastQC, Trimmomatic, DIAMOND, MEGAN, and R Studio from the provided links.
2. Follow the instructions in the `scripts/` directory to run the analysis pipeline.

## Usage

Detailed instructions on running the analysis scripts and processing the data are provided in the `scripts/` directory. Ensure that all dependencies are correctly installed and configured.

## References

- Andrews, S. (2010). FastQC: A quality control tool for high throughput sequence data. [FastQC](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/)
- Bolger, A. M., Lohse, M., & Usadel, B. (2014). Trimmomatic: A flexible trimmer for Illumina sequence data. *Bioinformatics*, 30(15), 2114-2120. [Trimmomatic](http://www.usadellab.org/cms/?page=trimmomatic)
- Buchfink, B., Xie, C., & Huson, D. H. (2015). DIAMOND: Fast alignment of short DNA sequences to large databases. *Bioinformatics*, 31(16), 3057-3064. [DIAMOND](https://github.com/bbuchfink/diamond)
- Huson, D. H., Mitra, S., Ruscheweyh, H. J., Weber, N., & Schuster, S. C. (2016). MEGAN Community Edition - Interactive exploration and analysis of large-scale microbiome sequencing data. *PLOS Computational Biology*, 12(6), e1004957. [MEGAN](http://www.megasoftware.net/)
- R Core Team (2023). R: A Language and Environment for Statistical Computing. R Foundation for Statistical Computing. [R](https://www.r-project.org/)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

For questions or issues, please contact Marko Terzin at:
m.terzin@aims.gov.au
marko.terzin@my.jcu.edu.au
