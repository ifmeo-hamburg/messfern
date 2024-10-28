# Exercise 2 - Plot bathymetry 

**Aim:** The purpose of this exercise is to make a map of bathymetry

**Context:** For this course, you can work with python either on your own computer, on the university computers or on Github Codespaces.  (Note, at this point, instructions are not yet verified for using python on the university computers which have recently removed `anaconda`.)

**Goals:** At the end of this exercise, you will be able to

- Load a netCDF (`*.nc`) file with bathymetry data
- Plot a contour map of bathymetry
- Download and crop your own bathymetry region given latitude and longitude coordinates
- Control some figure output parameters (like the size of the figure generated)
<hr>

## Step 1: Github.com

Access the Github Classroom for this course using the link you received in Stine.

Click the link to start the assignment.  Here, you may need to create a github account if you don't already have one, or will link your account to your name.

## Step 2: Set up your working environment

Refer to instructions from last time (exercise-python)[exercise-python.md] for starting with Git.

You'll be working with starter code at https://github.com/eleanorfrajka/messfern-plot-bathy.


## Step 3: Start editing the code

Note that a jupyter notebook in python is organised in cells.  The cells in this notebook (`*.ipynb*) are either of type "Markdown" or "code". 

- For Markdown cells, these contain information about the preceding or following cells and use [Markdown](https://www.markdownguide.org) to format.  Hashtags are used for headers, and dashes for list items.  To **bold** text, surround the text to be bolded with two asterisks (*) on each side.  For *italic* text, use one.
    
- For code cells, try to figure out what it's doing.  Python is a programming language (like Matlab or Julia) which allows you to send a set of instructions to the computer, and to have it manipulate and display data to the screen.
        - Syntax matters.  Missing punctuation, change in capitalisation, the wrong kinds of brackets or the wrong indentation all matter.
        - Rather than having you code from scratch to start with (e.g., demonstrating how arithmatic works in Python) we are going to use sample code for you to edit.  The disadvantage is that you may not realise how many choices about punctuation and indentation are being made for you.  The advantage is that you can get to using Python for 'real stuff' quicker.  But be aware that you will have gaps in your basic understanding.  

To work through this exercise:

1. Read each cell and follow the instructions.  

2. In the first cell (Exercise 2: Bathymetry), update the text to be your name and date.  You may need to double-click the cell in order to edit.

3. In the next cell, you are importing packages to python.  Note that we are adding packages `netCDF4`, `cmocean` and `cartopy`, so you will need to add these.  We are additionally using a module `bathymetry.py` which you will have downloaded to your computer in step 2.  If you did not, then please download the git repository (Step 2) including the directories.

4. In the third cell (# Set some paths), this cell tells python where various files are located.  Update the `rootdir` to be the root directory (containing the sub-directories or folders `src/` and `data/`) corresponding to this assignment.  The command `os.chdir(rootdir)` changes the python working directory to be this directory.  (Alternative options exist, including adding necessary directories to your path - if you're a more advanced user, you can choose whichever option you prefer.)

5. The next section loads bathymetry data using `xarray` with the function `xr.open_dataset()`.  Note that we imported `xarray` with short form `xr` above so that we don't have to type `xarray.open_dataset()`.  The variable inside the brackets or parentheses `()` is a character string which tells python where to find the file `bathymetry_subset.nc`.  The `print()` command prints the contents of the variable after loading it.

6. The next section titled "Make a simple plot" shows two examples for making a contour plot in python.  The first uses the common plotting package `matplotlib` which we've imported as `plt`.  When you run the cell, it should generate a figure below.  The command `plt.savefig()` also creates a `*.png` file with the figure you've generated.  Read through the commands, and experiment with commenting them out (add a hashtag `#` at the front of a line) to see how this changes what the figure looks like.

7. The next cell repeats this but uses the package `cartopy`.  Cartopy is particularly good for making geographic maps as you can choose your projection.  Here we've chosen the Mercator projection.  The main effect is to adjust the aspect ratio (the ratio of a distance in x vs y) as well as to improve the tick labels to include degrees north and west.

8. Edit the cartopy cell to add some additional features in the plot, and change the display parameter.  The "extra challenge" is to use some additional coding to work with the bathymetry file to find where the depth is deepest, and then plot this on the map.

9. **Repeat** but downloading the global bathymetry map (using the `bathymetry.py` module) and then selecting your own region.  Try to pick an interesting location which is less than 1000km on each side, preferably in the aspect ratio of 16:26.

## Step 4: Edit the readme file

Within your workspace, you'll find a file called `README.md`.  Open this file in a text editor (or code editor) of your choice.  It's written in markdown.  Follow the instructions within the file to update the file with your project name, notes to yourself on how you ran the code, and any further information as required.

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