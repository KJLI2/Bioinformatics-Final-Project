Evolutionary Study on Defensin Protein Conservation Across Tick Species

Pipeline:
1. Made new directory called finalproject and moved into new directory
   
   mkdir finalproject and then cd finalproject
   
2. Downloaded Entrez Direct to obtain sequences from NCBI
   
   sh -c "$(curl -fsSLhttps://ftp.ncbi.nlm.nih.gov/entrez/entrezdirect/install-edirect.sh)"
   
3. Used Entrez Direct to obtain defensin sequences and placed into a new file called defensin_sequences.fasta using

   </ENTREZ_DIRECT>
	
   efetch -db nuccore -id NC_051176.1 -format fasta -seq_start 96236740 -seq_stop 96275291 >> defensin_sequences.fasta
   
   fetch -db nuccore -id NW_024609880.1 -format fasta -seq_start 92058811 -seq_stop 92061911 >> defensin_sequences.fasta
   
   efetch -db nuccore -id NC_051154.1 -format fasta -seq_start 310944550 -seq_stop 310959889 >> defensin_sequences.fasta
   
   efetch -db nuccore -id NW_026085831.1 -format fasta -seq_start 92730987 -seq_stop 92743499 >> defensin_sequences.fasta
   
   efetch -db nuccore -id NW_027051223.1 -format fasta -seq_start 3311765 -seq_stop 3316716 >> defensin_sequences.fasta
   
4. Used MAFFT to align sequences and saved in aligned_sequences.fasta

   mafft --auto defensin_sequences.fasta > aligned_sequences.fasta
   
5. Downloaded IQTREE

wget https://github.com/iqtree/iqtree2/releases/download/v2.2.2/iqtree-2.2.2-Linux.tar.gz
--2024-12-03 22:02:29--  https://github.com/iqtree/iqtree2/releases/download/v2.2.2/iqtree-2.2.2-Linux.tar.gz

6. Used IQTREE to generate a phylogeny tree

./iqtree2 -s ../../aligned_sequences.fasta -m TEST -bb 1000 -nt AUTO

7. Renamed the accession numbers with the appropriate species name

nano aligned_sequences.fasta.contree

8. Displayed the contents of aligned_sequences.fasta.contree with cat
   
cat aligned_sequences.fasta.contree

9. Prepared R to open contree
library(ape)
library(ggtree)

10. Visualzed tree on R

shh_tree <- "(Rhipicephalus_sanguineus:0.1805648827,Ixodes_scapularis:0.2957665347,((Dermacentor_silvarum:0.2230923568,Dermacentor_andersoni:0.2029175234)100:0.4927511056,Dermacentor_albipictus:0.3844533755)100:0.1097124366);"

shh_tree <- read.tree(text = shh_tree)
