# Gene-Expression-Analysis-and-Pathway-Enrichment-with-DESeq2-and-EnrichR
Bioinformatics Approach for Gene Expression Analysis and Pathway Enrichment with DESeq2 and EnrichR

# Quick Recap:

RNA-Seq is a powerful method used in molecular biology to study gene expression. It is a technique that allows scientists to measure the amount of RNA molecules produced by cells or tissues under different conditions.

To understand RNA-Seq, we first need to know what RNA is. RNA stands for Ribonucleic Acid, and it is a molecule that plays an important role in the process of gene expression. RNA acts as a messenger between DNA (the genetic material of the cell) and proteins (the functional molecules that perform many tasks in the cell).

RNA-Seq works by isolating RNA from cells or tissues and converting it into a complementary DNA (cDNA) library. This cDNA library is then sequenced using high-throughput sequencing technologies, which generate millions of short reads that represent the RNA molecules present in the sample.

Once the reads are generated, bioinformaticians use specialized software to analyze them and map them back to the genome or transcriptome of the organism being studied. This mapping step allows scientists to identify which genes are expressed in the sample and how much RNA is being produced by each gene.

RNA-Seq can provide insights into a variety of biological processes, such as gene regulation, cellular differentiation, and disease states. It has revolutionized the field of molecular biology and is now widely used in research labs around the world.

# Scenario (Exemplary):

We started by obtaining raw sequencing reads in .fastq format from the sequencing facility. Before analyzing the data, we performed Quality Control (QC) checks to ensure the quality of the reads. These checks included assessing the distribution of read lengths, looking for the presence of adapter sequences, and checking for the presence of any low-quality reads.

Once we were satisfied with the quality of the reads, we used software such as STAR to map the reads to a transcriptome. We then used software such as SALMON to quantify the expression levels of each transcript, which gave us the number of reads that mapped to each transcript in the transcriptome, and then we used transcript counts to aggregate to gene level expression.

Now, our data consists of gene level counts for each sample, and we are expected to analyze it.

# We will do the following:

Firstly, to get a quick overview of the samples, we will use a technique called Principal Component Analysis (PCA). This technique allows us to visualize the similarities and differences between the samples based on their gene expression profiles. It was a useful way to check if the samples clustered together based on the expected biological variables (e.g., organ type or treatment condition).

Next, we want to compare gene expression between different conditions, such as different organs or treatment conditions. To do this, we use a statistical method called differential gene expression analysis. This method compares the expression of each gene between two or more conditions and identified genes that were expressed differently. We used software such as DESeq2 to perform differential gene expression analysis.

Finally, once we have identified the differentially expressed genes, we wante to understand which biological pathways or processes were affected. We do this using gene set enrichment analysis, which compared the differentially expressed genes to known sets of genes involved in specific biological pathways or processes. We use software such as EnrichR or GSEA to perform gene set enrichment analysis.

# Info on data: 

Sequencing libraries are created from total extracted mRNAs from different organs of healthy mice, after Cisplatin treatment or kept untreated.

# Info on condition:

Cisplatin is a chemotherapy drug commonly used to treat various types of cancer. It works by binding to DNA molecules in cancer cells and causing damage to the DNA strands. The damage caused by cisplatin can activate the cell's DNA repair mechanisms, including nucleotide excision repair (NER).

Nucleotide excision repair is a DNA repair mechanism that removes and replaces damaged nucleotides (the building blocks of DNA) in the DNA strand. NER is a multi-step process that involves the recognition and removal of damaged DNA, followed by the insertion of new nucleotides to repair the damage.

In the case of cisplatin treatment, the drug causes a specific type of DNA damage known as DNA crosslinking, where the two strands of DNA are covalently linked together. This type of DNA damage is particularly toxic and can lead to cell death if left unrepaired. NER plays a critical role in repairing this type of damage caused by cisplatin.

However, cancer cells can also develop resistance to cisplatin by altering their DNA repair mechanisms, including NER. Some cancer cells may overexpress certain proteins involved in NER, allowing them to repair the DNA damage caused by cisplatin more efficiently and survive the treatment.

Overall, the relationship between cisplatin and NER is complex and can have significant implications for the effectiveness of cisplatin chemotherapy in treating cancer. Understanding this relationship is important for developing new strategies to overcome cisplatin resistance and improve cancer treatment outcomes.

# RNA-seq Dataset Info

https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE117167

The modules we are going to use are as followed:

PyDESeq2: is for Differential gene expression analysis. It is Python implementation of DESeq2 library which is originally in R.

GSEApy: is a Python/Rust implementation of GSEA and wrapper for Enrichr. Enrichr contains most comprehensive and popular gene set libraries. We are going to use it for gene set enrichment over the selected libraries to see which biological pathways are enriched on up-regulated and down-regulated gene sets.

# clinical_df:

The index of this dataframe represents the sample IDs. It has two columns: "organ" and "condition". The "organ" column contains information about the organ from which each sample was taken. The "condition" column contains information about the treatment condition of each sample. The dataframe has 8 rows, indicating that there are 8 samples in total.

# counts_df:

The index of this dataframe represents the sample IDs, matching the samples in the clinical_df dataframe. The columns of this dataframe represent gene IDs. The values in the dataframe represent the gene-level counts for each sample and gene. Each row corresponds to a specific sample, and each column corresponds to a specific gene. The dataframe has 8 rows (matching the number of samples) and 25059 columns (representing different genes).

The Gene Ontology (GO) database is a widely used bioinformatics resource that provides a standardized vocabulary to annotate gene products in terms of their molecular function, cellular component, and biological process. It is organized into three major ontologies:

Molecular Function: This ontology describes the activities or tasks performed by gene products at the molecular level. It includes terms such as binding, catalysis, or receptor activity.

Cellular Component: This ontology represents the locations or structures within a cell where gene products are active. It includes terms such as nucleus, mitochondrion, or cytoskeleton.

Biological Process: This ontology describes the biological goals or objectives that gene products contribute to. It includes terms such as cell division, immune response, or signal transduction.

These three ontologies together provide a comprehensive framework to annotate and understand the functions and roles of genes and gene products.

The KEGG (Kyoto Encyclopedia of Genes and Genomes) pathway database is a collection of manually curated pathway maps that represent molecular interaction and reaction networks. It provides information about various biological pathways and their associated genes and molecules. KEGG pathways help in understanding the complex interactions and functions of genes in different biological processes, such as metabolic pathways, signaling pathways, and disease pathways.
