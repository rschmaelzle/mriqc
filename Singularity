# fmriprep from poldracklab
# used in CBLS server
# created by Zhifang Ye <zhifang.ye.fghm@gmail.com>
# 25/4/2017
# build size padding to 40000

BootStrap:docker
From:poldracklab/fmriprep:latest

%runscript

exec /usr/local/miniconda/bin/fmriprep "$@"

%post

#------------------------------------------------------------------------------
# fix any possible permission issue, from docker2singularity.sh code
#------------------------------------------------------------------------------
find /* -maxdepth 0 -not -path '/dev*' -not -path '/proc*' -not -path '/sys*' -exec chmod a+r -R '{}' \;

#------------------------------------------------------------------------------
# setup environment variables
#------------------------------------------------------------------------------
# FreeSurfer
export FSL_DIR=/usr/share/fsl/5.0
export OS=Linux
export FS_OVERRIDE=0
export FIX_VERTEX_AREA=
export FSF_OUTPUT_FORMAT=nii.gz
export FREESURFER_HOME=/opt/freesurfer
export SUBJECTS_DIR=$FREESURFER_HOME/subjects
export FUNCTIONALS_DIR=$FREESURFER_HOME/sessions
export MNI_DIR=$FREESURFER_HOME/mni
export LOCAL_DIR=$FREESURFER_HOME/local
export FSFAST_HOME=$FREESURFER_HOME/fsfast
export MINC_BIN_DIR=$FREESURFER_HOME/mni/bin
export MINC_LIB_DIR=$FREESURFER_HOME/mni/lib
export MNI_DATAPATH=$FREESURFER_HOME/mni/data
export FMRI_ANALYSIS_DIR=$FREESURFER_HOME/fsfast
export PERL5LIB=$MINC_LIB_DIR/perl5/5.8.5
export MNI_PERL5LIB=$MINC_LIB_DIR/perl5/5.8.5
export PATH=$FREESURFER_HOME/bin:$FSFAST_HOME/bin:$FREESURFER_HOME/tktools:$MINC_BIN_DIR:$PATH

# FSL
export FSLDIR=/usr/share/fsl/5.0
export FSLOUTPUTTYPE=NIFTI_GZ
export FSLMULTIFILEQUIT=TRUE
export POSSUMDIR=/usr/share/fsl/5.0
export LD_LIBRARY_PATH=/usr/lib/fsl/5.0:$LD_LIBRARY_PATH
export FSLTCLSH=/usr/bin/tclsh
export FSLWISH=/usr/bin/wish
export PATH=/usr/lib/fsl/5.0:$PATH

# AFNI
export AFNI_MODELPATH=/usr/lib/afni/models
export AFNI_IMSAVE_WARNINGS=NO
export AFNI_TTATLAS_DATASET=/usr/share/afni/atlases
export AFNI_PLUGINPATH=/usr/lib/afni/plugins
export PATH=/usr/lib/afni/bin:$PATH

# ANTs
export ANTSPATH=/opt/ants
export PATH=$ANTSPATH:$PATH

#C3D
export C3DPATH=/opt/c3d/
export PATH=$C3DPATH:$PATH

# Miniconda
export PATH=/usr/local/miniconda/bin:$PATH
export LANG=C.UTF-8
export LC_ALL=C.UTF-8

# Others
export MKL_NUM_THREADS=1
export OMP_NUM_THREADS=1
export CRN_SHARED_DATA=/niworkflows_data

#------------------------------------------------------------------------------
# add environment variables to /environment file
#------------------------------------------------------------------------------
echo "

# FreeSurfer
export FSL_DIR=/usr/share/fsl/5.0
export OS=Linux
export FS_OVERRIDE=0
export FIX_VERTEX_AREA=
export FSF_OUTPUT_FORMAT=nii.gz
export FREESURFER_HOME=/opt/freesurfer
export SUBJECTS_DIR=$FREESURFER_HOME/subjects
export FUNCTIONALS_DIR=$FREESURFER_HOME/sessions
export MNI_DIR=$FREESURFER_HOME/mni
export LOCAL_DIR=$FREESURFER_HOME/local
export FSFAST_HOME=$FREESURFER_HOME/fsfast
export MINC_BIN_DIR=$FREESURFER_HOME/mni/bin
export MINC_LIB_DIR=$FREESURFER_HOME/mni/lib
export MNI_DATAPATH=$FREESURFER_HOME/mni/data
export FMRI_ANALYSIS_DIR=$FREESURFER_HOME/fsfast
export PERL5LIB=$MINC_LIB_DIR/perl5/5.8.5
export MNI_PERL5LIB=$MINC_LIB_DIR/perl5/5.8.5
export PATH=$FREESURFER_HOME/bin:$FSFAST_HOME/bin:$FREESURFER_HOME/tktools:$MINC_BIN_DIR:$PATH

# FSL
export FSLDIR=/usr/share/fsl/5.0
export FSLOUTPUTTYPE=NIFTI_GZ
export FSLMULTIFILEQUIT=TRUE
export POSSUMDIR=/usr/share/fsl/5.0
export LD_LIBRARY_PATH=/usr/lib/fsl/5.0:$LD_LIBRARY_PATH
export FSLTCLSH=/usr/bin/tclsh
export FSLWISH=/usr/bin/wish
export PATH=/usr/lib/fsl/5.0:$PATH

# AFNI
export AFNI_MODELPATH=/usr/lib/afni/models
export AFNI_IMSAVE_WARNINGS=NO
export AFNI_TTATLAS_DATASET=/usr/share/afni/atlases
export AFNI_PLUGINPATH=/usr/lib/afni/plugins
export PATH=/usr/lib/afni/bin:$PATH

# ANTs
export ANTSPATH=/opt/ants
export PATH=$ANTSPATH:$PATH

#C3D
export C3DPATH=/opt/c3d/
export PATH=$C3DPATH:$PATH

# Miniconda
export PATH=/usr/local/miniconda/bin:$PATH
export LANG=C.UTF-8
export LC_ALL=C.UTF-8

# Others
export MKL_NUM_THREADS=1
export OMP_NUM_THREADS=1
export CRN_SHARED_DATA=/niworkflows_data

" >> /environment

#------------------------------------------------------------------------------
# mounting directory
#------------------------------------------------------------------------------
# use /etc/singularity/singularity.conf file to bind our server directory to image
# set enable overlay = yes and use bind dir = /seastor
