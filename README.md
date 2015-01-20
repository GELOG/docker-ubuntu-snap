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
