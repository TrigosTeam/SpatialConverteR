# SpatialConverteR
SpatialConverteR is an R package for conversion of single-cell -omics data objects. The package facilitates conversion between 
[Seurat by satijalab](https://satijalab.org/seurat/), [AnnData by scverse](https://anndata.readthedocs.io/en/stable/) and [BioConductor's SpatialExperiment](https://www.bioconductor.org/packages/release/bioc/html/SpatialExperiment.html)/[SingleCellExperiment](https://bioconductor.org/packages/release/bioc/html/SingleCellExperiment.html), and is compatible with disassociated single-cell and spatial data. 

Developed for use fully in R, the package functions without the need for any python virtual environments, and supports conversion with spatial and image data.

# Installation
Install as an R package using remotes:
```
if (!requireNamespace("remotes", quietly = TRUE))
	install.packages("remotes")

remotes::install_github("TrigosTeam/SpatialConverteR")
```


# Usage
### Seurat and AnnData
Ensure Seurat and AnndataR are installed.
```
if (!requireNamespace("Seurat", quietly = TRUE))
	install.packages("Seurat")
if (!requireNamespace("BiocManager", quietly = TRUE))
	install.packages("BiocManager")
if (!requireNamespace("AnndataR", quietly = TRUE))
	BiocManager::install("AnndataR")

# AnnData to Seurat
SpatialConverteR::anndataToSeurat(adata_path, image = FALSE)

# Seurat to AnnData
SpatialConverteR::seuratToAnndata(seurat_obj, export_path, raw_counts_names = c("RNA", "counts"), image = FALSE)
```

### Seurat and SingleCellExperiment/SpatialExperiment
Ensure Seurat, SingleCellExperiment and SpatialExperiment are installed.
```
if (!requireNamespace("Seurat", quietly = TRUE))
	install.packages("Seurat")
if (!requireNamespace("BiocManager", quietly = TRUE))
	install.packages("BiocManager")
if (!requireNamespace("SpatialExperiment", quietly = TRUE))
	BiocManager::install("SpatialExperiment")

# Seurat to SingleCellExperiment/SpatialExperiment
SpatialConverteR::seuratToSpatialExperiment(seurat_obj, image = FALSE)

# SingleCellExperiment/SpatialExperiment to Seurat
SpatialConverteR::spatialExperimentToSeurat(spe, raw_counts_name = "counts", image = FALSE)
```

### SingleCellExperiment/SpatialExperiment and AnnData
Ensure SingleCellExperiment, SpatialExperiment and anndataR are installed.
```
if (!requireNamespace("BiocManager", quietly = TRUE))
	install.packages("BiocManager")
if (!requireNamespace("SpatialExperiment", quietly = TRUE))
	BiocManager::install("SpatialExperiment")
if (!requireNamespace("AnndataR", quietly = TRUE))
	BiocManager::install("AnndataR")

# AnnData to SingleCellExperiment/SpatialExperiment
SpatialConverteR::anndataToSpatialExperiment(adata_path, image = FALSE)

# SingleCellExperiment/SpatialExperiment to AnnData
SpatialConverteR::spatialExperimentToAnndata(spe, export_path, raw_counts_name = "counts", image = FALSE)
```
More information is provided in the documentation of each function.


# Alternatives
There are multiple known alternatives:
1. [anndataR](https://www.bioconductor.org/packages/release/bioc/html/anndataR.html)
2. [zellkonverter](https://bioconductor.org/packages/release/bioc/html/zellkonverter.html)
3. [SeuratDisk](https://github.com/mojaveazure/seurat-disk)
4. [sceasy](https://github.com/cellgeni/sceasy) and [schard](https://github.com/cellgeni/schard/tree/main)
5. [anndata2ri](https://pypi.org/project/anndata2ri/)

However, many of these require the use of a python environment, struggle with spatial data, do not support conversion with histological imaging, or are no longer supported.
