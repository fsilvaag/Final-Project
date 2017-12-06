

# Title: Zygotic Genome Activation(ZGA) Occurs Shortly After Fertilization in Maize

This paper is about zygotic genome activation in maize and the authors gave an adequate introduction into the topic. 
In summary, ZGA occurs gradually with the initial steps of zygote and embryo development being primarily maternally controlled whereas the subsequent steps are governed by the zygotic genome. To characterize the start of ZGA at the whole-genome level, it is essential to determine the transcriptome profiles of both gametes and to identify de novo generated transcripts from the zygotic genome. For this reason, an experiment was set up using maize as a model plant, to investigate the timing of zygote development. In the experiment, the investigators manually isolated gametes (egg and sperm), zygotes (12 and 24 HAF) and daughter cells (Apical and basal) from which they generated RNA-seq data. They then investigated their transcriptome dynamics after fertilization. Finally, they compared the transcriptome from maize and rice with the goal of exploring how the cell cycle, chromatin and auxin pathways were regulated after fertilization. They were able to identify transcription factors, and receptor-like kinase genes that were associated with the various cell types and zygotic stages. From the analysis, they found out that:

1.	ZGA in maize occurs shortly after fertilization and that it involves about 10% of the genome being activated in a highly dynamic pattern. 

2.	Genes encoding transcriptional regulators of various families are activated shortly after fertilization.

3.	Chromatin assembly is strongly modified after fertilization, the egg cell is primed to activate the translational machinery, and that hormones likely play a minor role in the initial steps of early embryo development in maize. 

# Technical details of replication

We download the RNA-seq data provided in the paper from NCBI’s website. To do that, we used the SRA toolkit to convert the file from a SRA format to a fastq format. We then assessed the quality of the RNA-Seq data using the FASTQC program. The author of the paper used the cutadapt (ver.1.13; Martin, 2011) program to remove primer contamination, which we were not able to make it work. We then did size and quality trimming using Trimmomatic (ver. 0.32 (Am et al., 2014)), as the authors of the paper did.  We then aligned the trimmed reads to the maize genome (AGPv3, INSEC Assembly GCA_000005005.5, release 23, ftp://ftp.ensemblgenomes.org/pub/plants/) using STAR (Dobin et al., 2013). We did not identify duplicate reads, while the authors of the paper did that using the picard MarkDuplicates. We then counted the number of reads using featureCounts from the Rsubread R-library (Liao et al., 2014), using annotation information supplied by Gramene release 5b+  (http://ftp.gramene.org/maizesequence.org/release5b+/zea_mays.protein_coding.gff). With the count data we obtained, we did a differential expression analysis with DESeq2 (Love et al., 2014). All cell type comparisons were performed and corrected for multiple testing across all genes and cell type using False Discovery Rate (FDR –and Hochberg, 1995). Genes with a log2FoldChange>1 and FDR <0.05 were considered significant differentially expressed. Replication of the figures shown in the paper were done using R, JMP and Excel. The code for the replication of each figure is located inside each Figure’s folder. The data used for the replication of the figures was either the data we generated, or the summary data provided in the supplementary section of the paper.  
 




