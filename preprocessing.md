Raw sequence data requires pre-processing to be used in genotyping pipelines. You would think someone would have dealt with this issue in a single consolidated software package
by now, but no. So it's up to us to run a few convoluted steps to do this preprocessing ourselves! The scripts for running these on a SLURM cluster are listed in
<LOCATION FOR FUTURE TONY> .
This section provides links for running these tools in SLURM, and a bit of background on why we run them in a specific order.

First, we need to set up the directory structure:
  
```
mkdir sets
mkdir trim
mkdir align
mkdir angsd_out
mkdir gatk_out
mkdir phased
mkdir GWAS
mkdir PCANGSD_out 
```
We assume our reads are already hanging out in the aptly named
  
```
reads/
```

Go to the raw reads and use split to make set files for parallel SLURM jobs 

``` 
cd reads
  
ls *R1.fastq.gz | \
  sed 's/\_R1.fastq.gz//' > ../sets/aeipinds.tsv 

```

 Make/edit a file with parameters for analysis (WGSparams_aeip.tsv here), and use it for launching analyses via SLURM scheduling.
Launch the first script in the analysis pipeline, using default trimming parameters in [fastp](https://github.com/OpenGene/fastp) to remove adapter content, and add a sliding window function to remove polyG tails, as suggested by [Lou et al. 2022](https://doi.org/10.1111/1755-0998.13559). This script will be launched to run in parallel to run on all individuals, 200 at a time.

```
sbatch --export=ALL,set=aeipinds.tsv,paramfile=WGSparams_aeip.tsv 01_fastp_parallel.sh
```
  
  

