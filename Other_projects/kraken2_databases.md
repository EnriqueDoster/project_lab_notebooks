
# On Noelle's server
## /home/noyes046/shared/databases/kraken2_databases
* number of sequences
```
stored_genomes/archaea/library.fna:535
stored_genomes/bacteria/library.fna:38237
stored_genomes/viral/library.fna:11953
stored_genomes/human/library.fna:639
stored_genomes/protozoa/library.fna:11167
stored_genomes/UniVec_Core/library.fna:3137
stored_genomes/UniVec/library.fna:6093

```

kraken2-build --download-taxonomy --db /home/noyes046/shared/databases/kraken2_databases/Rumen_kraken_v2_Nov2019/
kraken2-build --download-library archaea --db /home/noyes046/shared/databases/kraken2_databases/Rumen_kraken_v2_April2020/
kraken2-build --download-library bacteria --db /home/noyes046/shared/databases/kraken2_databases/Rumen_kraken_v2_April2020/
kraken2-build --download-library viral --db /home/noyes046/shared/databases/kraken2_databases/Rumen_kraken_v2_April2020/
kraken2-build --download-library human --db /home/noyes046/shared/databases/kraken2_databases/Rumen_kraken_v2_April2020/
kraken2-build --download-library protozoa --db /home/noyes046/shared/databases/kraken2_databases/Rumen_kraken_v2_April2020/
kraken2-build --download-library UniVec --db /home/noyes046/shared/databases/kraken2_databases/Rumen_kraken_v2_April2020/
kraken2-build --download-library UniVec_Core --db 

Archaea
Processed 368 projects (567 sequences, 956.23 Mbp)... done.
Bacteria
Processed 19362 projects (42231 sequences, 78.24 Gbp)... done.
Viral
Processed 9346 projects (11968 sequences, 314.85 Mbp)... done.
Human
Processed 1 project (639 sequences, 3.27 Gbp)... done.
Protozoa
Processed 40 projects (11167 sequences, 902.06 Mbp)... done.
For univec_vore and univec, there was a total of 9230 sequences included.
