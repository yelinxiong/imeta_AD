# Single-Cell Transcriptomics Reveals Cellular Heterogeneity and Phenotypic Transitions of Smooth Muscle Cells in Aortic Dissection

## Overview

This repository contains the complete analysis code for the manuscript:

**"Single-cell transcriptomics reveals cellular heterogeneity and phenotypic transitions of smooth muscle cells in aortic dissection"**

## Repository Structure

```
imeta_scRNA_AD/
├── Figure1/
│   ├── Figure1.Rmd                          # Figure 1 analysis code
│   ├── Fig1A_UMAP_coordinates.csv           # Source data
│   ├── Fig1B_TOP5_markers.csv
│   ├── Fig1C_composition_by_thrombus.csv
│   ├── Fig1D_DEG_thrombus_vs_no.csv
│   ├── Fig1E_GSEA_TOP10_per_group.csv
│   ├── Fig1F_ANGPTL4_statistics.csv
│   ├── Fig1G_myeloid_UMAP.csv
│   ├── Fig1H_myeloid_by_thrombus.csv
│   └── Fig1H_myeloid_by_tissue.csv
├── Figure2/
│   ├── Figure2.Rmd                          # Figure 2 analysis code
│   ├── Fig2A_celltype_distribution.csv      # Source data
│   ├── Fig2B_SMC_proportions.csv
│   ├── Fig2C_Hallmark_TOP10_per_subtype.csv
│   ├── Fig2D_C2_TOP10_per_subtype.csv
│   ├── Fig2E_cell_pseudotime.csv
│   ├── Fig2F_interaction_counts.csv
│   ├── Fig2F_interaction_weights.csv
│   ├── Fig2G_SMC_EC_signaling.csv
│   └── Fig2H_all_pathways_to_EC.csv
├── FigureS1/
│   └── FigureS1.Rmd                         # Supplementary Figure S1
├── FigureS2/
│   └── FigureS2.Rmd                         # Supplementary Figure S2
└── README.md                                # This file
```

## Figures

### Main Figures

- **Figure 1**: Single-cell RNA sequencing reveals cellular heterogeneity in thrombus-related Aortic Dissection
  - 8 panels (A-H): UMAP, markers, composition, DEGs, GSEA, and myeloid analysis

- **Figure 2**: Identification and characterization of smooth muscle cell subpopulations in Aortic Dissection
  - 8 panels (A-H): SMC characterization, pathways, trajectory, and CellChat analysis

### Supplementary Figures

- **Figure S1**: Supplementary marker, clinical association, and myeloid enrichment analyses
  - Canonical markers, clinical associations, myeloid enrichment

- **Figure S2**: Extended analyses of cells programs and intercellular signaling
  - Volcano plots, trajectory details, EC analysis, ligand-receptor expression

## Data Requirements

### Required Data Files

Each analysis requires the following data files:

1. **Main Seurat Object** (`seurat_object.rds`)
   - Contains all single-cell data with UMAP embeddings
   - Cell type annotations in `subtype` column
   - Tissue type in `exp` column ("Dissection tissue" or "Adjacent normal")

2. **Myeloid Subset** (`myeloid_subset.rds`)
   - Subset of myeloid cells with subtype annotations

3. **CellChat Results** (`cellchat_results.rds`)
   - Pre-computed cell-cell communication analysis

### Data File Locations

The RMD files expect data files to be located in the parent directory. Update the file paths in each RMD file to match your data location:

```r
# Example: Update these paths in each RMD file
seurat_obj <- readRDS('path/seurat_object.rds')
myeloid_obj <- readRDS('path/myeloid_subset.rds')
cellchat_results <- readRDS('path/cellchat_results.rds')
```

## Software Requirements

### R Environment
- R >= 4.0.0
- RStudio (recommended)

### R Packages

```r
# Core packages
install.packages(c("Seurat", "tidyverse", "ggplot2", "dplyr", "patchwork"))

# Cell-cell communication
remotes::install_github("sqjin/CellChat")

# Trajectory analysis
BiocManager::install("monocle3")

# Visualization
install.packages(c("ComplexHeatmap", "circlize", "EnhancedVolcano", "ggpubr"))

# Statistics
install.packages("rstatix")
```

## Running the Analysis

### Quick Start

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/imeta_scRNA_AD.git
cd imeta_scRNA_AD
```

2. **Prepare data files**
   - Download or prepare the required RDS files
   - Rename your data files to match the expected names
   - Place them in the parent directory of the repository

3. **Run analysis for each figure**
```r
# Open RStudio and navigate to a figure folder
setwd("Figure1")

# Knit the R Markdown file
rmarkdown::render("Figure1.Rmd")
```

### Output Files

Each RMD file will generate:
- **PDF figures**: Publication-quality figures for each panel
- **CSV files**: Source data for each panel

All output files are saved in the same directory as the RMD file.

### Example Output

After running `Figure1.Rmd`, you will find:
```
Figure1/
├── Figure1.Rmd
├── Fig1A_UMAP_celltypes.pdf
├── Fig1A_UMAP_coordinates.csv
├── Fig1B_TOP5_markers_heatmap.pdf
├── Fig1B_TOP5_markers.csv
├── ... (and more)
```

## Reproducibility

All analyses are fully reproducible using the provided R Markdown notebooks.

## Citation

If you use this code or data, please cite:

```bibtex
@article{
  title={Single-cell transcriptomics reveals cellular heterogeneity and phenotypic transitions of smooth muscle cells in aortic dissection},
  journal={iMeta},
  year={2026},
  doi={10.xxxx/xxxxxx}
}
```

## Contact

**Code Author**: Lin-Xiong Ye
**Email**: 445233812@qq.com

For questions or issues, please open an issue on GitHub.

## Acknowledgments

We thank all contributors and collaborators for their support in this project.

