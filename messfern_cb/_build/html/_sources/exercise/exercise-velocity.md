# Exercise 3 - Plot velocity sections

**Aim:** The purpose of this exercise is to make a velocity section, as you might do after the Seepraktikum

**Context:** For this course, you can work with python either on your own computer, on the university computers or on Github Codespaces.  (Note, at this point, instructions are not yet verified for using python on the university computers which have recently removed `anaconda`.)

**Goals:** At the end of this exercise, you will be able to

- Load a `*.mat` matlab data file
- Plot sections of u- and v- velocity
- Convert time from Matlab format to python `xarray` format
- Control some figure plotting parameters like double y-axes and changing the position of a colorbar
<hr>

## Step 1: Github.com

Access the Github Classroom for this course using the link you received in Stine.

Click the link to start the assignment.  Here, you may need to create a github account if you don't already have one, or will link your account to your name.

## Step 2: Set up your working environment

Refer to instructions from last time [exercise-python](exercise-python.md) for starting with Git.

You'll be working with starter code at https://github.com/eleanorfrajka/messfern-plot-velo.

## Step 3: Start editing the code

1. Read each cell and follow the instructions.  

2. In the first cell, update the text to be your name and date.

3. The next cell (the first code cell) imports the packages you need.  You will likely need to add scipy.

4. The next set sets up paths to the directories.  Update these to match your computer.  Reminder that directories on Mac OSX use `/` while directories or folders on Windows use `\`.

5. Load the bathymetry data.  If you don't remember how to load a `*.nc` or netCDF file, see what we did last time.

6. Load velocity data from a `*.mat` file.  The tricky things here are importing the data (we use `scipy.io`), getting it into the right format (the lines like `ds['lat'][0][0]`), flattening the 2-dimensional data like latitude, longitude, depth and time which are really just 1-dimensional vectors (using `*.flatten()`), converting time from standard matlab time (fractional days since 0000-00-00 at 00:00:00) and then reshaping `u` and `v` into two-dimensional matrices or arrays.  *Recommended:* play around with the code and see how it breaks.  What happens in later cells if you don't flatten the data?  What happens if you reshape `u` the wrong way around (e.g., `time` before `depth`)?

7. Later cells show how to plot the data.  Special things to note:

- Using `*.twinx()` to add a second y-axis on a line plot
- How to fix the y-axis limits afterwards

8. There is an optional cell showing you how to turn the data you've extracted from the matlab file into an xarray dataset, which can then be exported (saved) as a netCDF file.

9. For the map, revisit last time to see how to add bathymetry under the location of the section.

10.  The velocity sections are plotted against time.  Extra challenge (but worthwhile!), calculate a distance vector (in units of kilometers) from one end of the section to the other.  Use the Gibbs Seawater toolbox to do this (hint: search gibbs seawater distance function).

## Step 4: Edit the readme file

Within your workspace, you'll find a file called `README.md`.  Open this file in a text editor (or code editor) of your choice.  It's written in markdown.  Follow the instructions within the file to update the file with your project name, notes to yourself on how you ran the code, and any further information as required.

For the purposes of this exercise, the `README.md` file serves as a coversheet for the work.

## Step 5: Submit the code on the Github classroom 


Ok - we haven't gone over this yet - we may have to wait until 2 weeks from now to try it.  If you have some familiarity with github, you can try to do this yourself. 

-- 
Navigate to your repository on Github.com.  

If you're using Github codespace, 

- In the left bar, find the circles connected by lines and click it.  
- For each of the changes noted, click the plus (+) symbol to 'stage' them for a commit.  
- Add a short note at the top saying what you've changed.
- Click "commit"
- Click "Sync changes"

Committing your repository is how you submit the exercise.  