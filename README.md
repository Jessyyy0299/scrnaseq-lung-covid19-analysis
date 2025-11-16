# scRNAseq-Melms2021-Analysis
Single-cell RNA-seq analysis of Melms2021 COVID-19 lung dataset using Seurat

# scRNAseq-Melms2021-Analysis

Single-cell RNA-seq analysis of the **Melms et al. 2021** COVID-19 lung dataset using **Seurat** in R.

> Author: **Jessy Xue**  
> Course: Single-cell RNA-seq Lab 1  
> Date: 2025-10-25  

---

## 🧬 Overview

This repository contains a complete single-cell RNA-seq workflow on the **Melms2021** lung dataset.  
The analysis is implemented in **R / R Markdown** and uses **Seurat** for preprocessing, dimensionality reduction, clustering, and visualization.

The main goals are:

- Perform **quality control (QC)** on cells and genes  
- Normalize and scale the data  
- Run **PCA** and choose informative components  
- Perform **clustering** and visualize cells in **UMAP space**  
- Identify **marker genes** for key cell populations  
- Provide **biological interpretation** of the main clusters

---

## 🛠 Methods & Pipeline

The analysis follows a standard Seurat pipeline:

1. **Quality control**
   - Filter cells by:
     - `nFeature_RNA` (number of detected genes)  
     - `nCount_RNA` (UMI counts)  
     - Percentage of mitochondrial genes  
   - Visualized with violin / scatter plots.

2. **Normalization & feature selection**
   - `NormalizeData()` with log-normalization  
   - `FindVariableFeatures()` to select highly variable genes  
   - (Optional) scaling with `ScaleData()`.

3. **Dimensionality reduction**
   - **PCA** on variable genes  
   - Examine **Elbow plot** to choose the number of PCs used downstream.

4. **Clustering**
   - Construct SNN graph with `FindNeighbors()`  
   - Cluster cells with `FindClusters()` at a chosen resolution.

5. **UMAP embedding**
   - Run `RunUMAP()` on the selected PCs  
   - Visualize cell clusters in 2D UMAP space.

6. **Marker gene analysis**
   - Use `FindAllMarkers()` to identify genes enriched in each cluster  
   - Inspect known markers (e.g. epithelial, endothelial, fibroblast, immune markers)  
   - Match clusters to putative **cell types**.

---

## 📁 Repository Contents

- `scRNA-seq-lab1-melms2021.Rmd`  
  - Main R Markdown file containing the full analysis code.

- `scRNA-seq-lab1-melms2021.html`  
  - Rendered HTML report with all figures and interpretations.

*(Optional in the future)*  
You can add a `figures/` folder with exported PNGs for PCA, UMAP, and QC plots.

---

## 💻 How to run the analysis

1. Clone or download this repository:

   ```bash
   git clone https://github.com/Jessyyy0299/scRNAseq-Melms2021-Analysis.git

