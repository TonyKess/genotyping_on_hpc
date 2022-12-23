Raw sequence data requires pre-processing to be used in genotyping pipelines. You would think someone would have dealt with this issue in a single consolidated software package
by now, but no. So it's up to us to run a few convoluted steps to do this preprocessing ourselves! The scripts for running these on a SLURM cluster are listed in
<LOCATION FOR FUTURE TONY> .
This section provides links for running these tools in SLURM, and a bit of background on why we run them in a specific order.

First, we need to set up the directory structure:
  
```
mkdir trim
mkdir align
mkdir angsd_out
mkdir phased
mkdir GWAS
mkdir PCANGSD_out 
```
