#################################################################
# Dockerfile
#
# Version:          1
# Software:         Samtools
# Software Version: 1.2
# Description:      Tools (written in C using htslib) for manipulating next-generation sequencing data
# Website:          https://github.com/samtools/samtools
# Tags:             Genomics
# Provides:         samtools 1.2
# Build Cmd:        docker build --rm -t jbrayet/samtools:1.2 .
# Pull Cmd:         docker pull jbrayet/samtools:1.2
# Run Cmd:          docker run --rm -it jbrayet/samtools <options> <files>
#################################################################

# Set the base image to Ubuntu
FROM ubuntu:14.04

################## BEGIN INSTALLATION ######################

RUN apt-get update && \
    apt-get install -y \
      wget \
      zip \
      cmake \
      zlib1g-dev \
      libncurses5-dev \
      libncursesw5-dev && \
    apt-get clean && \
    apt-get purge && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*


ENV ZIP=samtools-1.2.tar.bz2
ENV URL=https://github.com/BioDocker/software-archive/releases/download/samtools
ENV FOLDER=samtools-1.2
ENV DST=/tmp

RUN wget $URL/$ZIP -O $DST/$ZIP && \
    tar xvf $DST/$ZIP -C $DST && \
    rm $DST/$ZIP && \
    cd $DST/$FOLDER && \
    make && \
    make install && \
    cd / && \
    rm -rf $DST/$FOLDER

# CHANGE WORKDIR TO /DATA
WORKDIR /data

##################### INSTALLATION END #####################

# File Author / Maintainer
MAINTAINER Jocelyn Brayet <jocelyn.brayet@curie.fr>


