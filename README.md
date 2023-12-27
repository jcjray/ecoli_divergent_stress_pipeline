2022.09.09

# _E. coli_ divergent stress pipeline
Bioinformatic pipeline used for the following paper:

Wang H, McElfresh GW, Wijesuriya N, Podgorny A, Hecht AD, and Ray JCJ. (2021) Overlapping stimulons arising in response to divergent stresses in Escherichia coli. bioRxiv 2021.12.17.473201. https://doi.org/10.1101/2021.12.17.473201

This repo is a work in progress. 

## 1_trim_and_align_example/
Demonstration of trimming and aligning fastq files of bulk RNA-seq data. It can be run by calling the Snakemake file in the directory.

## 2_DE_analysis/
#### 1_DE_result_CSVs/
Folder containing differential expression gene (DEG) analysis results. 

- **counts_no_amp.csv** : Gene copy counts obtained from sequence alignment. 

- **pre_lac01/** : Folder containing differential expression analysis results with starvation as reference condition. 

- **pre_lac25/** : Folder containing differential expression analysis results with morderate lactose concentration as reference condition. 

- **pre_lac50/** : Folder containing differential expression analysis results with high lactose concentration as reference condition. 

#### 2_DE_analysis_scripts/
Script for performing differential expression analysis.

- **1-Preprocessing-PCA.ipynb** : Using PCA to remove sequence results that are significantly deviating from the cluster. 
- **2-Preprocessing-Generating control gene index file.ipynb** : Generating a set of control genes (typically householding genes, here those are non-regulated genes obtained from RegulonDB) were generated for `estimateSizeFactors`, a function called in the next step. 
- **3-DE-analysis.Rmd** : R notebook for differential expression analysis.
- **3-DE-analysis.html** : R notebook for differential expression analysis.
- **4-condition-clustering.ipynb** : Condition clustering using DEG log fold changes data. 

## 3_pathway_enrichment_analysis/
#### 1_pwy_enrichment_results/

- **lac01_vs_lac25.csv** : Pathway enrichment analysis results
- **lac50_vs_lac25.csv** : Pathway enrichment analysis results
- **PathEnrich_summary/**: metadata folder for pathway enrichment analysis.
- **PathEnrich_Tables/** : Folder for pathway enrichment analysis results compared between different conditions. 
  
#### 2_enrichment_analysis_scripts/
- **1-Pathway Enrichment Prepare.ipynb** : Save pathway IDs and their corresponding gene IDs into a file. 
- **2-Fgsea_pathways.Rmd** : Pathway enrichment analysis. 
- **3-Pathway Up-down percent, NES and Similarity.ipynb** : Calculating pathway enrichment related properties, such as regulatory similarities for enriched pathways in different conditions. 
- **4-Pathway enrichment comparison between conditions.ipynb**: Generating tables for enriched pathways in different conditions. 


## 4_annotations/
Annotation step is performed in preprocessing step, to bridge different databases, including the sequence alignment (this experiment), NCBI annotation and the Ecocyc annotation for the REL606 strain. The gene id is matched between databases is based on alignment score for the protein product sequence of the gene. 
