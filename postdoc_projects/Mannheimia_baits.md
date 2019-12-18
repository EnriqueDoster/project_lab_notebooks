Creating Mannheimia haemolytica sequencing baits
------------

Goal: Use the CATCH software to create sequencing baits for Mannheimia haemolytica


Main project repository
-----
[Bait github](https://github.com/EnriqueDoster/bait_creation_pipeline)


Current project status
-----

Tasks:
  1. Run CATCH to create baits
    * Optimize with pipeline
    * Test various "design.py" flags
  2. Improve specificity of baits
    * Test kraken and/or blast to identify contaminant sequences


- December 2019: 
  * Goal: Create bait design using all 69 genomes in a single file.
  * Notes:
    * On 2019-12-16, finished creating nextflow pipeline to better utilize "design.py"
- November 2019:


***
Lab journal
---------------------------------------------------------------------------------------------------------------


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
  




