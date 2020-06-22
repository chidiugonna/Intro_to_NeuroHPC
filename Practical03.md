# Practical 03 : Containers on the HPC



## Objectives 03

- Use existing docker image to create a singularity container for neuroimaging analysis 
- Use existing Singularity container for neuroimaging analysis



### Exercise 03.A: Build Singularity Container from Docker Image

- Docker images are available on Docker Hub (https://hub.docker.com) - you will need to register to gain access to images. You will need to have some idea of what you are looking for in order to identify high quality images you can trust. On docker hub Docker images are also referred to as Containers.

- When you pull a docker image from the docker hub it is stored as a blob in your default location on the HPC at  `$HOME/.singularity` 

- Unfortunately the $HOME directory can only store about 50GB and so very quickly this will eat up your disk allocation

- Use the code below initially to set up a new Cache Directory for storing blobs. Insert the last line in yoiur $HOME/.bashrc file to default to this directory every time you start a new terminal

  ```
  NEWCACHEDIR=/xdisk/nkchen/chidi/.singularity
  mkdir -p $NEWCACHEDIR
  export SINGULARITY_CACHEDIR=$NEWCACHEDIR
  ```
  
- For this example we will use `docker://kaczmarj/mrtrix` - the owner (https://github.com/kaczmarj) of this repository has established pedigree in developing containers. 

- create the script below and run it in a command line terminal

  ```
  module load singularity
  
  export SINGULARITY_CACHEDIR=/xdisk/nkchen/chidi/.singularity
  
  SINGNAME=mrtrix3.sif
  DOCKERURI=docker://kaczmarj/mrtrix3
  singularity build $SINGNAME $DOCKERURI
  ```

- This will build a singularity image called `mrtrix3.sif` in the current directory

- This can be tested by running the following commands

- `singularity run mrtrix3.sif mrinfo --version` will display the version of mrinfo

- `singularity run mrtrix3.sif mrview` will run mrview. 

  NOTE : at the time of writing this , this container was not able to run under centos 6 in ocelote but it is expected that you will have access to centos 7 when this workshop takes place.

### Exercise 03.B: Using an existing Singularity container

- Using an existing singularity image to run neuroimaging applications

- This is straightforward and usually entails getting read and/or execute permissions to an existing singularity image that has been built elsewhere

- For this example you can use the provided in ./singularity-images/nklab-mrtrix-v0.3.sif

  ```
  module load singularity
  singularity run./singularity-images/nklab-mrtrix-v0.3.sif mrinfo --version
  ```
  
- This container again provides access to mrtrix - compare both versions of mrtrix supplied in docker and  in presupplied singularity

- Which version would be the best to use? Navigate here for more information https://github.com/MRtrix3/mrtrix3. Note that care has to be taken with what versions are used of neuroimaging software - see here https://www.mrtrix.org/2020/01/10/avoid-version-3-0-rc4-not-for-deployment/ and here https://surfer.nmr.mgh.harvard.edu/fswiki/ReleaseNotes for examples



### Exercise 03.C: Use unsupported module on HPC

- One suggestion that has been championed is to make singularity containers available globally to all 

- activate the unsupported module `module load unsupported` 

- the path `/unsupported/` is now available

- identify and run available singularity images using `ls /unsupported/singularity` 

  