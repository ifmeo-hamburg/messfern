# Python packages


## Installing packages (Windows)

Ok, we are presuming some previous knowledge, but to help you get past some hurdles experienced, see tips below:

* If you try to run some code with an "import" line, and you get an error, this is likely because you don't have the package installed (on your computer) and python is trying to load it.  

- How to fix this (Windows): You need to install the package using conda.  If you're using "Anaconda", then find the Anaconda prompt in the application.  See how here: [https://saturncloud.io/blog/how-to-access-anaconda-command-prompt-in-windows-10-64bit/#2](https://saturncloud.io/blog/how-to-access-anaconda-command-prompt-in-windows-10-64bit/#2).  Then you need to install the missing package with conda.

Some packages you will need:

- [Gibbs Seawater Toolbox (GSW)](https://pypi.org/project/gsw/) - see installation instructions here
- [xarray](https://docs.xarray.dev/en/latest/getting-started-guide/installing.html#instructions) - see installation for xarray and necessary other packages (dask, netCDF4, bottleneck).  This is a *very useful* data format/package for netcdf files (many ocean/climate datasets).
<!--- [pyGMT](https://www.pygmt.org/latest/install.html) - a plotting package (like `matplotlib` and `cartopy`.  Please note, installation is *recommended* via a package/environment manager like `conda`.  If you are using `pip` to install, then read the troubleshooting section below as well.-->

You may also need:
- [pandas](https://pandas.pydata.org) - simpler than xarray.  Avoid, but may be needed.  
- [numpy](https://numpy.org/install/) - multi-dimensional arrays
- [matplotlib](https://matplotlib.org/stable/users/getting_started/) - plotting tools, similar to Matlab style
- [pycnv](https://pypi.org/project/pycnv/) - for importing Seabird format `*.cnv` datafiles

Potentially of interest:
<!-- - [ocean data parser](https://github.com/cioos-siooc/ocean-data-parser) - but only has pip install instructions [here](https://cioos-siooc.github.io/ocean-data-parser/dev/get_started/installation/).  If you've been using conda and you'd like to use pip instead, you can use conda to install pip.  See some info [here](https://stackoverflow.com/questions/19042389/conda-installing-upgrading-directly-from-github)-->

## Installing packages (Mac)

We need various packages as above.  For environment management, we use `conda` (or `mamba`, and their lightweight forms: `miniconda` and `micromamba`).  Some students also use `pipenv`, which you can explore on your own e.g. [here](https://docs.python-guide.org/dev/virtualenvs/).

```{seealso}
Managing environments with [conda](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html) or [mamba](https://mamba.readthedocs.io/en/latest/user_guide/mamba.html).  
```

Choose a directory where you will work on the python for this course.  Navigate to the directory in a terminal window.
The basic command is something like `conda create --name <my-env>`  where you replace `<my-env>` with the name of your environment.  Let's call it `messfern_env`.  But we'll try to install a lot of the necessary pieces at once:

### Create and then activate an environment `messfern_env`
```
conda create --name messfern_env 
conda install --channel conda-forge xarray gsw python pandas gsw numpy scipy cartopy matplotlib jupyterlab nb_conda ipykernel nb_conda_kernels 
conda activate messfern_env
```
<!--
### OR create and then activate an environment `messfern_env` using micromamba
```
micromamba create --channel conda-forge --name messfern_env xarray gsw python pandas gsw numpy scipy cartopy matplotlib jupyter notebook jupyterlab nb_conda jupyter-book ipykernel conda nb_conda_kernels
micromamba activate messfern_env
```
-->

```{note}
To install an individual package with conda, you can use

    conda install -c conda-forge <package>

where `conda-forge` is the "channel" of packages, meaning that specifying the name "anaconda" will try to find the package you're requested at a specified location or channel.  Another channel you might use is "anaconda".
```


We need a few more packages that seem to only have `pip` instructions
```
pip install pycnv
conda env export > environment.yml
```
Note that you should be within an activated conda environment before running the pip install command.

<!--
pip install git+https://github.com/cioos-siooc/ocean-data-parser.git-->

This has created a list of the current environment which you can get from this repository [environment.yml (repository)](https://github.com/ifmeo-hamburg/seaocn/blob/main/environment.yml).  If you download this into your working directory, you can activate the environment:
```
conda env create -f environment.yml
```
Then before you start working, activate the environment using
```
conda activate messfern_env
jupyter-lab
```

Now, when you start `jupyter-lab` you'll see that you can select the environment `messfern_env`.  Or, when you open an existing python notebook (`*.ipynb` file), in the upper right corner you can select the environment (e.g., `messfern_env` and tick the box to always open with preferred kernel).

```{note}
If it's been a while since you installed conda, you can update it with

    conda update -n base -c conda-forge conda

But your conda will tell you when you need to do this
```

```{note}
If you want to recreate your environment with conda, after adding a few things, you can do a

    conda deactivate
    conda remove --name messfern_env --all

And then start fresh with the `conda create` code above, appending the extra packages in the intial install.
```
<!-- micromamba env remove --name messfern_env -->
### Problems with jupyter-book and kernels

My jupyter-book didn't know about my environment `messfern_env`.  This should not be a problem for students, but is a problem when i want to execute this book (the course  notes) which contain packages that aren't in my base installation of python on my computer.
<!-- install python in base environment
micromamba install python=3.8
Didn't help with the nb_conda_kernels error (couldn't call conda)-->

```
pico $HOME/.jupyter/jupyter_config.json
```
and add the lines
```
{
  "CondaKernelSpecManager": {
    "kernelspec_path": "--user"
  }
}
```
After saving this, I was able to run
```
python -m nb_conda_kernels list
```
and it appeared to add my kernels.
<!-- python -m nb_conda_kernels.install --status --verbose -->

<!-- Conda no longer installs as kernel 
https://stackoverflow.com/questions/72226756/new-conda-environments-no-longer-being-recognised-in-jupyter-notebook 
python -m ipykernel install --user --name messfern_env --display-name "Python (messfern_env)"-->
<!--Installed kernelspec firstEnv in /Users/eddifying/Library/Jupyter/kernels/firstenv-->
<!-- See your jupyter paths
jupyter --paths -->
<!-- Useful micromamba info, micromamba list nb_conda_kernels-->
Then making the jupter book worked without errors.

<!--Problems with mamba https://github.com/mamba-org/mamba/issues/1403-->
```{seealso}
https://fcollonval.medium.com/conda-environments-in-jupyter-ecosystem-without-pain-e9fab3992fb7
```
(seaocn_env) 18:20 ~/Library/Mobile Documents/com~apple~CloudDocs/Work/teaching/SeaOcn-UHH $ python -m nb_conda_kernels list

## Environments

More advanced: It's best to work inside an environment.  This controls the version of each of the packages that you have installed, so that the code is more likely to run smoothly on another person's computer.  Some background on [conda environments](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html).

<!--## ADCP data

*This is a stub:* Likely looking package for handling `*.000` ADCP data files.
[pycurrents_ADCP_processing](https://github.com/IOS-OSD-DPG/pycurrents_ADCP_processing/).
-->

## Troubleshooting

Not finding kernels in jupyter, try
```
jupyter kernelspec list
```
On a mac, this is reading from `~/Library/Jupyter/kernels`.  In the directories (named according to the environment name) there is a `kernel.json` file.