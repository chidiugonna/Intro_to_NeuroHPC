# Practical 02 : Software Modules



## Objectives 02

- Explore how to use modules installed on the HPC
- Investigate some of the particulars of Python and Anaconda.




### Exercise 02.A: The module command 

- To find out what modules are available on the HPC, use the command below

  - `module avail`

    

  - To find out specific versions for a particular software then specify after avail e.g.

    `module avail python` 

    ```
    module avail python
    ------ /cm/shared/uamodulefiles ----------------
    python/2.7/2.7.14  python/2/2.7.14  python/3.5/3.5.5
    python/3.6/3.6.5   python/3/3.5.5  
    ```

    

- To load a module use the command  `module load` 

  - `module load python`  will load the latest version of python
  
  - `module load python/3/3.5.5` will load the specific version as specified by `module avail` above
  
    
  
- The `module load` construct essentially makes available the binaries and libraries for a particular software available on your path 

  - these modules are generally stored at `/cm/shared/uaapps/` on ocelote, so latest binary for `matlab` would be found here `/cm/shared/uaapps/matlab/r2020a/bin/matlab`
  - In theory you could path to the binaries directly but there are other nuances that behind the scenes get addressed which you may not be privy to, so best to always use module load.

  

### Exercise 02.B: Exploring Python

- Load a specific version of python  `$ module avail python/3/3.5.5` 

- standard packages locations and local package locations can be determined by using `$ pip list -v` - this will print out a large list! 

  - standard packages at `/cm/shared/uaapps/python/$VER/lib`  in this case VER=3.5.5
  - local packages at  `/home/u8/$USERID/.local/lib/python3.5` 

- To install a python library that is not available in standard path then use the `--user` parameter with `pip` 

- follow the steps below to use the --user to install MNE-Python https://pypi.org/project/mne/ 

  - one approach is to install a specific version to user directory

    `$ pip install --user mne==0.20.4`

  - another approach is to install and upgrade to latest version. The command below can also be used to upgrade after a specific version has already been installed as above.

    `$ pip install --upgrade --user mne`

-  Test the install by running python (from command line you will need to use python3 to run the right version of python. Python on its own will run python 2)

  - `python3`

  - `import mne`

    Should work without any errors

    


### Exercise 02.C: Exploring Anaconda

- Anaconda provides a convenient way of managing python-based neuroimaging and data analysis packages and their dependencies which avoids some of the complexities involved with installing python modules on the HPC without admin privileges.

-  Search for available packages on https://anaconda.org/ and installation is usually as simple as `$ conda install <package>`  or if using a channel like conda-forge `conda install -c conda-forge nibabel`

- To set up Anaconda on the HPC we can load the default version

  `$ module load anaconda`

- Then perform `conda init bash` and then open a new terminal. The command prompt should have `(base)`

  `(base) [chidiugonna@i0n8 bin]$ ` 

- **IMPORTANT**:

  - The snippet of code below is inserted by conda init into your ~/.bashrc file. Unfortunately this seems to interfere with Open On Demand on ocelote. Comment out or remove this code from the ~/.bashrc file and copy it into a seperate script which you can source whenever you want to use Conda in a terminal. For example if you store this code in a file called startConda.sh in your home dirtectory then you would source using a period as follows `$ . ~/startConda.sh `

    ```
    # >>> conda initialize >>>
    # !! Contents within this block are managed by 'conda init' !!
    __conda_setup="$('/cm/shared/uaapps/anaconda/2019.07/bin/conda' 'shell.bash' 'hook' 2> /dev/null)"
    if [ $? -eq 0 ]; then
        eval "$__conda_setup"
    else
        if [ -f "/cm/shared/uaapps/anaconda/2019.07/etc/profile.d/conda.sh" ]; then
            . "/cm/shared/uaapps/anaconda/2019.07/etc/profile.d/conda.sh"
        else
            export PATH="/cm/shared/uaapps/anaconda/2019.07/bin:$PATH"
        fi
    fi
    unset __conda_setup
    # <<< conda initialize <<<
    
    ```

    

- Confirm that python and pip are being called from anaconda path. Also useful to know what the default anaconda python version (will use this as base python for our new area )

  ```
  $ which python
  /cm/shared/uaapps/anaconda/2019.07/bin/python
  $ which pip
  /cm/shared/uaapps/anaconda/2019.07/bin/pip
  ```

  ```
  $ python -V
  Python 3.7.3
  ```

- Use `conda env list ` to see what environments have been created. The active environment has an asterix next to its location.

  ```
  $ conda env list
  # conda environments:
  #
  base                  *  /cm/shared/uaapps/anaconda/2019.07
  orange3                  /cm/shared/uaapps/anaconda/2019.07/envs/orange3
  rstudio                  /cm/shared/uaapps/anaconda/2019.07/envs/rstudio
                           /home/u8/chidiugonna/.julia/conda/3
                           /xdisk/nkchen/chidi/envs/py373
  ```

  

- Create a conda environment in $HOME/.conda/envs and activate it. Note you might have to deactivate the current environment `conda deactivate` before activating the new one

  ```
  conda create --name neuro python=3.7.3
  conda activate neuro
  ```

  For this example we will install fsleyes which 

  `conda install -c conda-forge fsleyes`

  To run fsleyes we just need to add the GL libraries on the library path as follows:

  `export LD_LIBRARY_PATH=/usr/lib64:$LD_LIBRARY_PATH`

- To remove an environment, then first you will need to make sure it is not the current environment by deactivating `conda deactivate`

  `conda remove --name dwi --all`

- An alternative approach to creating an environment avoids space restrictions on your $HOME directory by creating the environment on a high capacity disk. First create the folder that will contain environments:

  `mkdir -p /xdisk/nkchen/chidi/envs`

- Now to create your environment you will need to use the `--prefix` parameter with the fully qualified path and not `--name`

  `conda create --prefix /xdisk/nkchen/chidi/envs/py373 python=3.7.3` 

- To activate this new environment you will need to navigate directly to the location and then activate the environment 

  ```
  cd /xdisk/nkchen/chidi/envs/
  conda activate ./py373
  ```



