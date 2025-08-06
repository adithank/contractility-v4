Usage
=====

.. _installation:

Installation
------------

Download link : https://office365stanford-my.sharepoint.com/:u:/g/personal/adithan_stanford_edu/ESXWyru1YbBMqUeHVeW1vZQBsdZYXMDway18FdoBOiwHKA?e=nmo2MS

Please use "MyAppInstaller_mcr" to install MATLAB runtime and the Contractility software. 

Make sure to tick "Add shortcut to desktop" during installation. Keep other options at default. 



Guide
-----

Step 1 : Open the app
---------------------

After installation, either double-click on the shortcut or search for "Contractility analysis" in search bar.

You should see this window pop-up:

.. image:: /_static/images/1.png
   :width: 600px

Click on "Create a new job" (1) to start from scratch. If you want to open already created job, click button (2).

Step 2: Create a new job
------------------------

Navigate to the folder with images. The software will recursively look for sub-folders in the selected folder with "tif" files. 

.. image:: /_static/images/2.png
   :width: 600px

This example dataset has the following organization for imaging a 96 well plate. Each well has sub-positions (e.g. r_0004_c_0004). 
4 channels are imaged (beads, empty, MTDeepRed, ref) for each position. E.g. see the below screenshot:

.. image:: /_static/images/0_1.png
   :width: 600px

Each of the folder contains one or more "tif" files. If it is a timeseries, the files should have some numbering that increases with time. Eg:

.. image:: /_static/images/0_2.png
   :width: 600px


Step 3: Selecting files and aliases
-----------------------------------

A unique alias is created for each image folder when creating a new job. Output directory is automatically created. The name can be edited or clicked on the button (1) to edit the analysis destination.

Click (2) if alias needs modification to open "Make Alias" sub-app. Click (3) to filter the "Analyze" column in the table.

E.g. "Clear All" was clicked to clear Analyze column. Then, only MTDeepRed folder is selected for analysis using the "Selection filter" sub-app. 

.. image:: /_static/images/3.png
   :width: 600px


Step 4: Selecting files and aliases
-----------------------------------

A reference image to calculate deformation against is required. A diastolic frame in the timelapse where there is no motion (i.e. relaxed state) is automatically selected.
Please use the default "Automatic : Frame to Frame". 

In case you want to measure resting tension with a soft substrate plate, please select the third option and select the correct folder. In this example, it's "ref" folder. 

Please enter the correct frame rate in "Acquisition rate" dialog box. For PIV parameters, keep it at default. Refer to the manuscript for more details.

.. image:: /_static/images/4.png
   :width: 600px

Step 5: TFM and performance parameters 
--------------------------------------

If using soft substrate plate, enter the optical calibration and gel properties. Check 'Enable Traction Force Microscopy'.

Please use the parameters shown below (image) for best performance. If not using GPU, change 'GPU acceleration' to "disabled".


.. image:: /_static/images/5.png
   :width: 600px


Step 6: Start analysis
----------------------

Click 'Start Analysis button'.

.. image:: /_static/images/6.png
   :width: 600px

Status is updated as analysis goes. 

.. image:: /_static/images/7.png
   :width: 600px

Click 'Quit' to stop  after the next step. Now, you can go back to change parameters and start again.

.. image:: /_static/images/8.png
   :width: 600px


Step 7: Results
---------------

Once the analysis is done, it generates the following files in the output folder 

.. image:: /_static/images/10.png
   :width: 600px

- output       -     Results of contractility analysis for each folder
- raw          -     1D trace file, use this for QC while the analysis is running
- vel          -     Velocity file, used for automatic reference Selection
- config.json  -     Analysis parameter configuration
- log          -     Log of analysis running
- motion/traction -  csv file containing results. This is the file you would use for results
- jobfile      -     Contains list of folders and locations. 

Example of the motion/traction file with the different parameters (See manuscript for details):

.. image:: /_static/images/11.png
   :width: 600px


Load job
--------

Clicking 'Load job file' in the first page asks for 'jobfile' in case you want to load a pre-run job. 
