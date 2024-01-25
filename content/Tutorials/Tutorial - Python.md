See also [[Homework 2 - Intro to Python programming for data analysis]]

From [[How to Connect to Remote Accounts]]:
` ssh CID@vera1.c3se.chalmers.se`

You will be standing in your home directory on the cluster. We also have a shared directory for the course:
`cd /cephyr/NOBACKUP/groups/bbt045_2024`
All the necessary files can be found here.
To go back to your home directory just use `cd`.

## Setup for your home directory
Create a directory for this course: `mkdir BBT045`

Also create: `mkdir bin` and `mkdir BBT045/Python_Intro`

Move into the common area for the course: `cd /cephyr/NOBACKUP/groups/bbt045_2024`

Container and data are the only directories we will use today. Move into data: `cd data`

You will use the `iris`dataset, copy it into your directory: `cp iris.csv ~/BBT045/Python_Intro/`

Move to container: `cd ..` then `cd Container`

Copy `run_jupyter.sh`into your `bin` and your `Python_Intro`:
- `cp run_jupyter.sh ~/bin/`
- `cp run_jupyter.sh ~/BBT045/Python_Intro/`

Return home: `cd` (check with `ls` and/or `pwd`)

## Configuring run_jupyter.sh
Move into Python_Intro and open `run_jupyter.sh` with nano: `nano run_jupyter.sh`

You may change the duration to e.g. 1 hour/2 hours. BUT only use the time you will actually use it. Otherwise you and others may not have resources to use in the end of the project.

**If you feel you are running out if time, save and start a new job!**

Edit your ID number: 9 Alva;  10 Felix; 11 Parya. This is to make sure that you are not using the same number as another student.

Do NOT change project ID or IP login node.

`ml purge` = module purge, good habit to use, so that you are aware of what programs you are using. 

`bbt045.sif` - the container we will be using. "a tiny computer". Helps with reproducibility, ensures that there are no dependency issue, so that all programs are available.

The last line in the file is the actual command that is sent to SLURM.

`Ctrl+O`, `Enter` to save and `Ctrl+X` to save.

Copy it into Python_Intro, the notebook will open here and will be saved here.
	`cp run_jupyter.sh ~/BBT045/Python_Intro`

## Running run_jupyter.sh
Move to the correct  directory and run it:
	`./run_jupyter.sh`

Wait for the cluster to run it, may take a couple of minutes.

You will get three URLs, copy the numbers in the second one, it will have the form  *http://vera14-1:2010/lab?token=...*. In my case the relevant numbers are 14-1 and 2010.

Open a new terminal window/tab. The jupyter notebook tab you will NOT touch anymore. Run the following command in the new window, replacing *14-1* and *2010* with **YOUR** numbers. and *blfelix* with your CID
- `ssh -N -L 2010:vera14-1:2010 blfelix@vera1.c3se.chalmers.se `

If everything works, nothing will happen after you enter you password and press Enter

Go back to the jupyter tab and open the third URL (Form: 127..0....) in a browser.

This will open the Jupyter notebook!
iris.csv and the file run_jupyter.sh will be visible on the left.

Open a third terminal, log in to Vera and go to the Python_Intro directory (`cd ~/BBT045/Python_Intro` in my case) and download the notebook:
- `wget https://bengtssonpalme.github.io/MPBIO-BBT045-2024/python_for_data_analysis/intro_python_data_analysis.ipynb`

It will now be visible in the browser, otherwise click the spinning arrow to refresh.

To check how much time you have used so far: `squeue -u CID`where CID is your CID. If there is only a list of headers, you have no job running and the time you specified has run out and you need to run `run_jupyter.sh`again (remember to change the time to the correct amount you need).