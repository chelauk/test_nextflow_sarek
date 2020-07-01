# test nextflow sarek
based on [nf-core/sarek](https://github.com/nf-core/sarek)
go here for documentation etc.

# A temporary repository to test preliminary nextflow pipeline for ngs

## Instructions for use on davros

* enter an interactive node 

* clone this repository:

`git clone https://github.com/chelauk/test_nextflow_sarek`

* change directory to the cloned directory

`cd test_nextflow_sarek`

* copy test control_bams folder into this folder from

`cp -r /home/cjames/Scratch/test_nextflow_sarek/control_bams/`

create folder eg `singularity` and copy singularity image into it (it can be anywhere)

`cp /home/cjames/Scratch/nextflow_pipelines/singularity/nfcore-sarek-dev.img .`

as long as you point have the cachedir variable in the environment

* export NXF_SINGULARITY_CACHEDIR variable in .bashrc

eg:

`export NXF_SINGULARITY_CACHEDIR=/mnt/scratch/DMP/EVGENMOD/cjames/nextflow_pipelines/singularity/`

* load nextflow

`module load nextflow/19.10.0`

* run this command

```
nextflow run sarek -profile test1,singularity \
 --intervals test-giab.bed \
 --step VariantCalling \
 --tools mutect2,platypus \
 --input test-bams.tsv
 ```
if you get 255 errors I am aware of them and working with ICR bioinformatics to solve them just resubmit with -resume

```
nextflow run sarek -profile test1,singularity \
 --intervals test-giab.bed \
 --step VariantCalling \
 --tools mutect2,platypus \
 --input test-bams.tsv \
 -resume
 ```
 
 
 follow instructions at https://tower.nf/ if you want realtime updates of the pipeline on your browser
 
 Hopefully the platypus command will be included in the official nf-core/sarek pipeline but this is a slow process and we need to get on with our version.
 
 
all results and reports will be in results folder

the whole pipeline can also be run using bsub 
