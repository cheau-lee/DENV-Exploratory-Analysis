# An Integrative Analysis of Transcriptomic Data

## Introduction
Dengue virus (DENV) is a hyperendemic infectious disease that poses a major global health threat, notably prevalent in tropical regions of America, South-East Asia, and the West Pacific (WHO, 2023). Particularly, its primary mode of transmission is through the *Aedes* mosquito. This project aims to offer comprehensive insights into gene expression patterns across diverse patient cohorts, including convalescent (CONV), dengue fever (DF), dengue haemorrhagic fever (DHF), and healthy controls (HC). Utilising Python, the gene expression dataset is applied to several techniques such as Principal Component Analysis (PCA), Hierarchical Clustering Analysis (HCA), and Differential Gene Expression Analysis. Furthermore, this research seeks to elucidate the intricate molecular pathways governing the host response to DENV infection, through Gene Ontology (GO) and Pathway Enrichment Analysis. Thus, uncovering key relationships that may inform future diagnostic and therapeutic strategies.

## Dataset
The initial gene expression dataset is based on DNA microarray analysis which examined blood samples from individuals during acute DENV infection and convalescence (Kwissa *et al.*, 2014). This is readily accessible on the Gene Expression Omnibus (GEO) under the accession number GDS5093. However, a [cleaned version](https://drive.google.com/drive/folders/1Dk3ah6tFMUb27K3XUsSWJLxChW_U2eEy?usp=share_link) used for this project is available as:
- **`dengue_data.csv`**: Contains gene expression values.
- **`dengue_metadata.csv`**: Contains sample information.

## Getting Started

### Prerequisites
Before installing the dependencies, ensure you have Python ≥ 3.8 installed on your system.
### Installation
1. **Clone the Repository**:
   ```bash
   git clone <https://github.com/cheau-lee/Dengue-Gene-Exploratory-Analysis.git>

2. **Install Dependencies**:
   ```bash
   pip install -r requirements.txt

### Used Libraries 
- **pandas**: Data manipulation.
- **numpy**: Numerical operations.
- **scikit-learn**: Principal Component Analysis (PCA).
- **matplotlib**: Generate visualisations such as volcano plots.
- **scipy**: Hierarchical Clustering Analysis (HCA) and statistical tests.
- **seaborn**: Create annotated heatmaps and clustermaps.

## Analysis Notebooks
### Overall Exploratory Analysis
**`Exploratory_Analysis.ipynb`**
- **Overview**: Provides a comprehensive overview of the entire analysis pipeline, including data loading, cleaning, and analyses involved.
- **Content**:
  - PCA Analysis
  - HCA Analysis 
  - Volcano Plot Analysis

### Specific Analyses
**`PCA_Analysis.ipynb`**
- **Overview**: Principle Component Analysis (PCA) is a multivariate statistical tool for dimensionality reduction, performed by using the *scikit-learn* module to generate 10 principal components. A two-dimensional PCA (PC1 and PC2) was plotted to illustrate the relationships between samples representing each disease state.
  - PCA computation
  - PCA visualisation

**`HCA_Analysis.ipynb`**
- **Overview**: Hierarchical Clustering Analysis (HCA) was conducted in two phases: a sample-centric analysis of the entire dataset and a gene-centric analysis on the first 100 genes. This utilised the *scipy.cluster.hierarchy* module with the complete linkage method and Euclidean distance metric to produce dendrograms illustrating the hierarchal relationships among samples and genes. The *seaborn* package was utilised to create an annotated heatmap using the *clustermap* function, uncovering futher insights into their expression profiles and associations.
- **Content**
  - Sample-centric dendrograms
  - Gene-centric dendrograms
  - Heatmap 

**`Volcano_Plot_Analysis.ipynb`**
- **Overview**: Differential expression analysis was carried to out to identify significant gene expression changes between various disease states and healthy controls. This involved the *scipy.stats* module with the *ttest_ind* function to calculate the t-statistic and associated p-values. The dataset was partitioned according to distinct disease states, in which the fold changes and p-values were computed for each gene. This was according to predefined significance thresholds of log2FC (1.0) and p-value (<0.05). The resulting volcano plots are annotated with top upregulated genes to provide an overview of the differential expression patterns and the key genes associated with pathological conditions.
- **Content**:
  - Fold change and p-value calculations
  - Volcano plot visualisations for different disease states
  - Top upregulated genes

## Key Findings
- **Upregulated Genes**:Key upregulated genes associated with dengue fever (DF) include CEP55, KCTD14, PBK, and CDC6, while for dengue hemorrhagic fever (DHF), the primary upregulated genes are AI401105, PBK, CEP55, CDC6, and SPC25. Notably, PBK and CEP55 are commonly upregulated in both conditions, indicating their potential roles in the pathogenesis of dengue.
- **Gene Ontology**: Revealed shared processes such as the negative regulation of DNA replication and association with CDC6.
- **Pathway Enrichment**: For DF, the "CDC6 association with ORC (HAS-68689)" pathway was prominent, implicating a disruption in the initiation of DNA replication. For DHF, the "cell cycle checkpoint R-HAS-69620" pathway was most impacted, suggesting a more profound impairment in cell cycle checkpoints and possibly explaining the severity of the condition.

     
## References

1. Kwissa, M., Nakaya, H. I., Onlamoon, N., Wrammert, J., Villinger, F., Perng, G. C., Yoksan, S., Pattanapanyasat, K., Chokephaibulkit, K., Ahmed, R., & Pulendran, B. (2014). **Dengue virus infection induces expansion of a CD14(+)CD16(+) monocyte population that stimulates plasmablast differentiation.** *Cell Host & Microbe*, 16(1), 115–127.

2. World Health Organization. (2023). **Dengue and severe dengue: Fact sheet.** Available at: [https://www.who.int/news-room/fact-sheets/detail/dengue-and-severe-dengue](https://www.who.int/news-room/fact-sheets/detail/dengue-and-severe-dengue) [Accessed 10 December 2023].



