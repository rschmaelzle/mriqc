# fmriprep from poldracklab
# used in CBLS server
# created by Zhifang Ye <zhifang.ye.fghm@gmail.com>

BootStrap:docker
From:poldracklab/fmriprep:latest

%runscript
echo "This gets run when you run the image!" cd /code exec echo "Hello" "$@"

%post
# use /etc/singularity/singularity.conf file to bind our server directory to image
# set enable overlay = yes and use bind dir = /seastor
