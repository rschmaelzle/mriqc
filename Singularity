# fmriprep from poldracklab
# build size padding to 16000

BootStrap: docker
From: poldracklab/fmriprep:latest

%runscript
    exec /usr/local/miniconda/bin/fmriprep "$@"

%labels
Maintainer zhifang.ye.fghm@gmail.com
Version 0.5.2

#%environment

%labels
Author zhifang.ye.fghm@gmail.com
Build-date 2/7/2017
Vendor Ubuntu
Version 0.5.2

%post
#------------------------------------------------------------------------------
# Fix possible permission issue, from docker2singularity.sh code
#------------------------------------------------------------------------------
find /* -maxdepth 0 -not -path '/dev*' -not -path '/proc*' -not -path '/sys*' -exec chmod a+r -R '{}' \;
find / -executable -perm -u+x,o-x -not -path '/dev*' -not -path '/proc*' -not -path '/sys*' -exec chmod a+x '{}' \;
# chmod +x /usr/local/miniconda/bin/*
#------------------------------------------------------------------------------
# Change timezone to Shanghai
#------------------------------------------------------------------------------
ln -fs /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
dpkg-reconfigure --frontend noninteractive tzdata
#------------------------------------------------------------------------------
# Fix missing libGL.so.1
#------------------------------------------------------------------------------
#apt-get update
#apt-get install -y libgl1-mesa-glx
#apt-get clean -y
