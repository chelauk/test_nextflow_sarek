# test nextflow sarek
based on [nf-core/sarek](https://github.com/nf-core/sarek)
go here for documentation etc.

A temporary repository to test preliminary nextflow pipeline for ngs

clone this repository

`git clone https://github.com/chelauk/test_nextflow_sarek`

`cd test_nextflow_sarek`

copy test control_bams into this folder from

`/home/cjames/Scratch/test_nextflow_sarek/control_bams`

create folder eg `singularity` and copy singularity image into it

`/home/cjames/Scratch/nextflow_pipelines/singularity/nfcore-sarek-dev.img`

export NXF_SINGULARITY_CACHEDIR variable in .bashrc

eg
`export NXF_SINGULARITY_CACHEDIR=/mnt/scratch/DMP/EVGENMOD/cjames/nextflow_pipelines/singularity/`

module load nextflow/19.10.0

run this command

```
nextflow run sarek -profile test1,singularity \
 --intervals test-giab.bed \
 --step VariantCalling \
 --tools mutect2,platypus
 ```
if you get 255 errors I am aware of them and working with ICR bioinformatics to solve them just resubmit with -resume

```
nextflow run sarek -profile test1,singularity \
 --intervals test-giab.bed \
 --step VariantCalling \
 --tools mutect2,platypus \
 -resume
 ```
 
 
 follow instructions at https://tower.nf/ if you want realtime updates of the pipeline on your browser
 
 Hopefully the platypus command will be included in the official nf-core/sarek pipeline but this is a slow process and we need to get on with our version.
 
 
