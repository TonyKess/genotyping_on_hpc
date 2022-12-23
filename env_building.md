This section details how to build the conda environments, download key software, and access supplementary information that is required for the HPC genotyping workflow. Let's set up our preferred conda channels - for bioinformatics we often rely on bioconda.

`conda config --add channels bioconda
conda config --add channels conda-forge`

Now we can start installing software needed! 
Ths first thing we'll want to do with our data is run quality and adapter trimming. We can use fastp to do this

`conda create -n fastp fastp -c bioconda`

Make an environment for alignment of reads to the reference genome, as well as working with genotype likelihoods in ANGSD. These are imported together to ensure version comaptibility between ANGSD and the corresponding htslib and samtools installs. 

`conda create -n align samtools htslib bwa bwa-mem2 angsd -c bioconda`
