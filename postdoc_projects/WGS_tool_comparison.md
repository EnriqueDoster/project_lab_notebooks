Title of Proposal: How does analytic approach impact pathogen population structure when analyzing whole genome sequence data?
------------

"The overall goal of this project is to support an accurate, reproducible, transparent and uniform approach to whole-genome sequence (WGS) analysis for purposes of outbreak detection and pathogen surveillance. 
* The overarching objective is to demonstrate how different analytic approaches to whole-genome sequence analysis can impact analysis results.
* Supporting objectives are to evaluate the impacts:
  * dataset
  * core- vs. pan-genome inclusion
  * genome comparison approach (i.e., using SNPs, k-mers, gene-by-gene alleles, or functional domains).
* Additionaly, we wil provide information regarding the usability of different WGS pipelines and NCBI's pathogen genome database.

## Current Tasks

  1. Create script to parse the metadata file and download genomes as part of the pipeline
  2. Run pipeline on test set of genomes and finalize erasing temporary files

Table of Contents
-----
* [Main project resources](#main-project-resources)
* [Milestones](#milestones)
* [Monthly project status](#monthly-project-status)
* [Lab Journal](#lab-journal)

## Main project resources

[WGS pipeline github](https://github.com/TheNoyesLab/WGS_SNP_pipelines)

SFTP site: ftp.ncbi.nlm.nih.gov/pathogen/

- MSI genome locations
  - E coli and shigella - 7,537 genomes
    * /panfs/roc/risdb_new/genometrakr/ecoli_and_shigella
  - Salmonella enterica - 40,437 genomes
    * /panfs/roc/rissdb_new/genometrakr/salmonella_enterica
  - Listeria monocytogenes - 11,172 genomes
    * /panfs/roc/risdb_new/genometrakr/listeria_monocytogenes


  
## Milestones

![Milestones](https://github.com/EnriqueDoster/project_lab_notebooks/blob/master/postdoc_projects/docs/FMPRE_WGS_timeline.png "timeline")

| Status | Milestones| Date  | Description  |
| -------| ------------- |:------------:| ------------|
| | 1      | Jun 15, 2019  | Download all data, create 15 datasets |
| | 1.5 | ASAP  | Create 15 datasets |
|X| 2      | July 31, 2019 | Download CFSAN-SNP, Lyve-SET, Enterobase, kSNP, Moura et al |
|X| 3      | Aug 1, 2019   | Interim report due |
| | 4      | Sep 30, 2019  | Develop automated pipeline for functional annotations of domains with IBM |
| | 5      | Nov 30, 2019  | Execute pipelines on the “Random” Salmonella dataset; troubleshooting and validation  |
| | 6      | Jan 31, 2020  | Execute pipelines on all 15 datasets |
| | 7      | May 15, 2020  | Analysis |
| | 8      | Aug 30, 2020  | Manuscript and report preparation |
    
    
    
## Monthly project status

- January 2020: 
  * Goals: 
    * Email MSI regarding the use of "/scratch.global/"
    * Begin aggregating list of questions for NCBI
    * Begin report regarding the use of these 
    * Check genome vs non-core genome (Clawson)
  * Notes:
    * 
- December 2019:
  * Goal:
    * Run test-set of genomes
  * Notes:
    * I was finally able to get the nextflow pipelines and singularity containers to work well together, but now the only issue is ensuring I handle the data in the most efficient manner. Each WGS tool requires differing input formats, so I need to be careful that I don't duplicate any files that would cause our storage requirement to greatly increase.
- November 2019:
  * Goal: Make sure pipelines work on MSI.
  * Notes:
    * I had a hard time getting singularity to work well with Singularity and nextflow. 
- October 2019:
  * Goal: Work on creating singularity containers and nextflow scripts to facilitate running each WGS tool.
  * Notes:
    * A lot of time was spent troubleshooting errors with java and specific versions of tools that were required for the WGS pipelines to work well.
  * Accomplished: 
    * I succesfully made singularity containers for each tool and was able to run them on my local computer.
- September 2019:
  * Goal: Finish dowloading all genomes
  * Notes:
    * Working on finalizing the download of E. coli and Shigella genomes
    * We were notified that these genomes would take up too much space because it be up to 28TB plus the ~14TB of Salmonella genomes.
  * Accomplished: 
    * 7,537 E. coli and Shigella genomes succesfully downloaded to /panfs/roc/risdb_new/genometrakr/ecoli_and_shigella
    * 11,172 SRA accessions in the file you sent, 10,901 were able to be downloaded for Listeria monocytogenes to /panfs/roc/risdb_new/genometrakr/listeria_monocytogenes
- August 2019:
  * Goal: Create preliminary data for interim report
  * Notes:
    * Meera, James Kaufman, Noelle, and I all worked together to put together the interim report.
  * Accomplished: 
    * 14TB - 40,437 Salmonella enterica genomes were downloaded to /panfs/roc/rissdb_new/genometrakr/salmonella_enterica
    * I ran a test subset of genomes with kSNP3, CFSAN-SNP, lyveset, and Enterobase to include in the report.
- July 2019:
  * Goal: Figure out way to identify all SRA values for genometrakr, begin Salmonella enterica genome download.
  * Notes:
    * We gave Josh Baller a "script" to download the roughly 200k Salmonella enterica  genomes found in the "pathogen" database (that includes ~41,084 isolates from GenomeTrakr).
    * Josh reached out early in July to say the files would take up too much space. 
    * We decided to only download the genomes from GenomeTrakr for now.
  * Accomplished: 
    * Was able to download all of the SRA metadata and begin figuring out the command to find unique SRA values.   
    * Josh Baller began downloading all 200k Salmonella genomes
- June 2019:
  * Goal: Start Salmonella enterica genome download
  * Notes:
    * There was a bit of lag time between me sending the script for downloading genomes and when someone was assigned to get the process started. 
  * Accomplished: 
    * Sent list of "fastq-dump" commands to Joshua Baller to download ~200k Salmonella genomes
- May 2019:
  * Goal: Figure out how to download pathogen genomes
  * Notes:
    * It's important to note the distinction between the entire Pathogen database and GenomeTrakr as a source for genomes included in the database.
  * Accomplished: 
    * Corresponding with Ruth Timme from the FDA helped identify which genomes in the pathogen database are submitted by GenomeTrakr. 



***
## Lab journal
---------------------------------------------------------------------------------------------------------------

### 2019-1-16
* Received email from Tom Kono that we should be able to work with MSI to integrate our pipeline with their tools. Here is the email:

```
Hello,

Thank you for your patience! We have discussed the pipelined analysis idea and it should work well with the goals of the University of Minnesota Informatics Institute (UMII; https://research.umn.edu/units/umii). Their director is Dr. Thomas Pengo (tpengo@umn.edu), and he should be able to provide more detailed information about what support they can offer for developing workflows for large-scale data retrieval and metadata processing. He may have input regarding strategies for sharing the GenomeTrakr databases across research groups at the university, too.

With regard to the disk usage in scratch, that should work well with our policies around scratch usage. However, please do let us know when you plan to start working with the high-volume files in scratch, so we can make sure that the system will be able to handle it. Please let us know if you have additional questions, thank you!
--
Tom Kono
RIS Analyst | Minnesota Supercomputing Institute | msi.umn.edu
117 Pleasant Street S.E., 553 Walter Library
University of Minnesota | umn.edu
konox006@umn.edu | 612-626-4971
```


### 2019-1-13
* kSNP3 finished running for 194 samples, here is the nextflow output:

```
nextflow run main_test_ksnp3.nf --reference_genome /scratch.global/test_WGS/ref_genome.fasta --reads '/scratch.global/test_WGS/test_genomes/*_{1,2}.fastq' -profile singularity --output test_WGS_combined -resume
N E X T F L O W  ~  version 19.04.1
Launching `main_test_ksnp3.nf` [insane_galileo] - revision: 8deb467d88
[warm up] executor > local
executor >  local (196)
[46/760424] process > RunFastqConvert [100%] 194 of 194 ✔
[4a/ffd5da] process > RunMakeList     [100%] 1 of 1 ✔
[7a/5f0162] process > RunKSNP3        [100%] 1 of 1 ✔
Completed at: 13-Jan-2020 16:55:15
Duration    : 1h 48m 35s
CPU hours   : 5.4
Succeeded   : 196
```



### 2019-1-7
* I had a meeting with Noelle to evaluate the plan for running WGS pipelines on MSI. The original proposal consisted of running all 200k Salmonella genomes, but we are not allowed to download all of these genomes because it would take up too much space on MSI. We adapted to make the subset of genomes submitted by GenomeTrakr the "whole data set", which for Salmonella enterica consisted of 40K genomes. Instead, I think we could download the genomes in-line and delete them right after running the pipeline. Now, we just need permission to temporarily take up ~80-100TB of space for each genome. I will check in with MSI to see if they would allow it and I'll optimize the pipeline to make sure we delete unnecessary files. 


### 2019-9-19

* Received email from Thomas Kono saying that the L. monocytogenes and the E. coli/Shigella genomes were succesfully downloaded.


### 2019-9-13

* After discussion with Noelle, we decided to only download genomes from GenomeTrakr and not include the other sources.

### 2019-9-9

* Thomas Kono thinks the Listeria and Escherichia/Shigella genomes will take up too much space. Email follows: "However, there is an issue with the size of the files that we would be hosting in risdb. I randomly sampled 1000 of the accessions that you shared and extracted them. A total of 925 were still present in the SRA database, and they expanded to an average of 0.338 GB per accession, which puts the estimate for the whole list of accessions at 28.202 TB of data. Combined with the ~14 TB that the Salmonella already occupy, this puts the disk usage at ~42 TB, which is above the limit for hosting in the publicly available space"
* Thomas also shared his "prefetch" and "dump" scripts which greatly increase genome download speed. I will be using this method to download genomes for the pipeline as well.

### 2019-9-1

* Interim report was submitted.
* I also sent the SRA values for all the genomes from E coli/Shigella and Listeria.


### 2019-8-28

* Email to Noelle and Meera:
  * Hi Noelle and Meera, 

I have an update on the number of genomes for the other two species groups. Even though there are more Escherichia coli/Shigella genomes (60k) than GenomeTrakr Salmonella (40k) genomes, I think we should ask to download the entire datasets for both E coli/Shigella and Listeria. What do you think?
E coli and Shigella
All sources: ~63,674 genomes
Only GenomeTrakr: ~7,563 genomes
Listeria
All sources: ~26,432 genomes
Only GenomeTrakr: ~11,172 genomes

### 2019-8-26

* Email from Thomas that the Salmonella enterica genomes were downloaded. "The Salmonella enterica SRA accessions have finished downloading! They are located in this directory: /panfs/roc/risdb_new/genometrakr/salmonella_enterica.  Please note that if you want to access this directory from one of the "lab" nodes, the path is /panfs/roc/rissdb_new/genometrakr/salmonella_enterica (two s in rissdb_new). There are a total of 40,437 accessions that successfully downloaded. The ones that failed look like accessions that have been removed from the SRA database. The log file with the list of accessions that have been removed is attached."

### 2019-8-23
* Received a promising update from Thomas that the new method of downloading genomes was much faster than just using "fastq-dump". 
  * "Hi Enrique,The prefetch script started yesterday evening, and in the ~15 hours it has been running, it has fetched 17,751 of 38,460 .sra files, so hopefully it will finish in the next couple days! Once the prefetch is finished, I will start exporting to fastq. It looks like prefetch is the right way to go for large downloads from the SRA. It just requires one extra command: "prefetch [accession]" before calling "fastq-dump [accession]" so it should be easy to set up for the other species. Thanks!

### 2019-8-22
* We heard from Thomas that he will try a new approach for downloading the genomes and that he would let us know how it went.

### 2019-8-12
* I reached out to Josh to check on the progress of the download and whether they were experiencing issues with "fastq-dump" as I was often being disconnected. I also recommended the latest SRA toolkit as a potential improvement. 

### 2019-7-29
* Clarification email to Josh from Noelle as to why the GenomeTrakr subset of genomes was still a helpful communal resource for MSI
 * "Hi Josh, The original set of samples contained everything in the "Pathogens" database of NCBI.  However, that includes submissions from many non-verified submitters.  Instead, we think it is better to only pull submissions from the laboratories that are recognized as being able to submit to GenomeTrakr (the US government's food safety WGS system) -- these submissions are more standardized and meet certain QC thresholds.  The only way to identify those submissions is to extract the relevant identifiers from the "submitter" field of the metadata.  So that is what Enrique did on the latest version of the script.  So now, the samples we are pulling are the ones that are truly part of the GenomeTrakr network; whereas the original script was pulling GenomeTrakr PLUS other submissions. Does that make sense?"


### 2019-7-25
* We decided to focus on the genomes from GenomeTrakr and I sent Josh a script with 41,084 Salmonella genomes.


### 2019-7-17
* We received an email from Joshua Baller stating that the Salmonella genomes would take up too much space. Email below:
  * "We ran some tests on the scripts you provided and they appear to be working well, however our estimates of the amount of data that will be pulled down is considerably more than the 20TB Noelle and Meera estimated in our earlier discussions. Your script as is will likely pull down around 225TB. We added a compression step on the end as most sequencing tools can now handle compressed files, even then we are looking at around 70TB. This is a bit more than we can host as a communal resource at this time."

### 2019-7-12
* Checked in with Joshua again and he promised to provide an update after speaking with the staff member involved.

### 2019-6-28
* Checked in with Joshua on the progress of downloading Salmonella genomes and was assured he would get started with it right away.


### 2019-6-19

* I sent an email to Joshua Baller to begin download of Salmonella genomes which contained:
  * A draft tutorial of how I found the unique SRA values for Salmonella genomes.
  * A file with all of the "fastq-dump" commands for 202,985 genomes (plus non-chromosomal sequences)


### 2019-5-3

* Troubleshooting the download of SRA data and metadata
* Downloading the genome metadata from the website, https://www.ncbi.nlm.nih.gov/pathogens/isolates#/search/, is not successful because the output file is limited to 10,000 lines.
* Next goal is to explore the ftp site to download the metadata files that are included in the same directory as the genomes.

### 2019-5-29

* I sent the series of emails between Ruth Timme (FDA) and me as we discussed how to identify which genomes in the pahogen database were submitted by GenomeTrakr. Here are some highlights:
  * The metadata file on the FTP site should contain all the salmonella isolates in the Pathogen Detection database. This includes all the GenomeTrakr contributions as well as PulseNet, Public Health England, and other submitters.  If you want to filter for GT-only isolates I can help you identify some flags, like the sra_center or bioproject_center that you can filter on for isolates submitted by GenomeTrakr.  We don’t draw a clear distinction in the database for the submitting networks since the data are all collected as part of the same surveillance effort, from the same SOP, QC thresholds, etc.
  * I’m attaching the sheet I just downloaded so you can see the headings.  I did a quick filter for sra_center = FDA, CFSAN, FDA,CFSAN or FDA/CFSAN and the numbers look about right for what we’ve submitted for the network (almost 40K isolates).

### 2019-5-1

* Using the https://www.ncbi.nlm.nih.gov/pathogens/isolates#/search/ website.
* Can use search terms to identify only genomes of interest.
  * Click "Find Isolates Now!", search: taxgroup_name:"Salmonella enterica" OR taxgroup_name:"E.coli and Shigella" OR taxgroup_name:"Listeria monocytogenes"
* Click the following buttons #then "Expand All", then "Download" as file "IsolateBrowser_full_list.csv"



