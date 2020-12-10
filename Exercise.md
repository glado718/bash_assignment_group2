#!/bin/bash
### Bash Group Exercise

#Use the data in this [link](https://github.com/kipkurui/Intro2Linux2019/raw/master/Data/protein.fa.gz) for this exercise.

#Create a new project, complete with all the directories you would need for a reproducible project. Which commands did you use?
#From the home directory;
mkdir -p group2/assignments/intro2programming/bashassignment

#Using the command line, download and uncompress the data into the appropriat directory
cd group2/assignments/intro2programming/bashassignment
wget https://github.com/kipkurui/Intro2Linux2019/raw/master/Data/protein.fa.gz
gunzip protein.fa.gz

#From the file `protein.fa`, create a new FASTA file which only contains uncharacterized proteins, and a clean FASTA file without uncharacterized sequences
awk '{RS=">"; FS="\n";}{if ($1~/uncharacterized/) {print RS$0}}' protein.fa > uncharacterized.fa
grep -v "uncharacterized" protein.fa > clean.fa

#Create a new file which only contains raw sequences without the identifying information, or new lines. How many amino acids are in this new file?
grep -v ">" protein.fa >rawseq.fa
grep -v "^>" protein.fa | wc -c


