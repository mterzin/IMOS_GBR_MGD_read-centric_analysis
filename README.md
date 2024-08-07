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

4. **Data Processing in R**:
   - Data was imported into **R Studio** (version 1.4.1717) using the **phyloseq** R package.
   - Further filtering steps included:
     1. Removal of non-annotated reads.
     2. Exclusion of reads annotated as eukaryotic or viral.
     3. Removal of prokaryotic reads annotated only to the Domain level (Bacteria or Archaea), leaving 48% of the total dataset.
     4. Exclusion of rare/spurious reads (relative abundance < 0.0001%), resulting in 618 of the initial 1179 prokaryotic taxa for the final microbial taxonomy dataset. For gene annotation, 5015 GO terms were retained.

5. **Normalization and Visualization**:
   - Microbial abundance data was Center-Log-Ratio (CLR) normalized using the **microbiome** R package to address sparsity and compositional nature of metagenomic data. Pseudo counts were introduced prior to CLR normalization as log 0 is undefined.
   - CLR-transformed counts or relative abundance data were used for downstream statistical analysis and visualization in R Studio.
   - Final composite plots were created using **Inkscape** (version 0.92.5).


## Requirements

- **FastQC**: Version 0.11.3
  - **Purpose**: Quality control tool for high-throughput sequencing data, used to assess the quality of raw sequence reads.

- **Trimmomatic**: Version 0.38
  - **Purpose**: Tool for trimming Illumina sequence data, used to remove adapter sequences and low-quality bases from sequencing reads.

- **DIAMOND**: Version 2.0.9
  - **Purpose**: Fast alignment tool for comparing short DNA sequences to large databases, used for sequence alignment and similarity searching.

- **MEGAN**: Version 6.23.0
  - **Purpose**: Software for the interactive exploration and analysis of large-scale microbiome sequencing data, used for taxonomic and functional profiling.

- **R Studio**: Version 1.4.1717

  - Summary of ***R Packages Used***:
    - ***raster***: Used for handling and analyzing raster data to visualize reef locations on maps.
    - ***tidyverse***: A suite of R packages for data manipulation, visualization, and analysis.
    - ***ggspatial***: Provides tools for visualizing spatial data with ggplot2.
    - ***sf***: Provides simple features for R, enabling spatial vector data handling.
    - ***dataaimsr***: Facilitates access and analysis of AIMS data.
    - ***gisaimsr***: Provides tools for GIS data analysis within the AIMS framework.
    - ***ggrepel***: Enhances ggplot2 plots by adding text labels with automatic repelling.
    - ***phyloseq***: Provides tools for analyzing and visualizing high-throughput microbiome census data.
    - ***mixOmics***: Implements methods for multivariate analysis, including Principal Component Analysis (PCA) and integration of different data types.
    - ***microbiome***: Provides tools for analyzing microbiome data, including data normalization and diversity analysis.
    - ***vegan***: Offers functions for community ecology analysis, including distance measures and ordination methods.

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
- McMurdie, P.J., & Holmes, S. (2013). *phyloseq: An R Package for Reproducible Interactive Analysis and Graphics of Microbiome Census Data*. [CRAN Package](https://cran.r-project.org/package=phyloseq)
- Pebesma, E. (2018); Pebesma, E., & Bivand, R. (2023). *sf: Simple Features for R*. [CRAN Package](https://cran.r-project.org/package=sf)
- Hijmans, R.J. (2024). *raster: Geographic Data Analysis and Modeling*. [CRAN Package](https://cran.r-project.org/package=raster)
- Open-AIMS. (2024). *gisaimsr: GIS Tools for AIMS*. [GitHub Repository](https://github.com/open-AIMS/gisaimsr)
- Barneche, D.R., et al. (2021). *dataaimsr: Data Management for AIMS*. [CRAN Package](https://cran.r-project.org/package=dataaimsr)
- Dunnington, D., et al. (2023). *ggspatial: Spatial Data Visualization*. [CRAN Package](https://cran.r-project.org/package=ggspatial)
- Wickham, H., et al. (2019). *tidyverse: Easily Install and Load the 'Tidyverse'*. [CRAN Package](https://cran.r-project.org/package=tidyverse)
- Slowikowski, K., et al. (2024). *ggrepel: Automatically Reposition Text Labels*. [CRAN Package](https://cran.r-project.org/package=ggrepel)
- Lahti, L., & Shetty, S. (2017). *microbiome: Microbiome Analysis*. [CRAN Package](https://cran.r-project.org/package=microbiome)
- Rohart, F., et al. (2017). *mixOmics: A Comprehensive R Package for Multi-Omics Data Analysis*. [CRAN Package](https://cran.r-project.org/package=mixOmics)
- Oksanen, J., et al. (2010). *vegan: Community Ecology Package*. [CRAN Package](https://cran.r-project.org/package=vegan)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

For questions or issues, please contact Marko Terzin at:
m.terzin@aims.gov.au
marko.terzin@my.jcu.edu.au
