Title of Proposal:
------------

Project summary

The three 16S Pools are in directories named (pool 1-3 respectively):
191118_M01247_0372_000000000-CMB87
191122_M01247_0374_000000000-CR8L7
191204_M01247_0377_000000000-CRMGJ



***
## Workflow

After downloading files, I ran into an issue when trying to run the pipeline with nextflow because of the naming convention having a underscore right after the N, "N_##"

```bash
# Sign-in using Paul's account information and download all three directories above.
sftp pmorley55@seqdata.ucdenver.pvt 

# Rename files
rename 's/N_/N/g' *.gz

# Download github repository with nextflow scripts


# Run pipeline
nextflow run main_qiime2.nf --reads "/media/AngusWorkspace/Jake_project/*_R{1,2}_001.fastq.gz" --output Jake_qiime2 -profile local --metadata "/media/AngusWorkspace/run_Jake/jake_metadata.tsv" --classifier "/media/AngusWorkspace/run_Jake/bioinformatic-nextflow-pipelines/gg-13-8-99-515-806-nb-classifier.qza"
```
