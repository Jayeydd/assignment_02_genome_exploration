# SUAN_assignment_02_genome_exploration
# Name: Suan, Jade Angela B.
 
# Activity Title: Basic Genome Structure and Sequence Analysis
# Course: BIO 300 – B Cell and Molecular Biology Laboratory

# Species: *Hipposideros armiger* (Great Roundleaf Bat)
# Accession Number: GCF_001890085.2 / ASM189008v1

# Objectives
To describe the structure and quality of a genome assembly using bioinformatic tools, analyze sequence length distribution, filter sequences, and identify potential protein-coding regions.

# Tools Used in Galaxy
1. **Compute sequence length** – Calculate base pair length for every scaffold
2. **Sort data** – Sort sequences by length (descending)
3. **Filter sequences by length** – Minimum length = 10,000 bp
4. **gfastats / Assembly Statistics** – N50, total length, GC content, N50/L50
5. **EMBOSS getorf** – Minimum ORF size = 300 bp; Standard genetic code; both strands

# Part 1 – Genome Download
- Source: **NCBI Assembly**
- Accession:**GCF_001890085.2**
- File:**GCF_001890085.2_ASM189008v1_genomic.fna.gz**
- Renamed in Galaxy to: **Hipposideros_armiger_genome_original.fna.gz**
- **Species**: *Hipposideros armiger*

# Part 2 — Assembly Statistics
- Tool: **gfastats**
​- Tool mode: Summary statistics generation
​- Report mode: Genome assembly statistics (--nstar-report)
​- Input file: **1: Hipposideros_armiger_genome_original.fna.gz**
​- Output renamed to: **Hipposideros_armiger_Assembly_Statistics_gfastats**

# Part 3 — Sequence-Length Structure
- Tool: *Compute sequence length*
​- Input file: **1: Hipposideros_armiger_genome_original.fna.gz**
​- Setting: "Strip fasta description from header?" = Yes
​- Output: **Compute sequence length on dataset 1**
​- Sorted using Galaxy's *Sort* tool (column 2, descending) to identify the top 5 longest sequences

# Part 4 — Length-Filtering Experiment
# Step 1: 
- Tool: *Filter sequences by length*
​- Input file: **1: Hipposideros_armiger_genome_original.fna.gz**
​- Parameter: minimum length = **10,000 bp (10 kb)**
​- Output renamed to: **Hipposideros_armiger_filtered_10kb**
​
# Step 2
​- Re-ran *gfastats* (same settings as Part 2) using input file: **6: Hipposideros_armiger_filtered_10kb**
​- Output renamed to: **Hipposideros_armiger_Filtered_10kb_Assembly_Statistics_gfastats**

Part 5 — Small ORF Exploration
# Step 1: 
- Tool: Filter Sequence by length
- Input file: **1: Hipposideros_armiger_genome_original.fna.gz**
- Filter using ID list from: "provided list"
​- My ID: **NW_017732759.1 (193,330 bp)**
- Output: "Positive matches only"
- Output renamed to: **14: Hipposideros_armiger_genome_original.fna uncompressed with matched ID**
​
# Step 2: 
- Tool: getorf
​- Input file:**14: Hipposideros_armiger_genome_original.fna uncompressed with matched ID**
​- Minimum nucleotide size of ORF to report: 300
​- What to output: Translation of regions between STOP codons
​- All START codons to code for Methionine: Yes
​- Circular sequence: No
​- Output: **Hipposideros_armiger_getorf.fasta**
​- Results: **173 ORFs found; longest ORF = 4,145 bp**

# Short Interpretation
The *Hipposideros armiger* genome is relatively contiguous with an N50 of 2.33 Mb, indicating good assembly quality. Filtering short sequences had minimal impact on total genome size, and GC content is typical for mammals. ORF prediction found many potential coding regions, though these remain predictions — further evidence is needed to confirm real genes.

