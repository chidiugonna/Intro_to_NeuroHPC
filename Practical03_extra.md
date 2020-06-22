# Practical 03_Extra : Build Containers with Singularity



## Objectives 03_Extra

- Learn to build your own singularity containers using your own recipes




### Exercise 03_Extra.A: Build a container using Singularity Tokens

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

  

### Exercise 03_Extra.B: Build a Container using VirtualBox

- An alternative approach is to create a dedicated Virtual Machine to build singularity images

- A how-to guide is provided here [Singularity in Ubuntu VM.pdf](https://github.com/chidiugonna/Intro_to_NeuroHPC/blob/master/Singularity_in_Ubuntu_VM.pdf) 

- Another approach is documented by Dianne Patterson here using Cyverse

  

