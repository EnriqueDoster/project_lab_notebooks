Title of Proposal: How does analytic approach impact pathogen population structure when analyzing whole genome sequence data?
------------

"The overall goal of this project is to support an accurate, reproducible, transparent and uniform approach to whole-genome sequence (WGS) analysis for purposes of outbreak detection and pathogen surveillance. 
* The overarching objective is to demonstrate how different analytic approaches to whole-genome sequence analysis can impact analysis results.
* Supporting objectives are to evaluate the impacts:
  * dataset
  * core- vs. pan-genome inclusion
  * genome comparison approach (i.e., using SNPs, k-mers, gene-by-gene alleles, or functional domains).
* Additionaly, we wil provide information regarding the usability of different WGS pipelines and NCBI's pathogen genome database.


Main project resources
-----
[WGS pipeline github](https://github.com/TheNoyesLab/WGS_SNP_pipelines)
SFTP site: ftp.ncbi.nlm.nih.gov/pathogen/

- MSI genome locations
  - E coli and shigella - 7,537 genomes
    * /panfs/roc/risdb_new/genometrakr/ecoli_and_shigella
  - Salmonella enterica - 40,437 genomes
    * /panfs/roc/rissdb_new/genometrakr/salmonella_enterica
  - Listeria monocytogenes - 11,172 genomes
    * /panfs/roc/risdb_new/genometrakr/listeria_monocytogenes

Current Tasks
-----

  1. Create pipeline with all WGS analysis tools
  2. Run on Listeria genomes
  
Milestones
-----
![Milestones](https://github.com/EnriqueDoster/project_lab_notebooks/blob/master/postdoc_projects/docs/FMPRE_WGS_timeline.png "timeline")

| Status | Milestones| Date  | Description  |
| -------| ------------- |:------------:| ------------|
| | 1      | Jun 15, 2019  | Download all data, create 15 datasets |
| | 1.5 | ASAP  | Create 15 datasets |
|X| 2      | July 31, 2019 | Download CFSAN-SNP, Lyve-SET, Enterobase, kSNP, Moura et al |
|X| 3      | Aug 1, 2019   | Interim report due |
| | 4      | Sep 30, 2019  | Develop automated pipeline for functional annotations of domains with IBM |
|X| 5      | Nov 30, 2019  | Execute pipelines on the “Random” Salmonella dataset; troubleshooting and validation  |
| | 6      | Jan 31, 2020  | Execute pipelines on all 15 datasets |
| | 7      | May 15, 2020  | Analysis |
| | 8      | Aug 30, 2020  | Manuscript and report preparation |
    
    
    
Project status
-----

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
    * 
- November 2019:
  * Goal: Make sure pipelines work on MSI.
  * Notes:
    * 
  * Accomplished: 
    * 
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
    * Josh Baller began downloading all 200k Salmonella genomes and then we switched to only downloading the ~40k isolates from genomeTrakr.
- June 2019: Vacation
- May 2019:
  * Goal: Figure out how to download pathogen genomes
  * Notes:
    * It's important to note the distinction between the entire Pathogen database and GenomeTrakr as a source for genomes included in the database.
  * Accomplished: 
    * Corresponding with Ruth Timme from the FDA helped identify which genomes in the pathogen database are submitted by GenomeTrakr. 



***
Lab journal
---------------------------------------------------------------------------------------------------------------


### 2019-1-7
* I had a meeting with Noelle to evaluate the plan for running WGS pipelines on MSI. The original proposal consisted of running all 200k Salmonella genomes, but we are not allowed to download all of these genomes because it would take up too much space on MSI. We adapted to make the subset of genomes submitted by GenomeTrakr the "whole data set", which for Salmonella enterica consisted of 40K genomes. Instead, I think we could download the genomes in-line and delete them right after running the pipeline. Now, we just need permission to temporarily take up ~80-100TB of space for each genome. I will check in with MSI to see if they would allow it and I'll optimize the pipeline to make sure we delete unnecessary files. 


### 2019-9-19

* Received email from Thomas Kono saying that the L. monocytogenes and the E. coli/Shigella genomes were succesfully downloaded.


### 2019-9-13

* After discussion with Noelle, we decided to only download genomes from GenomeTrakr and not include the other sources.

### 2019-9-9

* Thomas Kono thinks the Listeria and Escherichia/Shigella genomes will take up too much space. Email follows: "However, there is an issue with the size of the files that we would be hosting in risdb. I randomly sampled 1000 of the accessions that you shared and extracted them. A total of 925 were still present in the SRA database, and they expanded to an average of 0.338 GB per accession, which puts the estimate for the whole list of accessions at 28.202 TB of data. Combined with the ~14 TB that the Salmonella already occupy, this puts the disk usage at ~42 TB, which is above the limit for hosting in the publicly available space"

### 2019-9-1

* Interim report was submitted.


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


### 2019-5-5

* Troubleshooting the download of SRA data and metadata
* Attempted a python script to parse SRA metadata and sent Meera some example files, but still need to troubleshoot duplicate rows.


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



