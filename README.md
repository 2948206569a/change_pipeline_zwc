# change_pipeline_zwc
scATAC
在snakemake基础上运行

1修改data path
cd ./ENCODE_scatac-master/config

cp samples.tsv samples.tsv.bad

printf '%s\t%s\t%s\t%s\n' Sample Modality Genome FASTQ_DIR > samples.tsv
printf '%s\t%s\t%s\t%s\n' AA9S 10x GRCh38 /home/data/XieWenHui/data/zwc/TCGA-4W-AA9S >> samples.tsv






2.dry run 测试通路
cd ./ENCODE_scatac-master/
snakemake -s workflow/Snakefile \
  -n -p -k \
  --cores 16 \
  results/AA9S/barcodes/barcodes.txt







3.正式运行
cd ./ENCODE_scatac-master

snakemake -s workflow/Snakefile \
  -p -k \
  --use-conda \
  --conda-frontend conda \
  --cores 16 \
  results/AA9S/barcodes/barcodes.txt
