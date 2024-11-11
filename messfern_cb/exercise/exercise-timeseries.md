# Exercise 4 - Plot time series data

**Aim:** The purpose of this exercise is to make time series plots as from a moored instrument.

**Context:** For this course, you can work with python either on your own computer, on the university computers or on Github Codespaces.  (Note, at this point, instructions are not yet verified for using python on the university computers which have recently removed `anaconda`.)

**Goals:** At the end of this exercise, you will be able to

- Load a `*.nc` file containing velocity and one containing CTD information
- Plot time series of salinity and of u- and v- velocity
- Fit a tidal harmonic to the time series
<hr>

## Step 1: Github.com

Access the Github Classroom for this course using the link you received in Stine.

Click the link to start the assignment.  Here, you may need to create a github account if you don't already have one, or will link your account to your name.

## Step 2: Set up your working environment

Refer to instructions from before [exercise-python](exercise-python.md) for starting with Git.

You'll be working with starter code at https://github.com/eleanorfrajka/messfern-plot-timeseries.

## Step 3: Start editing the code

1. Read each cell and follow the instructions.  

2. In the first cell, update the text to be your name and date.

3. The next cell (the first code cell) imports the packages you need.  You will likely need to add scipy.

4. The next set sets up paths to the directories.  Update these to match your computer.  Reminder that directories on Mac OSX use `/` while directories or folders on Windows use `\`.

5. Load the CTD data.  Here, `xr.open_dataset()` is handy for handling `*.nc` netCDF files.

6. Make a simple plot of practical salinity.  Recall that for archiving data, we use practical salinity (`.PSAL` in this file) to record salinity, even though "absolute salinity" is what we should use for onward calculations.

7. Compute and plot absolute salinity, using the Gibbs Seawater toolbox `gsw`.  Take a look at how much they differ.  

    - Calculate the difference and plot it.


8. There are strong tides in the North Sea region.  In order to fit a tidal signal neatly, we will convert the time format from `datetime64[ns]` into a numeric value with units of days.  There are two lines of code in here, one to create `time_in_days1` and one to create `time_in_days2`.  From reading the line of code, it would appear that either should give us time in units of days.  Only one of them is correct.  The other produces an unfavourable rounding effect, so that fractional days get assigned the equivalent of midnight.  Take a look at these to find out what is going wrong.

9. Now we'll fit a cosine with a period of 12.42 hours (the M2 semi-diurnal tide) to the data.  The plot automatically generated shows the original data and the best fit of a harmonic.  Read the function definition (starting with `def` and including all lines of code which are indented).  Can you figure out what it's doing, and what values it will return?

    - Take the difference to compute the residual.  Plot the residual

10. Working with velocity.  The first cell loads the data and plots the U, V and W velocity.

    - What can you say about the relative magnitudes of velocity in these three directions?

11.  Fit a cosine to the U and V velocity.  Again, we have to manipulate the time vector to work with this function.  

    - What happens if you omit (comment out) the lines of code starting with `finite_indices_uvel`?  Does the code break?  Can you read the error message to understand why?
    - We've imported `curve_fit` from `scipy.optimize`.  Google this function to read about how it works.

12. Plot a tidal ellipse.  This is plotting the u and v velocities on an axis.  

    - Reading the ellipse, can you determine the main direction of fluctuations of the tidal currents?  The secondary direction?
    - Plot the original data as points on the same axes.

13. Sometimes we are not interested in high frequency fluctuations.  To remove them, we can apply a lowpass filter, which allows low frequency variability to "pass through" but blocks the high frequency.  A simple way to do this is by using a moving average, sometimes called a "boxcar filter" or filtering with a "boxcar window" or "rectangular window".   The next section of code verifies that a 1-day rolling mean or moving average produces the save average for a single day (2024-05-22) as averaging together all values from 2024-05-22.  

14.  The remaining code is optional, but you can work through it and try various options to see what the result is on the original data.

After getting through step 13, choose 4 figures to export showing details about:

- The cosine fit to the CTD data and residuals
- The cosine fit to the velocity data and the residuals
- The effect of filtering a time series
- The ellipse

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