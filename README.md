# Intro_to_NeuroHPC dd/mm/2020
An outline for a day of HPC training for neuroimaging 

# Goals
Introduction to the High Performance Cluster at the University of Arizona to help neuroimaging researchers from a wide range of backgrounds learn

- What the HPC is and the advantages it brings to their research

- How to gain access and take advantage of the HPC's resources

- How to utilize containers on the HPC to perform basic neuroimaging research

  


# Schedule (9:30-15:00; Venue ?)
- 9:00 - 9:30 Coffee and Registration

   

- 9:30 - 10:30 First section
   - Intro to HPC

      - What is an HPC and why should I care? 
      - What is the architecture?
     - Nodes (login, compute, gpu), memory, cpus
   
- Using Open On Demand
   
      - Introduction to accessing files, running Desktop and shell terminals on cluster.
   - brief overview of Jupyter notebooks
   
- **Practical 01- logging on to the HPC**
   
   [Practical 01: Logging on to HPC](https://github.com/chidiugonna/Intro_to_NeuroHPC/blob/master/Practical01.md)
   
   
   
- 10:00 - 10:15 Break

   

- 10:15 - 12:00

   - Using Software Modules

   - Options for building your own software

   - **Practical 02 - Using Software modules**

     [Practical 02: Software Modules](https://github.com/chidiugonna/Intro_to_NeuroHPC/blob/master/Practical02.md)

     

   - Using Containers - Why use containers?
     
     - Use Docker Containers with  Singularity
     - Use Pre-built singularity containers (Build your own, Obtain from others - Dianne Patterson)
     
   - **Practical 03 - Working with Containers on HPC**

     [Practical 03: Containers on the HPC](https://github.com/chidiugonna/Intro_to_NeuroHPC/blob/master/Practical03.md)

   - **Practical 03 Extra : Building your own singularity containers**

     [Practical 03_Extra : Build singularity containers](https://github.com/chidiugonna/Intro_to_NeuroHPC/blob/master/Practical03_extra.md) 

     

   - Uploading/Downloading Data and Dealing with Neuroimaging Data

      - HIPAA Compliance
      - BIDS
      - Download/upload methods

   - **Practical 04 - upload data to HPC, download results locally**

      [Practical 04: Upload and Download Data](https://github.com/chidiugonna/Intro_to_NeuroHPC/blob/master/Practical04.md)

      

   - **Practical 04 Extra- Convert Dicom data to BIDS**

     [Practical 04 Extra: BIDS Conversion](https://github.com/chidiugonna/Intro_to_NeuroHPC/blob/master/Practical04_extra.md) 

       

- 12:00 - 13:00 Lunch

   

- 13:00 - 14:00 
  
   - scripting multisubject analysis for neuroimaging
   
   - Using  existing neuroimaging containers 
   
   - **Practical 05: Example using docker image of fmriprep**
   
     [Practical 05 : Fmri Pipeline](https://github.com/chidiugonna/Intro_to_NeuroHPC/blob/master/Practical05.md) 
   
     
   
   - Scripting using custom-built containers using bash-scripts 
   
   - Leveraging nipype for neuroimaging scripting
   
   - **Practical 06: Example using prebuilt singularity image on diffusion pipeline**
   
     [Practical 06 : Diffusion Pipeline](https://github.com/chidiugonna/Intro_to_NeuroHPC/blob/master/Practical06.md) 
   
     
   
- 14:15 - 15:00
  
   - Using Jupyter notebooks for analysis and visualization
   
   - **Practical 07: Using Jupyter notebooks**
   
     [Practical 07 : Jupyter Notebook](https://github.com/chidiugonna/Intro_to_NeuroHPC/blob/master/Practical07.md) 
   
     
   
     
   
- Doors close at 16:00

# Additional Resources
- Research Bazaar Arizona
   - Annual Event is May 18-20
   - Weekly events Tuesday and Thursdays



### Acknowledgements

**Yaohui Ding** - Drawing attention to sylab tokens as a way of building singularity images on the HPC

**Dianne Patterson** - Constantly working to improve collaboration in the neuroimaging community through the biweekly BMW meetings (https://sites.google.com/a/email.arizona.edu/bmw/) and maintaining excellent documentation on the HPC (https://neuroimaging-core-docs.readthedocs.io/en/latest/) and on neuroimaging in general (https://neuroimaging-core-docs.readthedocs.io/en/latest/index.html) . 

