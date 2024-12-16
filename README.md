## Poultry manure bacterial isolates
- Comprehending the existence of Antimicrobial Resistant Genes (ARGs) in poultry litter and bacteria harbouring them may provide insights into the potentiality of gene transmission into microbial communities of humans and opportunistic pathogens, highlighting the significance of a One-Health approach that considers the intricate relationships between humans, animals, and environmental health.
- The outcomes provide insights into the interaction of genes, phenotypes, and environmental variables in forming AMR profiles in poultry contexts, which has implications for agricultural settings and public health. 

## Graphical abstract 
![GA3](https://github.com/user-attachments/assets/91efe1da-b9bd-497e-ad3e-6c7365913e1e)

## Whole genome sequence (WGS) analysis workflow
- WGS Analysis workflow includes sequence quality checking, quality control, taxonomy assignment, genome assembly, assembly quality assessment, assembled contig annotation, antimicrobial resistance, and taxonomy predictions. 

## Setup Conda Environment for workflow management
- Miniconda is a lightweight version of Anaconda that includes only Conda and its dependencies. If you need a full package, install Anaconda instead of Miniconda. For detailed instructions, please refer to https://docs.anaconda.com/anaconda/install/ 

## Analysis workflow steps 
- We created a conda environment named `env_amr` and installed all the required packages, dependencies were installed and configured in this environment to execute the analysis workflow steps as per following commands. 
- Raw sequence quality assessment using FASTQC Toolkit (https://www.bioinformatics.babraham.ac.uk/projects/fastqc/)
```bash
$ conda create -n env_amr -c bioconda fastqc
```

```bash
$ conda activate env_amr
```

```bash
$ fastqc -o /fastqc_output -t 64 /data/*.fastq.gz
```
 
## Adapter trimming and low quality filtering using PrinSeq-Lite v0.20.4 and reports using MultiQC version 1.20  
```bash
$ perl prinseq-lite.pl -fastq Sample1_R1.fastq.gz -fastq2 Sample1_R2.fastq.gz -min_qual_mean 30 -min_len 50 -ns_max_n 0
```
```bash
$ fastp -i Sample1_R1.fastq.gz -I Sample1_R2.fastq.gz -o S1_clean_R1.fastq.gz -O S1_clean_R2.fastq.gz -h S1_fastp_report.html -j S1_fastp_report.json --low_complexity_filter --cut_mean_quality 30 --min_length 50 --thread 16
```
## Generate MultiQC report
```bash
$ multiqc . -o multiqc_report/
```
## Genome Assembly
- Illumina Paired-end trimmed and filtered reads were assembled using Unicycler with the command line options at local server. Unicycler is an assembly pipeline for bacterial genomes.
```bash
$ unicycler -1 S1_filt_reads_R1.fastq.gz -2 S1_filt_reads_R2.fastq.gz -o output_dir --assembly_method bold
```
## Genome quality check and statistics using CheckM v2 and QUality ASsessment Tool (QUAST) v5.0.2 
- We obtained the genomic assembly statistics using CheckM v2 for all the samples and obtained the QUAST reports
```bash
$ checkm lineage_wf -x fasta output_dir/ checkm_report/
```

```bash
$ quast -i genome_dir/assembly.fasta -o quast_report/ --threads 64 --m bacterial
```

## Genome based taxonomy assignment using (GTDB-Tk) and multi-locus sequence typing (MLST) using PubMLST server (https://pubmlst.org/)
- The bacterial genomes were assigned taxonomy using Genome based taxonomy database and processed for the multi-locus strain typing by PubMLST server.

```bash
$ gtdbtk classify_wf --genome_dir genome_dir/ --output_dir gtdbtk_report/ --cpus 64 
```
## Gene prediction using Prokka and annotation 
- Subsystems utilizing the SEED Servers (http://www.theseed.org/servers) and Rapid Annotation using Subsystem Technology (RAST) Server (https://rast.nmpdr.org/) and eggNOG-mapper v2 assisted with precomputed eggNOG v5.0 clusters were used to perform functional annotation.       

## Idenitfication of the Antimicrobial Resistant Genes (ARGs) 
- The ARGs were identified using the Resistance Gene Identifier (RGI) from respective bacterial genome assembly nucleotide sequences based on homology and SNP models using Comprehensive Antibiotic Resistance Database (CARD) (https://card.mcmaster.ca/) 

## Prediction of phage sequences using PHASTER (PHAge Search Tool Enhanced Release) server (https://phaster.ca/). 
- PHASTER web server was used for the rapid identification and annotation of prophage sequences within bacterial genome assemblies. 

## Analysis of virulence factors 
- Analysis was performed using VFDB server version 2022 (http://www.mgc.ac.cn/cgi-bin/VFs/v5/main.cgi)

## Analysis of Integrative and conjugative elements (ICEs), integrative and mobilizable elements (IMEs), and cis-mobilizable elements (CIMEs) 
- ICEfinder server was used (https://bioinfo-mml.sjtu.edu.cn/ICEfinder/ICEfinder.html) for the detection of ICEs/IMEs of bacterial genomes.

## The heavy metal resistant genes (HMRGs) analysis
- The HMRGs sequences were downloaded to create a custom database and analysed using the Hidden Markov models (HMMs) profile protein family (PF13801: Heavy-metal resistance) https://www.ebi.ac.uk/interpro/entry/pfam/PF13801/

## Genomic feature visulisation using Proksee server (https://proksee.ca/). Proksee is a suite of command line tools for performing assembly and evaluation of microbial genomes.
- Proksee server system was used for genome assembly, annotation and visualization, featuring interactive circular and linear genome maps for the respective bacterial genome assemblies, and ARGs

## Schematic
![Analysis-workflow](https://github.com/user-attachments/assets/c7b03cf9-e40c-4536-87d9-ee387682a003)

## Taxonomic identification using 16S ribosomal RNA gene sequencing 
MEGA 11 (Version 11.0.13) was employed for multiple sequence alignment, while the phylogenetic investigation was done using a maximum likelihood approach with 1000 bootstrap replicates. Using the iTOL server, aligned sequences were subsequently utilized to generate a circular phylogenetic tree (https://itol.embl.de/). All 16S rRNA gene sequences have been submitted to the NCBI public repository (GenBank Accession numbers PP053433-PP053445)

## Genome Analysis and Visualisation in Proksee Server 
Proksee (https://proksee.ca) provides users with a powerful, easy-to-use, and feature-rich system for assembling, annotating, analysing, and visualizing bacterial genomes. Proksee accepts Illumina sequence reads as compressed FASTQ files or pre-assembled contigs in raw, FASTA, or GenBank format. 

## The circular genome visualised below incidate the features of selected isolate (_Acinetobacter indicus_ BRLT-5) isolated from broiler litter samples: 

![BRLT5](https://github.com/user-attachments/assets/b77eb200-c45f-4059-9484-baa2de8dbd56)


## Raw Data Availaility 

Accession numbers (PP053433-PP053445) of 16S rRNA nucleotide sequences of selected poultry litter bacterial isolates used in this study are available in National Centre for Biotechnology Information (NCBI) database and the raw reads generated through WGS has been submitted to the NCBI under Sequence Read Archive (SRA) submission with Bio-project accession number PRJNA1058239.

## Funding Information

This research work was supported by Gujarat Biotechnology Research Centre (GBRC), Department of Science and Technology (DST), Government of Gujarat, Gandhinagar, India. Authors would like to gratefully acknowledge the UKRI-GCRF One Health Poultry Hub (OHPH), UK for supporting research activity. Department of Biotechnology (DBT), Government of India, New Delhi gratefully acknowledged for financial assistance to Animesh Tripathi in the form of Junior Research Fellow (DBTHRDPMU/JRF/BET-20/2020/AL/293).


## Citation

Tripathi, Animesh, Anjali Jaiswal, Dinesh Kumar, Ramesh Pandit, Damer Blake, Fiona Tomley, Madhvi Joshi, Chaitanya G. Joshi, and Suresh Kumar Dubey. "High occurrence of antimicrobial resistance genes in bacteria isolated from poultry manure assessed using bacterial genome sequencing.
