# Megatylan

/s/angus/i/nobackup/data/raw_sequence_data/tylan_1/16S_liver


# Tylan
nextflow run main_qiime2.nf --reads '/s/angus/i/nobackup/data/raw_sequence_data/tylan_1/16S_liver/*H*_{1,2}.fq.gz' --output /media/AngusWorkspace/updated_tylan1_liver_abscess_qiime2_results -profile local --classifier /media/AngusWorkspace/gg-13-8-99-515-806-nb-classifier.qza --threads 8 -w /media/AngusWorkspace/run_Jake/work_tylan_liver_abscess





# XIT


## liver abscess
/s/angus/i/nobackup/data/raw_sequence_data/mega_tylan/16S_XIT_liver
# running run_liver
# /media/AngusWorkspace/run_Jake/bioinformatic-nextflow-pipelines
nextflow run main_qiime2.nf --reads '/s/angus/i/nobackup/data/raw_sequence_data/mega_tylan/16S_XIT_liver/*_{1,2}.fq.gz' --output /media/AngusWorkspace/updated_XIT_liver_abscess_qiime2_results -profile local --classifier /media/AngusWorkspace/gg-13-8-99-515-806-nb-classifier.qza --threads 8 -w /media/AngusWorkspace/run_Jake/work_liver_abscess


## Exit Feces (2_run_liver)
/s/angus/i/nobackup/data/raw_sequence_data/mega_tylan/16S_XIT_exit_feces/concat_fastq
/media/AngusWorkspace/run_Jake/3_bioinformatic-nextflow-pipelines
nextflow run main_qiime2.nf --reads '/s/angus/i/nobackup/data/raw_sequence_data/mega_tylan/16S_XIT_exit_feces/concat_fastq/*_cat_R{1,2}.fq.gz' --output /media/AngusWorkspace/updated_XIT_exit_feces_qiime2_results -profile local --classifier /media/AngusWorkspace/gg-13-8-99-515-806-nb-classifier.qza --threads 8 -w /media/AngusWorkspace/run_Jake/work_xit_exit_feces



## Soilsurface  (surface_samples)
/media/AngusWorkspace/run_Jake/4_bioinformatic-nextflow-pipelines

nextflow run main_qiime2.nf --reads '/media/AngusStorage/Raw_Data_2020/Megatylan_XIT_Kuner/16S_XIT_soil_surface/*cat_R{1,2}.fq.gz' --output /media/AngusWorkspace/updated_XIT_soilsurface_qiime2_results -profile local --classifier /media/AngusWorkspace/gg-13-8-99-515-806-nb-classifier.qza --threads 30 -w /media/AngusWorkspace/run_Jake/work_xit_soil_surface





# Kuner

nextflow run main_qiime2.nf --reads '/s/angus/i/nobackup/data/raw_sequence_data/mega_tylan/16S_Kuner_soilcores/concat_fastq/*_cat_R{1,2}.fq.gz' --output /media/AngusWorkspace/updated_Kuner_soilcores_qiime2_results -profile local --classifier /media/AngusWorkspace/run_Jake/bioinformatic-nextflow-pipelines/gg-13-8-99-515-806-nb-classifier.qza --threads 8 -w /media/AngusWorkspace/run_Jake/work_soilcores_qiime

