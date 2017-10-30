# FMRIPREP from poldracklab

BootStrap: docker
From: poldracklab/fmriprep:latest

%runscript
    exec /usr/local/miniconda/bin/fmriprep "$@"

%environment

%labels
Author zhifang.ye.fghm@gmail.com
Build-date 30/10/2017
Vendor Ubuntu:Xenial
Version 1.0.0-rc8

%post
    #------------------------------------------------------------------------------
    # Fix possible permission issue, from docker2singularity.sh code
    #------------------------------------------------------------------------------
    #find /* -maxdepth 0 -not -path '/dev*' -not -path '/proc*' -not -path '/sys*' -exec chmod a+r -R '{}' \;
    #find / -executable -perm -u+x,o-x -not -path '/dev*' -not -path '/proc*' -not -path '/sys*' -exec chmod a+x '{}' \;
    #------------------------------------------------------------------------------
    # Change timezone to Shanghai
    #------------------------------------------------------------------------------
    ln -fs /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
    dpkg-reconfigure --frontend noninteractive tzdata
    #------------------------------------------------------------------------------
    # Fix shared library libGL.so.1
    #------------------------------------------------------------------------------
    #ln -s /usr/lib/x86_64-linux-gnu/mesa/libGL.so.1 /usr/lib/x86_64-linux-gnu/libGL.so.1
