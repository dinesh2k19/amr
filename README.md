## Poultry manure bacterial isolates
Comprehending the existence of Antimicrobial Resistant Genes (ARGs) in poultry litter and bacteria harbouring them may provide insights into the potentiality of gene transmission into microbial communities of humans and opportunistic pathogens, highlighting the significance of a One-Health approach that considers the intricate relationships between humans, animals, and environmental health. The outcomes provide insights into the interaction of genes, phenotypes, and environmental variables in forming AMR profiles in poultry contexts, which has implications for agricultural settings and public health. 

## Graphical abstract 
![GA3](https://github.com/user-attachments/assets/91efe1da-b9bd-497e-ad3e-6c7365913e1e)

## Whole genome sequence (WGS) analysis workflow
WGS Analysis workflow includes sequence quality checking, quality control, taxonomy assignment, genome assembly, assembly quality assessment, assembled contig annotation, antimicrobial resistance, and taxonomy predictions. 

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
## Schematic
![Analysis-workflow](https://github.com/user-attachments/assets/c7b03cf9-e40c-4536-87d9-ee387682a003)

## Taxonomic identification using 16S ribosomal RNA gene sequencing 
MEGA 11 (Version 11.0.13) was employed for multiple sequence alignment, while the phylogenetic investigation was done using a maximum likelihood approach with 1000 bootstrap replicates. Using the iTOL server, aligned sequences were subsequently utilized to generate a circular phylogenetic tree (https://itol.embl.de/). All 16S rRNA gene sequences have been submitted to the NCBI public repository (GenBank Accession numbers PP053433-PP053445)

## Genome Analysis and Visualisation in Proksee Server 
Proksee (https://proksee.ca) provides users with a powerful, easy-to-use, and feature-rich system for assembling, annotating, analysing, and visualizing bacterial genomes. Proksee accepts Illumina sequence reads as compressed FASTQ files or pre-assembled contigs in raw, FASTA, or GenBank format. 

## The circular genome visualised below incidate the features of selected isolate (_Acinetobacter indicus_ BRLT-5) isolated from broiler litter samples: 

![BRLT5](https://github.com/user-attachments/assets/b77eb200-c45f-4059-9484-baa2de8dbd56)

## Whole genome SNP based phylogentic analysis  
SNP identification and phylogenetic analysis without genome alignment or the requirement for reference genomes (kSNP v3.0; Gardner et. al., 2015). The genomes were analysed using IPGA v1.09 server and tree visulised in the iTOL: Interactive Tree Of Life.

![kSNP-Phylogeny](https://github.com/user-attachments/assets/9698303c-a67d-4442-97fd-f13a57de4877)

BRLT13	100.00									
BRLT14	100.00	100.00								
BRLT15	65.61	65.61	100.00							
BRLT5	64.43	64.45	65.08	100.00						
BRLT8	80.32	80.27	65.61	64.49	100.00					
LYRL1	63.36	63.36	64.28	77.88	63.17	100.00				
LYRL2	67.38	67.40	67.96	63.83	67.34	62.71	100.00			
LYRL26	72.60	72.60	65.62	64.48	72.76	63.64	67.62	100.00		
LYRL28	65.27	64.73	64.28	63.73	64.81	63.01	64.30	65.45	100.00	
LYRL3	66.05	66.31	78.37	64.81	66.09	63.77	68.45	66.20	63.94	100.00
	BRLT13	BRLT14	BRLT15	BRLT5	BRLT8	LYRL1	LYRL2	LYRL26	LYRL28	LYRL3
![image](https://github.com/user-attachments/assets/e25c90dd-667e-450e-9c58-79685c1eae27)

## Citation

Tripathi, Animesh, Anjali Jaiswal, Dinesh Kumar, Ramesh Pandit, Damer Blake, Fiona Tomley, Madhvi Joshi, Chaitanya G. Joshi, and Suresh Kumar Dubey. "Release of antimicrobial resistance genes from poultry manure into agro-ecosystems assessed using bacterial genome sequencing.

## Raw Data Availaility 

Sequence Information: Accession numbers (PP053433-PP053445) of 16S rDNA nucleotide sequences of selected poultry litter bacterial isolates used in this study are available in National Centre for Biotechnology Information (NCBI) gene database and the raw reads generated through WGS has been submitted to the NCBI under Sequence Read Archive (SRA) submission with Bio-project accession number PRJNA1058239.
