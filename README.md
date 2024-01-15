# Bioinformatics-Resources-Project-2023

**Professor Alessandro Romanel**

**Academic Year 2022/2023**

***Group members***

- Computer Science (CS) Master student: Camilla Pelagalli (MAT. 238775)
- Quantitative and Computational Biology (QCB) Master student: Alessandro Salvatore Raho (MAT. 229323)

The group members equally contributed to the project realization.

***Project instructions***

Execute the following tasks and and comment the code with the results you obtain. The
code you generate should be provided as R script. Alternatively, you can use frameworks
like R markdown to provide both the report and the code together.

Select one among the RData files available representing RNA-seq count data extracted
from different cancer datasets from the Cancer Genome Atlas (TCGA). From the original
TCGA data 50 cases (tumor samples) and 50 controls (normal samples) were randomly
selected.

**1.** Load the RData file. The following three data-frames are available:
  - **a)** raw_counts_df = contains the raw RNA-seq counts
  - **b)** c_anno_df = contains sample name and condition (case and control)
  - **c)** r_ anno_df = contains the ENSEMBL genes ids, the length of the genes and the genes symbols

**2.** Update raw_count_df and r_anno_df extracting only protein coding genes.
  - **a)** Use biomaRt package to retrieve the needed information
  - **b)** Next tasks should use the new data-frames you have created

**3.** Perform differential expression analysis using edgeR package and select up- and
down-regulated genes using a p-value cutoff of 0.01, a log fold change ratio >1.5 for
up-regulated genes and < (-1.5) for down-regulated genes and a log CPM > 1. Relax
the thresholds if no or few results are available.
  - **a)** Use the workflow we developed during the course
  - **b)** Filter raw counts data retaining only genes with a raw count >20 in at least 5 Cases or 5 Control samples
  - **c)** Create a volcano plot of your results
  - **d)** Create an annotated heatmap focusing only on up- and downregulated genes

**4.** Perform gene set enrichment analysis using clusterProfiler R package.
  - **a)** Perform both GO (BP and MF) and WP analysis
  - **b)** Report the top 10 enriched GO terms and the top 10 enriched WP pathways resulting from both up- and down-regulated gene lists

**5.** Use the pathview R package to visualize one pathway you find enriched using the
upregulated gene list.

**6.** Identify which transcription factors (TFs) have enriched scores in the promoters of all
up-regulated (or down-regulated if you prefer) genes.
  - **a)** use a window of 500 nucleotides upstream each gene

**7.** Select one among the top enriched TFs, compute the empirical distributions of scores
for all PWMs that you find in MotifDB for the selected TF and determine for all of
them the distribution (log2) threshold cutoff at 99.75%.

**8.** Identify which up-regulated (or down-regulated depending on the choice you made
at point 7) genes have a region in their promoter (defined as previously) with binding
scores above the computed thresholds for any of the previously selected PWMs.
  - **a)** Use pattern matching as done during the course

**9.** Use STRING database to find PPI interactions among differentially expressed genes
and export the network in TSV format.

**10.** Import the network in R and using igraph package and identify and plot the largest
connected component. 
