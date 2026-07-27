# 1: FASTQC (Sena Brandine G, Smith AD. Falco)

export PATH=/usr/bin:/arf/home/bcetiner/miniconda3/bin:$PATH
/fastqc -t 8 1.fq 2.fq -o /new qc folder

# 2: Trimmomatic (Anthony M. Bolger, Marc Lohse)

/trimmomatic PE -phred33 1.fastq 2.fastq  output_forward_paired.fq.gz output_forward_unpaired.fq.gz output_reverse_paired.fq.gz output_reverse_unpaired.fq.gz  ILLUMINACLIP:TruSeq3-PE.fa:2:30:10 LEADING:3 TRAILING:3 SLIDINGWINDOW:4:15 MINLEN:36

# 3 JELLYFISH (Guillaume Marcais and Carl Kingsford)

/jellyfish count -m 21 -s 2G -t 32 -C -o /newfolder.jf /1.fq 2.fq
/jellyfish histo -t 32 -h 10000 /newfolder.jf > .hist

# 4 GENOMESCOPE (Gregory W Vurture et al. 2017)

/genomescope2 -i /.hist -o /new_folder_genomescope_k21_p2 -k 21 -p 2 -n _p2

