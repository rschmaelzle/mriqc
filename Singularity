# fmriprep from poldracklab
# used in CBLS server
# created by Zhifang Ye <zhifang.ye.fghm@gmail.com>

BootStrap:docker
From:poldracklab/fmriprep:latest

%runscript

exec /usr/local/miniconda/bin/fmriprep "$@"

%post

# fix any possible permission issue, from docker2singularity.sh code
find /* -maxdepth 0 -not -path '/dev*' -not -path '/proc*' -not -path '/sys*' -exec chmod a+r -R '{}' \;

# mounting directory
# use /etc/singularity/singularity.conf file to bind our server directory to image
# set enable overlay = yes and use bind dir = /seastor
# mkdir -p /seastor
