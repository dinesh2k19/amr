## Poultry manure bacterial isolates
Comprehending the existence of Antimicrobial Resistant Genes (ARGs) in poultry litter and bacteria harbouring them may provide insights into the potentiality of gene transmission into microbial communities of humans and opportunistic pathogens, highlighting the significance of a One-Health approach that considers the intricate relationships between humans, animals, and environmental health. The outcomes provide insights into the interaction of genes, phenotypes, and environmental variables in forming AMR profiles in poultry contexts, which has implications for agricultural settings and public health. 

## Graphical abstract 
![GA3](https://github.com/user-attachments/assets/91efe1da-b9bd-497e-ad3e-6c7365913e1e)

## Whole genome sequence (WGS) data analysis workflow
WGS Analysis workflow includes sequence quality checking, quality control, taxonomy assignment, genome assembly, assembly quality assessment, assembled contig annotation, antimicrobial resistance, and taxonomy prediciton. The pipeline is built using Nextflow, a workflow tool to run tasks across multiple compute infrastructures in a very portable manner. It uses Docker/Singularity containers making installation trivial and results highly reproducible.

## Taxonomic identification using 16S ribosomal RNA gene sequencing 
MEGA 11 (Version 11.0.13) was employed for multiple sequence alignment, while the phylogenetic investigation was done using a maximum likelihood approach with 1000 bootstrap replicates. Using the iTOL server, aligned sequences were subsequently utilized to generate a circular phylogenetic tree (https://itol.embl.de/).

## All 16S rRNA gene sequences have been submitted to the NCBI public repository (GenBank Accession numbers PP053433-PP053445)

## Analysis steps 
- Raw sequence quality assessment using FASTQC Toolkit (https://www.bioinformatics.babraham.ac.uk/projects/fastqc/)
- Adapter trimming and low quality filtering using PrinSeq-Lite v0.20.4 (Parameters: -min_qual_mean 30 --min_len 50 -ns_max_n 0) and reports using MultiQC version 1.20  
- Bacterial genome assembly using Unicycler (unicycler -1 short_reads_1.fastq.gz -2 short_reads_2.fastq.gz -o output_dir)
- Genome quality check and statistics using CheckM v2 and QUality ASsessment Tool (QUAST) 
- Genome based taxonomy assignment using (GTDB-Tk) and multi-locus typing using PubMLST server (https://pubmlst.org/)
- Gene prediction using Prokka and annotation of genes among different subsystems utilizing the SEED and RAST servers (https://rast.nmpdr.org/)    
- Idenitfication of the Antimicrobial Resistant Genes (ARGs) using CARD Database (https://card.mcmaster.ca/)
- Prediction of phage sequences using PHASTER (PHAge Search Tool Enhanced Release) server (https://phaster.ca/)
- Analysis of virulence factors using VFDB server version 2022 (http://www.mgc.ac.cn/cgi-bin/VFs/v5/main.cgi) 
- Genomic feature visulisation using Proksee server (https://proksee.ca/)

![Analysis-workflow](https://github.com/user-attachments/assets/c7b03cf9-e40c-4536-87d9-ee387682a003)


## Genome Analysis and Visualisation in Proksee Server 
Proksee (https://proksee.ca) provides users with a powerful, easy-to-use, and feature-rich system for assembling, annotating, analysing, and visualizing bacterial genomes. Proksee accepts Illumina sequence reads as compressed FASTQ files or pre-assembled contigs in raw, FASTA, or GenBank format. 

## The circular genome visualised below incidate the features of selected isolate (_Acinetobacter indicus_ BRLT-5) isolated from broiler litter samples: 

![BRLT5](https://github.com/user-attachments/assets/b77eb200-c45f-4059-9484-baa2de8dbd56)


## Citation


Tripathi, Animesh, Anjali Jaiswal, Dinesh Kumar, Ramesh Pandit, Damer Blake, Fiona Tomley, Madhvi Joshi, Chaitanya G. Joshi, and Suresh Kumar Dubey. "Release of antimicrobial resistance genes from poultry manure into agro-ecosystems assessed using bacterial genome sequencing.
