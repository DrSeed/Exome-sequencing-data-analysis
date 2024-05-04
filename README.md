# Exome-sequencing-data-analysis


NGS Data Processing Pipeline
This pipeline automates the process of quality control, read mapping, and variant calling for next-generation sequencing (NGS) data. It utilizes a suite of well-established bioinformatics tools to process FASTQ files through to variant calling.

Prerequisites
Before running this script, ensure the following tools are installed on your system:

FastQC: For quality control checks on raw sequence data.
MultiQC: For aggregating results from bioinformatics analyses into a single report.
BWA (Burrows-Wheeler Aligner): For aligning sequence reads against a reference genome.
Samtools: For manipulating alignments in the SAM format.
FreeBayes: For variant calling.
Bcftools: For variant processing and filtering.
These tools must be in your system's PATH to be recognized by the script.

Installation
You can install most of these tools via Bioconda. For example:
conda install -c bioconda fastqc multiqc bwa samtools freebayes bcftools

Directory Structure
Before running the script, ensure your directory structure is organized as follows:

/path/to/your/directory/
│
├── fastq_files/      # Directory containing all .fq.gz FASTQ files
├── hg19.fa           # Reference genome file
│
├── fastqc_results/   # Output directory for FastQC results
├── multiqc_report/   # Output directory for MultiQC aggregation report
├── bam_files/        # Output directory for BAM files and their indices
└── vcf_files/        # Output directory for VCF files


Usage
Modify the Script:
Open the script in a text editor.
Update the WORK_DIR variable to point to the base directory of your project.

Run the Script:
Make the script executable with chmod +x script_name.sh.
Execute the script by running ./script_name.sh from your terminal.

Script Workflow
Step 1: Quality control with FastQC.
Step 2: Aggregate FastQC reports with MultiQC.
Step 3: Index the reference genome with BWA.
Step 4: Map reads, sort, fix mates, mark duplicates, and index BAM files with BWA and Samtools.
Step 5: Call variants using FreeBayes.
Step 6: Normalize and filter variants using Bcftools.

Output
Quality control reports in fastqc_results/ and multiqc_report/.
Sorted and deduplicated BAM files in bam_files/.
Variant calls in VCF format located in vcf_files/.
