Title of Proposal:
------------

Project summary

* N = 236 paired end samples
  * 60 from beef systems
  * 60 from poultry
  * 60 from swine
  * 56 from Human waste water plants


Host genome
cat /panfs/roc/risdb/genomes/Bos_taurus/Bos_taurus_UMD_3.1/bwa/Bos_taurus_UMD_3.1.fa /panfs/roc/risdb/genomes/Gallus_gallus/galGal3/bwa/galGal3.fa /panfs/roc/risdb/genomes/Sus_scrofa/Sscrofa10.2/bwa/Sscrofa10.2.fa /panfs/roc/risdb/genomes/Homo_sapiens/hg38/seq/hg38.fa > proj7_4hosts.fa



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

- October 2019:
  * Goal: 
  * Notes:
    * 
  * Accomplished: 
    * 


***
## Lab journal
---------------------------------------------------------------------------------------------------------------

### 2020-04-12
* The AMR++ run failed and there were less files in the working directory then when I first started the run. Still not sure why files are being deleted when MSI says they don't actually remove files automatically.

* Trying everything again, but with the new storage space.
  * /tempalloc/noyes042/

```
nextflow run minor_AMR_SNP_detection.nf -profile local_MSI -w /tempalloc/noyes042/proj7/work_dir_AMR --threads 10 --reads '/home/noyes046/shared/projects/proj7_results/NonHostReads/*.non.host.R{1,2}.fastq.gz' --output /tempalloc/noyes042/proj7/proj7_AMRPlusPlus_results -resume -with-report non_host_run.report -with-trace -with-timeline
```


### 2020-04-07
* Run AMR++ analysis with the AMR snps
* Run on cn1107, but the working directory is still in scratch.global
```
nextflow run minor_AMR_SNP_detection.nf -profile local_MSI -w /scratch.global/run_proj7/work2_dir_AMR --threads 20 --reads '/home/noyes046/shared/projects/proj7_results/NonHostReads/*.non.host.R{1,2}.fastq.gz' --output /scratch.global/run_proj7/proj7_AMRPlusPlus_results -resume -with-report non_host_run.report -with-trace -with-timeline
```


### 2020-03-07


```
nextflow run rm_other_host.nf -profile local_MSI -w /scratch.global/run_proj7/work2_dir_nonhost --threads 6 --reads '/home/noyes046/shared/projects/proj7_results/NonHostReads/*.non.host.R{1,2}.fastq.gz' --output /scratch.global/run_proj7/proj7_all_hosts_removed --host /scratch.global/run_proj7/proj7_4hosts.fa -resume -with-report non_host_run.report -with-trace -with-timeline
```


### 2020-03-01
* There were a couple of issues with the MSI server reseting and stopping my progress, but the project 7 sequences are nearly done being processed (206/236) processed to remove the bos taurus sequences.
  * Unfortunately, this is when I remembered that I need to run each sample type based on their host so I'll still need to remove chicken, pig, and human DNA from these samples
  * For now, I'll move these non-bovine sequences back to Noelle's server and combine all other host genomes for another host removal run.
 ```
 edoster@cn4201 [/scratch.global/run_proj7] % du --max-depth=1 -h
200M	./amrplusplus_v2
11T	./work2_dir_nonhost
8.0T	./proj7_nonhost_fastq
19T	.
 ```
 
### 2020-02-25

```
nextflow run minor_to_nonhost.nf -profile local_MSI -w /scratch.global/run_proj7/work2_dir_nonhost --threads 6 --reads '/home/noyes046/shared/projects/proj7_raw_reads/*R{1,2}.fastq.gz' --output /scratch.global/run_proj7/proj7_nonhost_fastq --host /panfs/roc/risdb/genomes/Bos_taurus/Bos_taurus_UMD_3.1/bwa/Bos_taurus_UMD_3.1.fa --adapters /panfs/roc/msisoft/trimmomatic/0.33/adapters/all_illumina_adapters.fa --kraken_db /home/noyes046/shared/databases/kraken2_databases/Rumen_kraken_v2_Nov2019/ -resume -with-report non_host_run.report -with-trace -with-timeline

```

