# Exercise 1 - Plot profiles in python


**Aim:** The purpose of this exercise is to get python running.

**Context:** For this course, you can work with python either on your own computer, on the university computers or on Github Codespaces.  (Note, at this point, instructions are not yet verified for using python on the university computers which have recently removed `anaconda`.)

**Goals:** At the end of this exercise, you will be able to

- Run python with jupyter notebooks 
- Load a netCDF (`*.nc`) file with CTD data
- Plot a profile of temperature and salinity

<hr>

## Step 1: Github.com

Access the Github Classroom for this course using the link you received in Stine.

Click the link to start the assignment.  Here, you may need to create a github account if you don't already have one, or will link your account to your name.

## Step 2: Choose where to work on the assignment



### Option 1: Work on the assignment on your own computer.

Getting started with this option.

Copy the code from [https://github.com/eleanorfrajka/messfern-plot-profiles](https://github.com/eleanorfrajka/messfern-plot-profiles) to your local computer.  There should be a 'download' option if you click the green button that says "<> Code".  Save it to the directory you'd like to work in.

*Advanced:* Instead of copying the code, clone it using Github or git, which will create it as a git repository on your computer.

Then:
- Activate your conda environment (exact steps depend on how you'll use python: e.g., pycharm, spyder, anaconda)
- Rename the example notebook in `src/` with your lastname instead of "Lastname".
- Start an editor and open the example notebook within `src/`
- Select the kernel with your packages/environment installed
- Try running the code (normally a "run" button at the top, or to the left of each cell)

### Option 2: Github codespaces

Getting started with this option.

For this option, you will want to start Github codespace within the assignment you've accepted.

**First step:** Commit any changes to the repository.

**Second step:** Follow the steps below to run and edit the code.


- Navigate to the python notebook example within `src/`.  
- At the right, choose the kernel.  It may say 'python' or 'kernel'.
- In the center dropdown, choose "select another kernel"
- Choose "python environments"
- Choose "create a python environment"
- Choose "Conda creates a `.conda` environment in the current workspace"
- Select the version of python to install: python 3.9. **The first time will take a while since it will try to install packages that you need. Watch the "Go To" button at the top, or the pop up windows in the bottom right.  Check for errors and follow instructions.**
- Try the "Run all" button at the top.  This will throw an error about missing packages. 
- In the terminal window at the bottom of the page, click terminal, and then install the packages.  This can be done one by one or all together, e.g.,
    conda install -c conda-forge matplotlib
    conda install -c conda-forge xarray
or
    conda install -c conda-forge matplotlib xarray gsw numpy
etc

Note that the option `-c conda-forge` tells the installer to look for the packages on the `conda-forge` (which is needed especially for the gibbs seawater toolbox, `gsw`.)
- In the terminal window, install the package ctd-tools
    pip install ctd-tools
- Try running the code again

```{tip}
Note: If you get the error 
    notebook controller is DISPOSED. 
    View Jupyter <a href='command:jupyter.viewOutput'>log</a> for further details.
when clicking `Run all`, try again but running one cell at a time.
```

## Step 3: Start editing the code

Note that a jupyter notebook in python is organised in cells.  The cells in this notebook (`*.ipynb*) are either of type "Markdown" or "code". 

- For Markdown cells, these contain information about the preceding or following cells and use [Markdown](https://www.markdownguide.org) to format.  Hashtags are used for headers, and dashes for list items.  To **bold** text, surround the text to be bolded with two asterisks (*) on each side.  For *italic* text, use one.
    
- For code cells, try to figure out what it's doing.  Python is a programming language (like Matlab or Julia) which allows you to send a set of instructions to the computer, and to have it manipulate and display data to the screen.
        - Syntax matters.  Missing punctuation, change in capitalisation, the wrong kinds of brackets or the wrong indentation all matter.
        - Rather than having you code from scratch to start with (e.g., demonstrating how arithmatic works in Python) we are going to use sample code for you to edit.  The disadvantage is that you may not realise how many choices about punctuation and indentation are being made for you.  The advantage is that you can get to using Python for 'real stuff' quicker.  But be aware that you will have gaps in your basic understanding.  

To work through this exercise:

1. Read each cell and follow the instructions.  


2. In the first cell (Exercise 1: Profile data), update the text to be your name and date.  You may need to double-click the cell in order to edit.

3. In the next cell, you are importing packages to python.  You likely do not need to edit this, but note that each package name is imported using the command `import` which then makes the package contents "known" to your python code.

4. In the third cell (# Input file paths), the lines starting with a hash indicate that this is a comment.  Python will not try to execute this line but will instead skip it.  Comments are for the reader/programmer to explain what is happening in the code.  Use them often!

    This cell tells python where various files are located, and saves the text string with that location to a variable name, e.g., `cnv_file_with_path`.  That way, you don't have to type the long string with the location multiple times.

5. The next section is titled "Transforming to xarray".  This reads the data from the native format provided by the manufacturer (in the case, Seabird Electronics, Inc) and converts it into a netCDF file (a common data format used in oceanography and climate science) using a package written by a UHH student Yves Sorge.

6. The section "Open file and show contents" then reads this netCDF data into a data type within Python called an `xarray` dataset.  This data type is enabled by you having loaded the `xarray` package a few cells above, and has the advantage of reading netCDF files easily, and preserving the information contained within the file (which includes data variables, meta data).  The `xarray` package also has useful features for working with e.g., 1-, 2-, 3-, and 4-dimensional datasets, especially ones which use time as an index.

    Note the line: `print(ctd_ds.info)` which prints to the screen some fo the data contained within the `xarray` dataset which we've named here as `ctd_ds`.

7. The code below goes through some basic plotting routines.  **Your task** is to edit this code according to the instructions, to get familiar with the `matplotlib` package.  To figure out how to do this, refer to the [Matplotlib website](https://matplotlib.org/stable/gallery/index) and use internet searches or your colleagues.

## Step 4: Edit the readme file

Within your Github Classroom workspace, you'll find a file called `README.md`.  Open this file in a text editor (or code editor) of your choice.  It's written in markdown.  Follow the instructions within the file to update the file with your project name, notes to yourself on how you ran the code, and any further information as required.

For the purposes of this exercise, the `README.md` file serves as a coversheet for the work.

## Step 5: Submit the code on the Github classroom 

Navigate to your repository on Github.com.  

If you're using Github codespace, 

- In the left bar, find the circles connected by lines and click it.  
- For each of the changes noted, click the plus (+) symbol to 'stage' them for a commit.  
- Add a short note at the top saying what you've changed.
- Click "commit"
- Click "Sync changes"

Committing your repository is how you submit the exercise.  