# What is Snap ?
SNAP is a new sequence aligner that is 3-20x faster and just as accurate as existing tools like BWA-mem, Bowtie2 and Novoalign. It runs on commodity x86 processors, and supports a rich error model that lets it cheaply match reads with more differences from the reference than other tools. This gives SNAP up to 2x lower error rates than existing tools (in some cases) and lets it match larger mutations that they may miss. SNAP also natively reads BAM, FASTQ, or gzipped FASTQ, and natively writes SAM or BAM, with built-in sorting, duplicate marking, and BAM indexing.

SNAP was developed by a team from the UC Berkeley AMP Lab, Microsoft, and UCSF.

http://snap.cs.berkeley.edu/

# What is Docker?
Docker is an open platform for developers and sysadmins to build, ship, and run distributed applications. Consisting of Docker Engine, a portable, lightweight runtime and packaging tool, and Docker Hub, a cloud service for sharing applications and automating workflows, Docker enables apps to be quickly assembled from components and eliminates the friction between development, QA, and production environments. As a result, IT can ship faster and run the same app, unchanged, on laptops, data center VMs, and any cloud.

https://www.docker.com/whatisdocker/

## What is a Docker Image?
In Docker terminology, a read-only Layer is called an image. An image never changes.

https://docs.docker.com/terms/image/

## what is a Docker Layer?
When Docker mounts the rootfs, it starts read-only, as in a traditional Linux boot, but then, instead of changing the file system to read-write mode, it takes advantage of a union mount to add a read-write file system over the read-only file system. In fact there may be multiple read-only file systems stacked on top of each other. We think of each one of these file systems as a layer.

https://docs.docker.com/terms/layer/

# Dependencies
* [Docker](https://docs.docker.com/installation/)

# How to use this image?
### 1) Get the reference genome (or chromosome) and unzip it. 
```
mkdir /docker-volume/
wget -O /docker-volume/chr1.fa.gz http://hgdownload.cse.ucsc.edu/goldenPath/hg19/chromosomes/chr1.fa.gz
gzip -d /docker-volume/chr1.fa.gz
```
### 2) Index the reference genome (or chromosome)
```
docker run --rm=true -ti -v /docker-volume:/docker-volume gelog/snap index /docker-volume/chr1.fa /docker-volume/snap-index.chr1  
```
### 3) Get a genome (or chromosome)
```
wget -O /docker-volume/SRR062634.filt.fastq.gz ftp://ftp.1000genomes.ebi.ac.uk/vol1/ftp/data/HG00096/sequence_read/SRR062634.filt.fastq.gz
gzip -d /docker-volume/SRR062634.filt.fastq.gz
```
### 4) Align the genome (or chromosome) with snap
```
docker run --rm=true -ti -v /docker-volume:/docker-volume gelog/snap single /docker-volume/snap-index.chr1/ /docker-volume/SRR062634.filt.fastq -o /docker-volume/SRR062634.sam
```
