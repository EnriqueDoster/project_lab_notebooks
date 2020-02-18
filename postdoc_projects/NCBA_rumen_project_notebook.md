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

- February 2020:
  * Goal: Get resistome and microbiome results for Blake
  * Notes:
    * Fixed the issue with identical sample names and re-started the run. Had some issues with Singularity that caused the pipeline to fail.
  * Accomplished:
    * Finished running 
- January 2020:
  * Goal: Get resistome and microbiome results for Blake
  * Accomplished: 
    * Completed the run, but I had to skip an error about sample names with identical SRA values across different studies.


***
## Lab journal
---------------------------------------------------------------------------------------------------------------

### 2020-2-11
* Re-ran the AMR++ pipeline, but this time just to the nonhost step so I can backup those files in Noelle's server. 

```
Launching `main_to_nonhost.nf` [intergalactic_lamport] - revision: 8d2b394352
[warm up] executor > local
executor >  local (46)
[c5/0796b5] process > BuildHostIndex   [100%] 1 of 1, cached: 1 ✔
[40/c95273] process > RunQC            [100%] 103 of 103, cached: 103 ✔
[ff/270030] process > AlignReadsToHost [100%] 103 of 103, cached: 88, failed: 2 ✔
[4d/fb50f5] process > RemoveHostDNA    [100%] 101 of 101, cached: 86 ✔
[ea/480cbc] process > NonHostReads     [100%] 101 of 101, cached: 86 ✔
[0e/2b93a3] process > QCStats          [100%] 1 of 1, cached: 1 ✔
[d0/bb15c5] process > HostRemovalStats [100%] 1 of 1 ✔
Completed at: 11-Feb-2020 10:58:26
Duration    : 23h 52m 59s
CPU hours   : 858.2 (90.2% cached, 1% failed)
Succeeded   : 44
Cached      : 365
Ignored     : 2
```
### 2020-2-10
* Singularity issue was resolved and I started running the pipeline again.

### 2020-2-6
* Was attempting to run the pipeline, but kept getting errors due to singularity. I contacted the MSI helpdesk and was informed that this was a server issue and they were working on fixing it.


### 2020-1-15
* The Kraken 2 run was completed
```
nextflow run minor_kraken2.nf -profile local_MSI -w /scratch.global/run_rumen_capstone/rumen_work_dir --threads 4 --reads '/home/noyes046/shared/seq_data/rumen_project_nonhost_reads/*.non.host.R{1,2}.fastq.gz' --output /scratch.global/run_rumen_capstone/Rumen_kraken_results --kraken_db /home/noyes046/shared/databases/kraken2_databases/Rumen_kraken_v2_Nov2019/ -resume
```

* Now, run with MEGARes v2
```
nextflow run minor_only_AMR.nf -profile local_MSI -w /scratch.global/run_rumen_capstone/rumen_work_dir --threads 5 --reads '/home/noyes046/shared/seq_data/rumen_project_nonhost_reads/*.non.host.R{1,2}.fastq.gz' --output /scratch.global/run_rumen_capstone/Rumen_MEGARes_results -resume
```

### 2020-1-14
* Non-host reads were done and I moved everything to Noelle's server to ensure they don't get deleted on accident

### 2020-1-12
* Re-started pipeline to create non-host reads. 
  * Fixed issue where some samples had the same SRA name, even though they were from different projects and were different files sizes.
