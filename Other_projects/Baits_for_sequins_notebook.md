Goal: Create Agilent baits for enrichment Sequins spike-in sequences.
------------



Table of Contents
-----
* [Main project resources](#main-project-resources)
* [Current tasks](#current-tasks)
* [Milestones](#milestones)
* [Monthly project status](#monthly-project-status)
* [Lab Journal](#lab-journal)

## Main project resources

We'll use the same pipeline we created for making pathogen-specific Agilent baits.
[Bait creation github page](https://github.com/EnriqueDoster/bait_creation_pipeline)

* ANAQUIN: a software toolkit for the analysis of spike-in controls for next generation sequencing 
  * https://academic.oup.com/bioinformatics/article/33/11/1723/2959850

* Synthetic microbe communities provide internal reference standards for metagenome sequencing and analysis
  * https://www.nature.com/articles/s41467-018-05555-0

https://github.com/sequinstandards/Anaquin


## Current Tasks

  1. Identify all Sequins sequences and run the bait creation pipeline.
  
## Milestones

![Milestones]( "timeline")

| Status | Milestones| Date  | Description  |
| -------| ------------- |:------------:| ------------|
| | 1      | date  | short description |

    
## Monthly project status

- January 2020:
  * Goal: Find all Sequins sequences
  * Notes:
    * 
  * Accomplished: 
    * Downloaded all sequences from Anaquin and created probes with the CATCH software


***
## Lab journal
---------------------------------------------------------------------------------------------------------------


### 2019-1-14

* I figured out the bait design nextflow script was not working properly on sequins because the fasta file contains sequences shorter than the desired probe length (120).

```
nextflow run main_bait_design.nf --input_fasta /home/enriquedoster/Dropbox/Projects/sequins_bait_design/metasequin_sequences_3.0.fa -profile local --output /home/enriquedoster/Dropbox/Projects/sequins_bait_design/test_sequins --probe_length 120
```


### 2019-1-13
* I downloaded the anaquin github repository and created probes using the "design.py" script from CATCH. The metasequin_sequences_3.0.fa file contained 178 sequences and 3348 probes were created using the following command:

```
git clone https://github.com/sequinstandards/Anaquin.git

mv Anaquin/data/metagenome/metasequin_sequences_3.0.fa

design.py metasequin_sequences_3.0.fa -pl 120 -ps 120 -o metasequin_sequences_3.0.fa.probes.fasta --max-num-processes 10 --verbose --small-seq-skip 120
```


