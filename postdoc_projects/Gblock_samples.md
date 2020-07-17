# Gblock


## Making classifier with Ec5001_sequence.fasta
conda activate qiime2-2019.10

qiime tools import   --type 'FeatureData[Sequence]'   --input-path spikein_85_otus.fasta   --output-path spikein_85_otus.qza

qiime tools import   --type 'FeatureData[Taxonomy]'   --input-format HeaderlessTSVTaxonomyFormat   --input-path spikein_85_otu_taxonomy.txt   --output-path spikein_ref-taxonomy.qza


/media/AngusWorkspace/Gblock/spikein_85gg_classifier_June2020.qza

# Standard classifier
nextflow run main_qiime2_gblock_test.nf --reads '/media/AngusStorage/Raw_Data_2020/Gblock_spikein_test_2020/concat_reads/*_cat_R{1,2}.fq.gz' --output /media/AngusWorkspace/Gblock/Gblock_qiime2_standard_classifier_no_trunc -profile local --classifier /media/AngusWorkspace/gg-13-8-99-515-806-nb-classifier.qza -resume --threads 12

# Spike in classifier
# Running with Paul's exercise
nextflow run main_qiime2_gblock_test.nf --reads '/media/AngusStorage/Raw_Data_2020/Gblock_spikein_test_2020/concat_reads/*_cat_R{1,2}.fq.gz' --output /media/AngusWorkspace/Gblock/updated_Gblock_qiime2 -profile local --classifier /media/AngusWorkspace/Gblock_spikein_test/spikein_85gg_classifier_June2020.qza -resume --threads 12
