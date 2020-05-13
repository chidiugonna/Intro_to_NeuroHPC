# Practical 5



## Objectives

Learn to pull existing docker bidsapps  containers for use on the HPC 



### Exercise: Using a BIDS app, FMRIPREP

- create a bash file on HPC tp create version of a custom container orbisys/bidsconvert:02 for bids conversion on the HPC

  ```
  #!/bin/bash
  module load singularity
  VER=20.0.7
  singularity build fmriprep-${VER}.sif docker://poldracklab/fmriprep:${VER}
  ```

  

- 