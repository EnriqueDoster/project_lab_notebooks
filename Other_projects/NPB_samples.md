Title of Proposal:
------------

How to access on MSI

```
ssh tanxx606@login.msi.umn.edu
ssh mesabi

# Main lab directories:
/home/noyes046/shared/ 

# Currently, the NPB samples and results are in a temporary allocation here:
/tempalloc/noyes042/NPB_samples/NPB_MEGARes_kraken_output

# Two computing node options if you want to run something. Use "screen" or "nohub" to run commands without the scheduler.
ssh cn4201 # Smaller, main computing cluster (no qsub)
ssh cn1107 # Large computing cluster (no qsub)
```

Raw sample data release and new location:
```
# Data release was as total of 232 samples (Stored here for 5 years)
# 47 samples
/home/noyes046/data_release/umgc/novaseq/200305_A00223_0336_AH2WFWDSXY/Noyes_Project_011_Pool_1
# 46
/home/noyes046/data_release/umgc/novaseq/200305_A00223_0336_AH2WFWDSXY/Noyes_Project_011_Pool_5
# 47
/home/noyes046/data_release/umgc/novaseq/200325_A00223_0346_BH75VWDSXY/Noyes_Project_011_Pool_2
# 46
/home/noyes046/data_release/umgc/novaseq/200226_A00223_0330_BH2WT2DSXY/Noyes_Project_011_Pool_3
# 46
/home/noyes046/data_release/umgc/novaseq/200226_A00223_0330_BH2WT2DSXY/Noyes_Project_011_Pool_4

# New location with symlinks
# 216 NPB samples, 16 amazonian k9 samples
/tempalloc/noyes042/NPB_samples/samples/
```

## For further analysis, use these nonhost samples:
```
# Do any further analysis with these samples
/tempalloc/noyes042/NPB_samples/NPB_nonhost_sus_scrofa/NonHostReads/
```

## For statistical analysis of the microbiome and resistome, use the results here:
```
/tempalloc/noyes042/NPB_samples/NPB_MEGARes_kraken_output

# I also moved a copy of the count tables to this directory for storage:
/home/noyes046/shared/projects/NPB_resistome_followon/NPB_MEGARes_results/
```


Table of Contents
-----
* [Main project resources](#main-project-resources)
* [Current tasks](#current-tasks)
* [Milestones](#milestones)
* [Lab Journal](#lab-journal)

## Main project resources

[github page](https://github.com/EnriqueDoster/project_lab_notebooks)



## Current Tasks

  1. Running kraken2 and alignment to MEGARes with bwa (2020-05-09)
  
## Milestones
 * I accidentally used the bovine genome with the AMR++ pipeline so I had to re-start the analysis using the swine genome.
 * I ran the host DNA removal step with the swine genome and samples can be found here: /tempalloc/noyes042/NPB_samples/NPB_nonhost_sus_scrofa/NonHostReads/
 



***
## Lab journal
---------------------------------------------------------------------------------------------------------------
### 2020-


### 2020-05-09
* The current run was going too slow because I had included the "dedup" step with samtools (taking a couple of hours per sample). Instead, I removed those extra steps and added kraken:
```
nextflow run minor_AMR_and_kraken.nf -profile local_MSI -w /tempalloc/noyes042/NPB_samples/work_AMR_kraken --threads 6 --reads '/tempalloc/noyes042/NPB_samples/NPB_nonhost_sus_scrofa/NonHostReads/*.non.host.R{1,2}.fastq.gz' --output /tempalloc/noyes042/NPB_samples/NPB_MEGARes_kraken_output --kraken_db /home/noyes046/shared/databases/kraken2_databases/Rumen_kraken_v2_Nov2019/ -resume -with-report MEGARes_kraken.report -with-trace -with-timeline
```

### 2020-04-30
```
# /tempalloc/noyes042/NPB_samples

nextflow run minor_only_AMR.nf -profile local_MSI -w /tempalloc/noyes042/NPB_samples/work_AMR --threads 6 --reads '/tempalloc/noyes042/NPB_samples/NPB_nonhost_sus_scrofa/NonHostReads/*.non.host.R{1,2}.fastq.gz' --output /tempalloc/noyes042/NPB_samples/NPB_MEGARes_sus_scrofa --host /panfs/roc/risdb/genomes/Sus_scrofa/Sscrofa10.2/seq/Sscrofa10.2.fa -resume -with-report MEGARes.report -with-trace -with-timeline

```




### 2020-04-12
* Run pipeline to get nonhost reads for all samples, using cn4201 computing node

```
# /tempalloc/noyes042/NPB_samples

nextflow run minor_to_nonhost.nf -profile local_MSI -w /tempalloc/noyes042/NPB_samples/work_npb_dir_nonhost2 --threads 6 --reads '/tempalloc/noyes042/NPB_samples/samples/NPB*_R{1,2}_001.fastq.gz' --output /tempalloc/noyes042/NPB_samples/NPB_nonhost_sus_scrofa --host /panfs/roc/risdb/genomes/Sus_scrofa/Sscrofa10.2/seq/Sscrofa10.2.fa --adapters /panfs/roc/msisoft/trimmomatic/0.33/adapters/all_illumina_adapters.fa --kraken_db /home/noyes046/shared/databases/kraken2_databases/Rumen_kraken_v2_Nov2019/ -resume -with-report non_host_run.report -with-trace -with-timeline

```


```
cd /tempalloc/noyes042/NPB_samples
mkdir samples
cd samples/
ln -s /home/noyes046/data_release/umgc/novaseq/200305_A00223_0336_AH2WFWDSXY/Noyes_Project_011_Pool_1/*.gz .
ln -s /home/noyes046/data_release/umgc/novaseq/200305_A00223_0336_AH2WFWDSXY/Noyes_Project_011_Pool_5/*.gz .
ln -s /home/noyes046/data_release/umgc/novaseq/200325_A00223_0346_BH75VWDSXY/Noyes_Project_011_Pool_2/*.gz .
ln -s /home/noyes046/data_release/umgc/novaseq/200226_A00223_0330_BH2WT2DSXY/Noyes_Project_011_Pool_4/*.gz .
ln -s /home/noyes046/data_release/umgc/novaseq/200226_A00223_0330_BH2WT2DSXY/Noyes_Project_011_Pool_3/*.gz .

```




### 2020-03-18
 
* Run AMR++, only on four lanes whle we wait for the remaining lane

```
# Make symlinks to "/scratch.global/test_AMR/NPB_samples"

nextflow run main_AmrPlusPlus_v2_withKraken.nf -profile local_MSI -w /scratch.global/test_AMR/work_npb_dir --threads 2 --kraken_db /home/noyes046/shared/databases/kraken2_databases/Rumen_kraken_v2_Nov2019/ --reads '/scratch.global/test_AMR/NPB_samples/*_R{1,2}_001.fastq.gz' --host '/panfs/roc/risdb/genomes/Bos_taurus/Bos_taurus_UMD_3.1/bwa/Bos_taurus_UMD_3.1.fa' --output /scratch.global/test_AMR/NPB_AMR++_results -with-report NPB_4_lanes.report -with-trace -with-timeline
```


