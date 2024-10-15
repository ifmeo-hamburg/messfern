# Exercise 0 - Python


**Aim:** The purpose of this exercise is to get python running.

**Context:** For this course, you can work with python either on your own computer on the university computers.  Note, at this point, instructions are not yet verified for using python on the university computers.

**Goals:** At the end of this exercise, you will be able to

- Run python with jupyter notebooks 
- (Optional) Run jupyter-lab
- (Optional) Create and use `conda` to manage environments
- Install python packages (e.g., `gsw`, `pandas`, `xarray`)


<hr>

## Step 0: Create a working folder for this class

Create a folder somewhere on your computer where you'll work on python for this class.  Name it something that you can remember.  Save your work (jupyter notebooks) in this location.

Within this folder, create a text file named `readme.md` to record the steps you take to get python installed and to start jupyter.

## Step 1: Check whether you have python installed

In Mac or Linux, at the command line, type
```
python --version
```

For example, mine says
```
(base) 9:34 ~ $ python --version
Python 3.9.5
```

If it's not installed, see: [Python installation](../resource/python-install).

Once you verify that python is installed, you have two options for moving forward:
- Get jupyter running on your computer.
- (Optional) Environment management with conda (and jupyter lab) [below](#slightly-more-advanced-step-2-setting-up-a-conda-environment)
*Either* option is acceptable for this course.


```{seealso}
- [Jupyter notebook v Jupyter lab (external)](https://saturncloud.io/blog/what-is-the-difference-between-jupyter-notebook-and-jupyterlab/#:~:text=If%20you%20are%20already%20familiar,is%20the%20way%20to%20go.)
```


## Step 2: Conda environment 

Conda environments are a way to manage different installations of packages for different projects.  This can help avoid incompatibilities between various packages (but which aren't all needed for a piece of code), or to specify which version of python you were running when you wrote some code, so that 10 years down the line if it doesn't work with the most modern python, you have a chance of reverting to an earlier version.

Start by reading the basics about [conda environments (external link)](https://carpentries-incubator.github.io/introduction-to-conda-for-data-scientists/02-working-with-environments/index.html#:~:text=Key%20Points-,A%20Conda%20environment%20is%20a%20directory%20that%20contains%20a%20specific,activate%20(%20conda%20deactivate%20)%20commands.).  

```{note}
Key points from the link above:
- A Conda environment is a directory that contains a specific collection of Conda packages that you have installed.
- You create (remove) a new environment using the `conda create` (`conda remove`) commands.
- You activate (deactivate) an environment using the `conda activate` (`conda deactivate`) commands.
- You install packages into environments using `conda install`; you install packages into an *active* environment using `pip install`.
- You should install each environment as a sub-directory inside its corresponding project directory
- Use the `conda env list` command to list existing environments and their respective locations.
- Use the `conda list` command to list all of the packages installed in an environment.
```

- For Mac users, you will probably want `conda` and `pip` installed on your computer.

You can get conda here: [https://conda.io/projects/conda/en/latest/user-guide/install/index.html](https://conda.io/projects/conda/en/latest/user-guide/install/index.html).  I would recommend *miniconda* (Here is the direct link for [installing miniconda](https://docs.anaconda.com/free/miniconda/miniconda-install/)).  If you already have Anaconda, that is fine too.

- To create an environment to use for the work in this course, use the `conda create` command as in 
[Python packages](../resource/python-packages).
<!--conda create --channel conda-forge --name seaocn_env xarray python pandas gsw dask netCDF4 bottleneck numpy matplotlib jupyterlab nb_conda jupyter-book ipykernel nb_conda_kernels pygmt cartopy scipy cmocean erddapy argopy tqdm-->
Note that it can be advantages to install all your packages at once since `conda` (or `mamba`) need to cross-check packages for compatibility upon installation.

- Then activate the environment:
```
conda activate messfern_env
```

## Step 3: Get Jupyter running

- Install either [jupyterlab or jupyternotebook](https://docs.jupyter.org/en/latest/#where-do-i-start).

```{note}
If you already have Anaconda, then jupyter lab comes by default as [explained here](https://test-jupyter.readthedocs.io/en/latest/install.html).
```

- Get Jupyter running on your computer.  The specific steps will depend on how it's been installed.  See instructions [here (external)](https://docs.jupyter.org/en/latest/running.html).  

- Record the steps you need to take to start jupyter!   **Specifically, put these steps into a `readme.md` within your working folder.**.


## Step 4: Create a new python notebook

- Create a new  notebook following the file-naming convention.

```{admonition} Naming convention: Zeroeth notebook
Name your notebook following the convention `Ex<A>-<Lastname>-messfern.ipynb` where you replace the `<A>` with the exercise number (or number/letter combo), and `<Lastname>` with your lastname.
```

- Within this notebook, create a first cell to import the packages we'll be using during this course.  This starter example should have:

```{code}
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import xarray as xr
import gsw
import pycnv
```

If any of these packages fail to run, then first *check which kernel you're using*. You want to use the kernel corresponding to the conda environment you created, `messfern_env`.  This should be available from where you can edit the python notebook, as a dropdown menu in the upper right corner.  Or revisit your installations, or [python packages](../resource/python-packages) for tips on how to install them.


- Now add a cell above your `import` cell, and change the format of the cell from "code" to "markdown".  Within this markdown cell, add some text, for example:

```{code}
# My Messfern python notebook

- Author: <My name>
- Purpose: Verify package installation
- Date: <Today's date>

This **worked**!  But *not sure* what to do next.

<hr>
```

After adding text to the cell, run it as you would a python code cell.  Note that running the cell changes the formatting based on the markdown formatting commands you've provided.