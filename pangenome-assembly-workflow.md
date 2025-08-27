# Corynebacterium pangenome assembly
## 1. Activate the appropriate environment
The pangenome is assembled using the Anvi'o developer environment, anvio-dev.
### Enter the anvio-dev environment
```sh
conda activate anvio-dev
```
## 2. Reformat fasta files of each genome
```sh
anvi-script-reformat-fasta C_durumJJ1.fna -o C_durumJJ1.fa --simplify-names 
```
## 3. Make a contig database for each genome
```sh
anvi-gen-contigs-database -f C_durumJJ1.fa -o C_durum_JJ1.db -n "C_durum_JJ1"
```
## 4. Run the following commands on each contig database
```sh
anvi-run-hmms -c C_durum_JJ1.db
anvi-run-ncbi-cogs -c C_durum_JJ1.db
anvi-run-kegg-kofams -c C_durum_JJ1.db
anvi-run-pfams -c C_durum_JJ1.db
```
## 5. Create an external genome text file to store genomes
```sh 
nano external-genomes.txt 
```
### External genomes storage file listed in repository for reference
## 6. Create a genomes storage database file
```sh
anvi-gen-genomes-storage -e external-genomes.txt -o GENOMES.db 
```
## 7. Run the pangenome analysis
```sh
anvi-pan-genome -g GENOMES.db -n GENOME
```
## 8. Compute genome similarity
```sh
anvi-compute-genome-similarity -e external-genomes.txt -o PAN_OUT -p PANGENOME/PANGENOME-PAN.db
```
## 9. Display pangenome
```sh
anvi-display-pan -p PANGENOME/PANGENOME-PAN.db -g GENOMES.db
```
## 10. Download raw data from the genomes
```sh
anvi-summarize -p PANGENOME/PANGENOME-PAN.db -g GENOMES.db -C default
```
### This generates a .txt.gz file in the new directory, deliminated by -o
-C is the collection name, use --list-collections to show available collections

