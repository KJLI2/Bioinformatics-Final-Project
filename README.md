Evolutionary Study on Defensin Protein Conservation Across Tick Species

Pipeline:
1. Downloaded Entrez Direct to obtain sequences from NCBI using sh -c "$(curl -fsSL https://ftp.ncbi.nlm.nih.gov/entrez/entrezdirect/install-edirect.sh)"
2. Used Entrez Direct to obtain defensin sequences using
   </ENTREZ_DIRECT>
   efetch -db nuccore -id NC_051176.1 -format fasta -seq_start 96236740 -seq_stop 96275291 >> defensin_sequences.fasta
   fetch -db nuccore -id NW_024609880.1 -format fasta -seq_start 92058811 -seq_stop 92061911 >> defensin_sequences.fasta
   efetch -db nuccore -id NC_051154.1 -format fasta -seq_start 310944550 -seq_stop 310959889 >> defensin_sequences.fasta
   efetch -db nuccore -id NW_026085831.1 -format fasta -seq_start 92730987 -seq_stop 92743499 >> defensin_sequences.fasta
   efetch -db nuccore -id NW_027051223.1 -format fasta -seq_start 3311765 -seq_stop 3316716 >> defensin_sequences.fasta
