# Practical 1



## Objectives

- Explore several ways of logging on to the HPC
- Appreciate the distinction between compute and login nodes
- Get a quick introduction to how commands are made on the HPC and how resources are requested
- Explore some of the features of Open On Demand

More documentation here https://public.confluence.arizona.edu/display/UAHPC 



### Exercise

- Log on using Open On Demand (Graphical, Interactive Compute Node)

  - Request a 2 hour session with multiple cpus

  - Open a terminal, notice that you are in a compute node

  - Run matlab

    ```
    module load matlab
    matlab
    ```

    

- Log on using Cluster link (Login node)

  - Start an interactive compute node in Cluster link using qsub 

    ```
    qsub -I -N interactive -m bea -M yourname@emailaddress -W group_list=yourPIid -q standard -l select=1:ncpus=1:mem=6gb -l cput=4:0:0 -l walltime=4:0:0
    ```

    qsub will be covered in a little more detail later 

  - Notice you are now in compute node - run matlab in command line mode and exit

  - A few commands to explore

    ```
    va
    qstat -san 
    uquota
    ```

    

- Open Jupyter Notebook
- Browse file system