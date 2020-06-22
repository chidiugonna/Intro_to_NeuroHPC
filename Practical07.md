# Practical 07



## Objectives

use jupyter notebooks to visualize and analyse data



### Exercise: 

- create a bash file on HPC tp create version of a custom container orbisys/bidsconvert:02 for bids conversion on the HPC

  

- Installing kernels https://ipython.readthedocs.io/en/stable/install/kernel_install.html 

- using conda - https://sites.northwestern.edu/summerworkshops/resources/software-installation__trashed/adding-python-3-to-jupyter-notebooks/ 

- matlab - see https://am111.readthedocs.io/en/latest/jmatlab_install.html 

  ```
  pip install matlab_kernal
  
  python -m matlab_kernel install
  ```

  

- Python https://ipython.readthedocs.io/en/stable/install/kernel_install.html 

- Python quirks  - see pythonEnv notebook that queries paths

- looks like it has to be `module load python/3/3.5.5` on ocelote and elgato

- ​                        

```
 jupyter kernelspec list
Available kernels:
  ir           /home/u8/chidiugonna/.local/share/jupyter/kernels/ir
  julia-0.6    /home/u8/chidiugonna/.local/share/jupyter/kernels/julia-0.6
  julia-1.0    /home/u8/chidiugonna/.local/share/jupyter/kernels/julia-1.0
  julia-1.3    /home/u8/chidiugonna/.local/share/jupyter/kernels/julia-1.3
  matlab       /home/u8/chidiugonna/.local/share/jupyter/kernels/matlab
  bash         /cm/shared/uaapps/python/3.6.5/share/jupyter/kernels/bash
  python3      /cm/shared/uaapps/python/3.6.5/share/jupyter/kernels/python3

```



### Anaconda Python

n py373
conda install pykernel
python -m ipykernel install --user --name conda_py373 --display-name "Python py373"
Installed kernelspec conda_py373 in /home/u8/chidiugonna/.local/share/jupyter/kernels/conda_py373

  conda_py373    /home/u8/chidiugonna/.local/share/jupyter/kernels/conda_py373
  ir             /home/u8/chidiugonna/.local/share/jupyter/kernels/ir
  julia-0.6      /home/u8/chidiugonna/.local/share/jupyter/kernels/julia-0.6
  julia-1.0      /home/u8/chidiugonna/.local/share/jupyter/kernels/julia-1.0
  julia-1.3      /home/u8/chidiugonna/.local/share/jupyter/kernels/julia-1.3
  matlab         /home/u8/chidiugonna/.local/share/jupyter/kernels/matlab
  bash           /cm/shared/uaapps/python/3.5.5/share/jupyter/kernels/bash
  python3        /cm/shared/uaapps/python/3.5.5/share/jupyter/kernels/python3