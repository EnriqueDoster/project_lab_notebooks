Creating Mannheimia haemolytica sequencing baits
------------

Goal: Use the CATCH software to create sequencing baits for Mannheimia haemolytica


Main project repository
-----
[Bait github](https://github.com/EnriqueDoster/bait_creation_pipeline)


Current Tasks
-----


  1. Improve specificity of baits
  
    * Test kraken and/or blast to identify contaminant sequences
  2. Determine which loci are associated with different PFGE clusters.
    * Is this different for short reads?
   
    

Current project status
-----

- December 2019: 
  * Goal: Create bait design using all 69 genomes in a single file with updated flags.
  * Notes:
    * On 2019-12-16, finished creating nextflow pipeline to better utilize "design.py"
- November 2019:
  * Goal: Create design by splitting genomes into smaller groups.
  * Notes:
    * Broke genome sequences into groups of 5.
  * Accomplished: 
    * Finished first design using all genomes. Combined sequences (239,918) and removed redunant sequences (225,118) using cdhit.
- October 2019:
  * Goal: Create bait design using all 69 M haemolytica genomes..
  * Notes:
    * Running the 69 genomes at once took way too long and was slowing down the server.
  * Accomplished: 
    * Unfortunately, nothing was actually accomplished with a combination of Angus server breakdowns and cancelling the command on Noelle's server to free up computing power for another project.
- September 2019:
  * Goal: Create design on test subset of 34 genomes.
  * Notes:
  * Accomplished: 
    * Finished design on 34 genomes resulting in 24,676 baits.


***
Lab journal
---------------------------------------------------------------------------------------------------------------


### 2020-1-25
* We received an email from Mike Clawson with a spreadsheet containing important gene regions
```
Hello Enrique and everyone,

 

Attached is a spreadsheet that has variable loci that would be useful to type Mannheimia haemolytica strains at both the serotype, genotype, and subtype levels. Tagging subtype SNPs and the entire capsule biosynthetic loci for A1, A2, and A6 strains are represented in the spreadsheet.  With this information for a given strain, it’s molecular serotype, genotype and subtype should be discernable.  Genotype 1 subtypes are b, c, e, f, and i.  For genotype 2 they are c, d, and b/e.

 

The tagging information will be good to have, and the assembled contigs pulled down for M. haemolytica strains should be amendable to analysis with phylogenetic software that includes reference M. haemolytica genomes.  I understand this may be tricky if there are contigs representing multiple strains in a sample.

 

Regarding conserved regions specific to M. haemolytica.  Is there any chance you have that information already from the Catch software and the blasting process that removed sequences that were not M. haemolytica specific?  The Catch software should have been identifying conserved regions for probe design.

 

One more question, there are other full-length M. haemolytica genomes in GenBank then our 69, with one in particular that ideally would have been included for probe design.  That is CP006957.  Please take a look at the attached pdf to see how it places with the genomes we did.  This is a very different genome of an A2 strain then what we sequenced. Variation within the capsule serotyping locus alone can distinguish this strain from other A2 strains as there are multiple alleles unique to that particular strain.  

 

If I understand the sequencing question correctly, I think it would be better to dial in with deeper coverage to the regions in the spreadsheet, and other regions of interest (like AMR genes) versus conserved regions which are essentially non-informative (aside from confirming the sequence is M. haem and defining the genomic backbone).  I don’t think it’s necessary to weight coverage differently between the variable regions in the spreadsheet as there is some tagging redundancy.

 

Best regards,

 

Mike
```



### 2020-1-20
* Email was sent to collaborators with updates and to request guidance on "genes of interest" to consider in our bait design.

```
Hello everyone,

 

We are reaching out to provide a brief update on our progress with developing the bait-pulldown system for target-enriched Mh sequencing from metagenomic samples.   As we discussed, the goal is to develop a set of baits that is comprehensive to regions of the Mh genome that are specific to that organism, and especially for variable regions that can allow strain typing.  Given that we intend to apply these baits to metagenomic samples, we also have to be concerned about specificity.

 

Since our meeting at AVC, we used the M. haemolytica genomes from Dr. Clawson (GenBank genomes CP017484 – CP017552) and processed these the "CATCH" software (https://github.com/broadinstitute/catch) to design an optimal set of baits as described by Metsky et al (Nat Biotechnol. 2019. doi: 10.1038/s41587-018-0006-x). We have further processed the bait set using blast to identify and remove sequences that were not specific to M. haemolytica (i.e., those that are homologous with other Pasteurelleciae or other bacteria).   

 

Having generated this set of candidate baits, we now want to check the coverage of these baits to "regions of interest" in the M. haemolytica genome that have previously been identified as important for typing.  We are not bacterial geneticists, or even card-carrying bacteriologists (!) so we are hoping to solicit the team’s help: 

Can you help us identify a list of genomic regions (aka genes) and the sequence coordinates that we can map coverage against? 
We were hoping to obtain a list of previously identified highly-variable regions
We also want to obtain a list of conserved regions that are specific to Mh. 
 

Also, we would like your input on should we be aiming for even coverage across these sequence regions, or if it would be better to develop baits that provide overlapping, deeper coverage.
 

Thank you for your time and help!

 

Enrique and Paul
```



### 2019-8-13

* Probe design resulted in a total of 24,676 baits using 34 M. haemolytica genomes


### 2019-8-12

* Installed CATCH using anaconda
* Run "design.py" on 34 M. haemolytica genomes to test probe creation.

```bash
design.py  all_34_genomes.fa -pl 120 -ps 1 -o test_34genome_probes
```

### 2019-8-9

* We had a meeting including most collaborators. Below is everyone invited to join the meeting.
  Woolums, Amelia <amelia.woolums@msstate.edu>
  Paul Morley <pmorley@cvm.tamu.edu>,
  Enrique Doster <enriquedoster@gmail.com>,
  Jonathan Frye <jonathan.frye@ars.usda.gov>,
  "Clawson, Mike" <mike.clawson@usda.gov>,
  Sarah Capik <Sarah.Capik@ag.tamu.edu>,
  "Thoresen, Merrilee" <mt1657@msstate.edu>,
  Cory Wolfe <Cory.Wolfe@colostate.edu>,
  "Castle,Jake" <Jake.Castle@colostate.edu>,
  Noelle Noyes <nnoyes@umn.edu>,
  Charlene Jackson <charlene.jackson@ars.usda.gov>,
  Sushim <sushimgupta@gmail.com>,
  Dustin Loy <jdloy@unl.edu>,
  "Epperson, Bill" <epperson@cvm.msstate.edu>,
  Will Crosby <wbc95@msstate.edu>,
  "lari.hiott@ars.usda.gov" <lari.hiott@ars.usda.gov>,
  "Karisch, Brandi" <brandi.karisch@msstate.edu>,
  "Blanton, John" <john.blanton@msstate.edu>
  
* Main take-aways for my part of the project
  * We will use CATCH, developed by the Broad institute, to create baits for enrichment of M. haemolytica. 
  * Goal is to use Mike Clawson's 69 genomes to create the baits
  * Further discussion warranted regarding the fine-tuning of the bait design.
  * Paul sent me zipped file of 34 genomes to begin experimenting with CATCH.
  




