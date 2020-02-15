# Hoffman2 Info
This repo is for aggregating information about using the Hoffman2 cluster at UCLA.

## Using $SCRATCH storage
If you are storing files in your [$SCRATCH](https://www.hoffman2.idre.ucla.edu/data-storage/#SCRATCH) directory on Hoffman2, files older than 14 days are subject to deletion by the system. One method for keeping your files "fresh" is to execute the `touch` command on all files in your scratch directory once a week. For a tutorial on how to set up a job to do this, see [this repo](https://github.com/brianhill11/touch) 

**NOTE**: Any files that need to be stored long term (and backed up) should be stored in your $HOME directory.  

## Interactive sessions

## Launching jobs

## Jupyter notebooks

Running Jupyter notebooks on Hoffman2 is possible by following the steps found [here](https://www.hoffman2.idre.ucla.edu/access/jupyter-notebook/#Starting_a_Jupyter_Notebook_on_the_Hoffman2_cluster_displaying_it_on_your_local_web-browser)

Basically, you need to clone the code from [this repo](https://gitlab.idre.ucla.edu/dauria/jupyter-notebook.git) to your laptop and run the `h2jupynb` script to start a session and connect. 

One thing to note is that you can use command-line parameters to specify the python version, the amount of memory, whether you want to use a GPU node, etc. For a list of parameters, use the `-h` flag when calling the `h2jupynb` script.

