Title of Proposal:
------------

Project summary


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


### 2020-04-18
* Run was completed for k9 samples. Results were transferred to: /home/noyes046/shared/projects/Amazonian_k9_project/

```
4.5T    ./work_k9
3.4T    ./amazonian_k9_AMR++_results
7.8T    .
```

### 2020-03-14

* Also ran the CF samples
```
cat /panfs/roc/risdb/genomes/Canis_lupus/canFam3/seq/canFam3.fa /panfs/roc/groups/11/noyes046/shared/genomes/eukaryotic_genomes/Cassava/GCF_001659605.1_Manihot_esculenta_v6_genomic.fna > combined_k9_cassava.fa


/tempalloc/noyes042/amazonian_k9
nextflow run main_AmrPlusPlus_v2_withKraken.nf -profile local_MSI -w /tempalloc/noyes042/amazonian_k9/work_k9 --threads 10 --kraken_db /home/noyes046/shared/databases/kraken2_databases/Rumen_kraken_v2_Nov2019/ --reads '/scratch.global/test_AMR/NPB_samples/CF*_R{1,2}_001.fastq.gz' --host '/tempalloc/noyes042/amazonian_k9/combined_k9_cassava.fa' --output /tempalloc/noyes042/amazonian_k9/amazonian_k9_AMR++_results -with-report CF_samples.report -with-trace -with-timeline

```
