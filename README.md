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
```

```








# docker-ubuntu-snap
(Genomics) Dockerfile for running Snap (Scalable Nucleotide Alignment Program) - http://snap.cs.berkeley.edu/


## Building this image
```
git clone https://github.com/GELOG/docker-ubuntu-snap.git
cd docker-ubuntu-snap/
docker build --rm=true -t snap:1.0beta.15 .
```

## Running this image in a container
The default behavior is to print the arguments on the command line
```
docker run -ti --rm=true snap:1.0beta.15
```
