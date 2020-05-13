# Practical 7 Extra



## Objectives

Learn to build your own singularity containers using your own recipes



### Exercise: Build a container using Singularity Tokens

- create an account with sylabs cloud at https://cloud.sylabs.io/builder 

- To build remotely directly on HPC - then create a token and give it a label https://cloud.sylabs.io/auth

- copy token onto clipboard

- in HPC rmote connect to Sylab

  ```
  singularity remote login SylabsCloud
  ```

  

- Paste the Key when prompted

  ```
  INFO:    Authenticating with remote: SylabsCloud
  Generate an API Key at https://cloud.sylabs.io/auth/tokens, and paste here:
  API Key: 
  ```

- if successful then successful message

  ```
  INFO:    API Key Verified!
  ```

- Now build a test container and test

  ```
  singularity build --remote lolcow2.sif lolcow.def
  ```

  ```
  singularity run lolcow2.sif
  ```

  

### Exercise: Build a Container using VirtualBox

- create a bash file on HPC tp create version of a custom container orbisys/bidsconvert:02 for bids conversion on the HPC

- bbvb

