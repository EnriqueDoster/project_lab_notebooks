

/s/angus/index/common/tools/nextflow run main_AmrPlusPlus_v2_withRGI.nf --reads "/media/AngusStorage/Raw_Data_2020/CEAH_calf_proj1_2020/CEAH_calf_proj1_targetedAMR/concat_reads/*_finalcat_R{1,2}.fq.gz" --host /s/angus/index/databases/bwa_indexes/mod_bos_taurus/mod_bos_taurus.fna --annotation /media/AngusWorkspace/CEAH_calf_proj1_AMR/bioinformatic-nextflow-pipelines/data/amr/megares_modified_annotations_v2.00.csv --amr /media/AngusWorkspace/CEAH_calf_proj1_AMR/bioinformatic-nextflow-pipelines/data/amr/megares_modified_database_v2.00.fasta --output /media/AngusWorkspace/CEAH_calf_proj1_AMR/AMR_Output -profile local_angus --threads 6


# Use script to move the 130 files that have already been run to nonhost

# Start the run on the remaining 90 samples.
/s/angus/index/common/tools/nextflow run minor_to_nonhost.nf --reads "/media/AngusStorage/Raw_Data_2020/CEAH_calf_proj1_2020/CEAH_calf_proj1_targetedAMR/concat_reads/*_finalcat_R{1,2}.fq.gz" --host /s/angus/index/databases/bwa_indexes/mod_bos_taurus/mod_bos_taurus.fna --output /media/AngusWorkspace/CEAH_calf_proj1_AMR/2nd_part_nonhost_reads -profile local_angus --threads 6

