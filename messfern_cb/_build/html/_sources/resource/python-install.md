# Python installation

## Installing jupyter notebook & other useful software packages

Based on instructions from Leo Borchert.

Here, I guide through the installation of the Python distribution conda (similar to mamba, micromamba, etc) and set up jupyter notebook. Once conda is installed, various useful software packages can be added. Let me know if you run into trouble with any of this.

## For Linux users:
### STEP 1		
Download miniconda installer from:
  https://docs.conda.io/projects/conda/en/latest/user-guide/install/linux.html 
Then, from the terminal run: 
  bash Miniconda3-latest-Linux-x86_64.sh 

### STEP 2		
After successful installation, run:
  conda --version
If the terminal does not recognize the conda command, add the path to conda by running the following command in your terminal: 
  export PATH=~/anaconda3/bin:$PATH

### STEP 3
Create a conda environment (feel free to choose your own name instead of `messfern_env` for your environment):
  conda create -n messfern_env python=3.7

### STEP 4
Activate the created conda environment:
  conda activate py3

### STEP 5
Install additional modules into the environment:
  conda install -c anaconda jupyter
  conda install -c anaconda numpy
  conda install -c anaconda xarray
  conda install -c anaconda scipy
  conda install -c anaconda pandas
  conda install -c anaconda matplotlib
  conda install -c anaconda pycnv
  conda install -c anaconda gsw

If `anaconda` doesn't work, try `conda-forge`.
  

### STEP 6
To start jupyter notebook, run (after activating your environment py3):
  jupyter notebook

or if you've installed jupyterlab, then
  jupyter lab

(For jupyterlab, you may additionally need to install packages: `jupyterlab nb_conda jupyter-book ipykernel nb_conda_kernels`)

## Some useful tips:

1.	Installation guide for Windows and Mac users:
  https://docs.conda.io/projects/conda/en/latest/user-guide/install/# 

2.	You can learn more about conda here:
  https://docs.conda.io/projects/conda/en/latest/ 

3.	Keep a copy of this conda cheat sheet ready:
  https://docs.conda.io/projects/conda/en/4.6.0/_downloads/52a95608c49671267e40c689e0bc00ca/conda-cheatsheet.pdf 

4.	You can learn more about jupyter notebook here:
  https://www.dataquest.io/blog/jupyter-notebook-tutorial/ 
  https://realpython.com/jupyter-notebook-introduction/ 

5.	To install additional packages into your conda environment you can search for the installation command in Google. Search:
  conda install <package_name>

6. If you don't already have python, you can follow instructions on the [Software Carpentry website](https://carpentries.github.io/workshop-template/install_instructions/#python).  Note that their instructions are based on using Anaconda which is *not* recommended for UHH-owned computers.  
