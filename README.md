## Whole genome sequence (WGS) data analysis pipeline

WGS Analysis workflow includes sequence quality checking, quality control, taxonomy assignment, genome assembly, assembly quality assessment, assembled contig annotation, antimicrobial resistance, and taxonomy prediciton. The pipeline is built using Nextflow, a workflow tool to run tasks across multiple compute infrastructures in a very portable manner. It uses Docker/Singularity containers making installation trivial and results highly reproducible.

![image](https://github.com/user-attachments/assets/e15f0370-7955-4c5f-a076-ca5d38423f28)


## Poultry manure bacterial isolates

Comprehending the existence of Antimicrobial Resistant Genes (ARGs) in poultry litter and bacteria harbouring them may provide insights into the potentiality of gene transmission into microbial communities of humans and opportunistic pathogens, highlighting the significance of a One-Health approach that considers the intricate relationships between humans, animals, and environmental health. The outcomes provide insights into the interaction of genes, phenotypes, and environmental variables in forming AMR profiles in poultry contexts, which has implications for agricultural settings and public health. 

## Graphical abstract 
![GA3](https://github.com/user-attachments/assets/91efe1da-b9bd-497e-ad3e-6c7365913e1e)

## Analysis steps 
- Raw sequence quality assessment using FASTQC Toolkit 
- Adapter trimming and low quality filtering using PrinSeq-Lite v0.20.4 (Parameters: -min_qual_mean 30 --min_len 50 -ns_max_n 0) and reports using MultiQC  
- Bacterial genome assembly using Unicycler 
- Genome quality check and statistics using CheckM and QUAST 
- Genome based taxonomy assignment using (GTDB-Tk) and multi-locus typing using PubMLST server (https://pubmlst.org/)
- Gene prediction using Prokka and annotation of genes among different subsystems utilizing the SEED and RAST servers (https://rast.nmpdr.org/)    
- Idenitfication of the Antimicrobial Resistant Genes (ARGs) using CARD Database (https://card.mcmaster.ca/)
- Prediction of phage sequences using PHASTER (PHAge Search Tool Enhanced Release) server (https://phaster.ca/)
- Analysis of virulence factors using VFDB server version 2022 (http://www.mgc.ac.cn/cgi-bin/VFs/v5/main.cgi) 
- Genomic feature visulisation using Proksee server (https://proksee.ca/)

![Analysis-workflow](https://github.com/user-attachments/assets/719a7353-a246-48ae-8822-2a143f12aa72)


## Genome Analysis and Visualisation in Proksee Server 
Proksee (https://proksee.ca) provides users with a powerful, easy-to-use, and feature-rich system for assembling, annotating, analysing, and visualizing bacterial genomes. Proksee accepts Illumina sequence reads as compressed FASTQ files or pre-assembled contigs in raw, FASTA, or GenBank format. 

## The circular genome visualised below incidate the features of selected isolate (_Acinetobacter indicus_ BRLT-5) isolated from broiler litter samples: 

![BRLT5](https://github.com/user-attachments/assets/b77eb200-c45f-4059-9484-baa2de8dbd56)


## Citation


Tripathi, Animesh, Anjali Jaiswal, Dinesh Kumar, Ramesh Pandit, Damer Blake, Fiona Tomley, Madhvi Joshi, Chaitanya G. Joshi, and Suresh Kumar Dubey. "Release of antimicrobial resistance genes from poultry manure into agro-ecosystems assessed using bacterial genome sequencing.
