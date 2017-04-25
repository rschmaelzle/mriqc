# fmriprep from poldracklab
# used in CBLS server
# created by Zhifang Ye <zhifang.ye.fghm@gmail.com>
# 25/4/2017
# build size padding to 16000

BootStrap:docker
From:poldracklab/fmriprep:latest

%runscript
  exec /usr/local/miniconda/bin/fmriprep "$@"

%post
  ## fix any possible permission issue, from docker2singularity.sh code
  find /* -maxdepth 0 -not -path '/dev*' -not -path '/proc*' -not -path '/sys*' -exec chmod a+r -R '{}' \;
  ## mounting directory
  # use /etc/singularity/singularity.conf file to bind our server directory to image
  # set enable overlay = yes and use bind dir = /seastor

%environment
  # FreeSurfer
  FSL_DIR=/usr/share/fsl/5.0
  OS=Linux
  FS_OVERRIDE=0
  FIX_VERTEX_AREA=
  FSF_OUTPUT_FORMAT=nii.gz
  FREESURFER_HOME=/opt/freesurfer
  SUBJECTS_DIR=$FREESURFER_HOME/subjects
  FUNCTIONALS_DIR=$FREESURFER_HOME/sessions
  MNI_DIR=$FREESURFER_HOME/mni
  LOCAL_DIR=$FREESURFER_HOME/local
  FSFAST_HOME=$FREESURFER_HOME/fsfast
  MINC_BIN_DIR=$FREESURFER_HOME/mni/bin
  MINC_LIB_DIR=$FREESURFER_HOME/mni/lib
  MNI_DATAPATH=$FREESURFER_HOME/mni/data
  FMRI_ANALYSIS_DIR=$FREESURFER_HOME/fsfast
  PERL5LIB=$MINC_LIB_DIR/perl5/5.8.5
  MNI_PERL5LIB=$MINC_LIB_DIR/perl5/5.8.5
  PATH=$FREESURFER_HOME/bin:$FSFAST_HOME/bin:$FREESURFER_HOME/tktools:$MINC_BIN_DIR:$PATH
  export PATH FSL_DIR OS FS_OVERRIDE FIX_VERTEX_AREA FSF_OUTPUT_FORMAT FREESURFER_HOME SUBJECTS_DIR FUNCTIONALS_DIR MNI_DIR LOCAL_DIR FSFAST_HOME MINC_BIN_DIR MINC_LIB_DIR MNI_DATAPATH FMRI_ANALYSIS_DIR PERL5LIB MNI_PERL5LIB

  # FSL
  FSLDIR=/usr/share/fsl/5.0
  FSLOUTPUTTYPE=NIFTI_GZ
  FSLMULTIFILEQUIT=TRUE
  POSSUMDIR=/usr/share/fsl/5.0
  LD_LIBRARY_PATH=/usr/lib/fsl/5.0:$LD_LIBRARY_PATH
  FSLTCLSH=/usr/bin/tclsh
  FSLWISH=/usr/bin/wish
  PATH=/usr/lib/fsl/5.0:$PATH
  export PATH FSLDIR FSLOUTPUTTYPE FSLMULTIFILEQUIT POSSUMDIR LD_LIBRARY_PATH FSLTCLSH FSLWISH

  # AFNI
  AFNI_MODELPATH=/usr/lib/afni/models
  AFNI_IMSAVE_WARNINGS=NO
  AFNI_TTATLAS_DATASET=/usr/share/afni/atlases
  AFNI_PLUGINPATH=/usr/lib/afni/plugins
  PATH=/usr/lib/afni/bin:$PATH
  export PATH AFNI_MODELPATH AFNI_IMSAVE_WARNINGS AFNI_TTATLAS_DATASET AFNI_PLUGINPATH

  # ANTs
  ANTSPATH=/opt/ants
  PATH=$ANTSPATH:$PATH
  export PATH ANTSPATH

  #C3D
  C3DPATH=/opt/c3d/
  PATH=$C3DPATH:$PATH
  export PATH C3DPATH

  # Miniconda
  PATH=/usr/local/miniconda/bin:$PATH
  export PATH

  # Others
  LANG=C.UTF-8
  LC_ALL=C.UTF-8
  MKL_NUM_THREADS=1
  OMP_NUM_THREADS=1
  CRN_SHARED_DATA=/niworkflows_data
  export LANG LC_ALL MKL_NUM_THREADS OMP_NUM_THREADS CRN_SHARED_DATA

%test
  /usr/local/miniconda/bin/fmriprep -h
