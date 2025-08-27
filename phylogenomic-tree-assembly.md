# Phylogenomic tree assembly using pangenome
### We added a sixth genome (proposed outgroup) for phylogenomic analysis. See external-genomes-tree.txt file.
## 1. Get sequences for gene clusters (single copy core genes) 
```sh
anvi-get-sequences-for-gene-clusters -g GENOMES.db -p PANGENOME/PANGENOME-PAN.db -o organized-pan.fa --min-num-genomes-gene-cluster-occurs 6 -max-num-genes-from-each-genome 1 --max-functional-homogeneity-index 0.9 --min-geometric-homogeneity-index 1 --concatenate-gene-cluster
```
## 2. Generate phylogenomic tree 
```sh
iqtree -s organized-pan.fa -nt 6 -m WAG -bb 1000
```
## 3. Display tree
```sh
anvi-interactive -p phylogenomic-profile.coryne.db --manual -t organized-pan.fa.contree
```











