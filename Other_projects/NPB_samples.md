Title of Proposal:
------------

Project summary
* Sample data release and new location:
```
# Data release
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


# New location
/home/noyes046/shared/seq_data/NPB_samples/
```



Table of Contents
-----
* [Main project resources](#main-project-resources)
* [Current tasks](#current-tasks)
* [Milestones](#milestones)
* [Monthly project status](#monthly-project-status)
* [Lab Journal](#lab-journal)

## Main project resources

[github page](https://github.com/EnriqueDoster/project_lab_notebooks)



## Current Tasks

  1. Write more tasks!
  
## Milestones

![Milestones]( "timeline")

| Status | Milestones| Date  | Description  |
| -------| ------------- |:------------:| ------------|
| | 1      | date  | short description |

    
## Monthly project status

- Month YEAR:
  * Goal: 
  * Notes:
    * 
  * Accomplished: 
    * 


***
## Lab journal
---------------------------------------------------------------------------------------------------------------

### 2020-04-12
* Run AMR++ on all samples, using cn4201 computing node

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


