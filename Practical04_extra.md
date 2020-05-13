# Practical 2



## Objectives

Learn to pull existing docker containers for use on the HPC 



### Exercise : BIDS Conversion

- create a bash file on HPC tp create version of a custom container orbisys/bidsconvert:02 for bids conversion on the HPC

- **NOTE**: The DICOM files for this exercise have been provided with consent of the subject - in almost all cases you should NOT perform Bids conversion on the HPC but should do it locally

  ```
  #!/bin/bash
  module load singularity
  VER=0.2
  singularity build bidsconvert-${VER}.sif docker://orbisys/bidsconvert:${VER}
  ```

- make it executable then execute 

- Singularity container `bidsconvert-0.2.sif` should be created

- We will now convert a sample set of DICOMS to bids format, first we need to do a few preliminaries. Create an output folder `nifti` for your output and make it accessible

  ```
  mkdir -p nifti
  chmod -R 777 nifti
  ```

- Now create the json file `bids_config.json` for mapping DICOMS to bids

  ```
  {
      "descriptions": [
          {
          "dataType": "func",
          "modalityLabel": "bold",
          "customLabels": "task-rest",
          "criteria": {
              "SeriesDescription": "*FMRI*"
              }
          },
          {
          "dataType": "anat",
          "modalityLabel": "T1w",
          "criteria": {
              "SeriesDescription": "*MPRAGE*"
              }
          }
      ]
  }
  ```

  

- Now execute the following to perform the conversion

  ```
  #!/bin/bash
  module load singularity
  singularity run   -B $PWD:/mnt              \
                    -B /home/u8/chidiugonna/HPCWORKSHOP/data/DICOMS:/dicom         \
                    -B $PWD/nifti:/nifti         \
                    --cleanenv    \
                    bidsconvert-0.2.sif       \
                    python  /src/bidsconvert.py  \
                    --subject 001  --dicomdir /dicom --niftidir /nifti --bidsconfig /mnt/bids_config.json --overwrite True
  ```

  

- Ordinarilly you would perform this bids conversion on your local machine using singularity as above or docker as shown before and also perform some anonymization like defacing on the anatomicals before uploading to the HPC

  ```
  #!/bin/bash
  module load singularity
  singularity run --it --rm  -v $PWD:/mnt              \
                    -v /home/u8/chidiugonna/HPCWORKSHOP/data/DICOMS:/dicom         \
                    -v $PWD/nifti:/nifti         \
                    orbisys/bidsconvert:0.2       \
                    python  /src/bidsconvert.py  \
                    --subject 001  --dicomdir /dicom --niftidir /nifti --bidsconfig /mnt/bids_config.json --overwrite True
  ```

  

- Delete the temporary folders `logs` and `tmp_dcm2bids` once completed

  

- TODO: Complete bidspreprocess that also does defacing

