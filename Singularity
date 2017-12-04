# FMRIPREP from poldracklab

BootStrap: docker
From: poldracklab/fmriprep:1.0.0-rc13

%post
################################################################################
# Install additional login shells for users that need them
################################################################################
yum -y install tcsh ksh zsh
 

 
################################################################################
# Create directories to enable access to common HPCC mount points
################################################################################
mkdir -p /mnt/home
mkdir -p /mnt/research
mkdir -p /mnt/research/schmaelzlelab
mkdir -p /mnt/dfs17
mkdir -p /mnt/ffs17
mkdir -p /mnt/local
mkdir -p /mnt/ls15
mkdir -p /opt/software
mkdir -p /mnt/home/schmaelz
 
