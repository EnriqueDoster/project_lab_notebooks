Creating Mannheimia haemolytica sequencing baits
------------

Goal: Create educational materials 


Main project repository
-----
[github](https://github.com/EnriqueDoster/Bioinformatic_resources)


Current Tasks
-----

  1. Run CATCH to create baits
    
    * Test various "design.py" flags
  2. Compare bait design to
    

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
  




