# fmriprep from poldracklab
# used in CBLS server
# created by Zhifang Ye <zhifang.ye.fghm@gmail.com>

BootStrap:docker
From:poldracklab/fmriprep:latest

%runscript
echo "This gets run when you run the image!" cd /code exec echo "Hello" "$@"

%post
# create /seastor for server directory binding
mkdir -p /seastor
