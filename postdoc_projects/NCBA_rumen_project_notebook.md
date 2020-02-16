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

[github page](https://github.com/TheNoyesLab/NCBA_rumen_project)



## Current Tasks

  1. Write more tasks!
  
## Milestones

![Milestones]( "timeline")

| Status | Milestones| Date  | Description  |
| -------| ------------- |:------------:| ------------|
| | 1      | date  | short description |

    
## Monthly project status

- October 2019:
  * Goal: 
  * Notes:
    * 
  * Accomplished: 
    * 


***
## Lab journal
---------------------------------------------------------------------------------------------------------------
### 2019-1-15
* The Kraken 2 run was completed
```
nextflow run minor_kraken2.nf -profile local_MSI -w /scratch.global/run_rumen_capstone/rumen_work_dir --threads 4 --reads '/home/noyes046/shared/seq_data/rumen_project_nonhost_reads/*.non.host.R{1,2}.fastq.gz' --output /scratch.global/run_rumen_capstone/Rumen_kraken_results --kraken_db /home/noyes046/shared/databases/kraken2_databases/Rumen_kraken_v2_Nov2019/ -resume
```

* Now, run with MEGARes v2
```
nextflow run minor_only_AMR.nf -profile local_MSI -w /scratch.global/run_rumen_capstone/rumen_work_dir --threads 5 --reads '/home/noyes046/shared/seq_data/rumen_project_nonhost_reads/*.non.host.R{1,2}.fastq.gz' --output /scratch.global/run_rumen_capstone/Rumen_MEGARes_results -resume
```

### 2019-1-14
* Non-host reads were done and I moved everything to Noelle's server to ensure they don't get deleted on accident

### 2019-1-12
* Re-started pipeline to create non-host reads. 
  * Fixed issue where some samples had the same SRA name, even though they were from different projects and were different files sizes.
