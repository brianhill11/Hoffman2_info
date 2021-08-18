# Hoffman2 Info
This repo is for aggregating information about using the Hoffman2 cluster at UCLA.

## Using $SCRATCH storage
If you are storing files in your [$SCRATCH](https://www.hoffman2.idre.ucla.edu/data-storage/#SCRATCH) directory on Hoffman2, files older than 7 days are subject to deletion by the system. One method for keeping your files "fresh" is to execute the `touch` command on all files in your scratch directory once a week. For a tutorial on how to set up a job to do this, see [this repo](https://github.com/brianhill11/touch) 

**NOTE**: Any files that need to be stored long term (and backed up) should be stored in your $HOME directory.  

## Interactive sessions

## Launching jobs

## Jupyter notebooks

Running Jupyter notebooks on Hoffman2 is possible by following the steps found [here](https://www.hoffman2.idre.ucla.edu/access/jupyter-notebook/#Starting_a_Jupyter_Notebook_on_the_Hoffman2_cluster_displaying_it_on_your_local_web-browser)

Basically, you need to clone the code from [this repo](https://gitlab.idre.ucla.edu/dauria/jupyter-notebook.git) to your laptop and run the `h2jupynb` script to start a session and connect. 

One thing to note is that you can use command-line parameters to specify the python version, the amount of memory, whether you want to use a GPU node, etc. For a list of parameters, use the `-h` flag when calling the `h2jupynb` script.

## GPU Usage

There are several GPU nodes available for use on the Hoffman2 cluster. As of 09/2020, these include P4, RTX2080Ti and V100 cards. If submitting jobs or starting an interactive session on Hoffman2, you can specify that you want a GPU node (and which type of card). For example, to get a GPU node with a P4 Nvidia card, use:

```
qsub -cwd -V -N GPU -l gpu,P4,h_data=16G,h_rt=23:59:00
```

If using the `h2jupynb` script, you can use the `-g` flag to ask for a GPU node, and the `-c` flag can be used to specify which GPU card type you would like to use. 

CUDA versions 7.0, 7.5, 8.0, 9.1 and 10.0 are installed, and can be loaded using `module load cuda/[version number]`, for example `module load cuda/10.0`. The CUDA version can also be specificed when using the `h2jupynb` script using the `-l` flag (see `h2jupynb --help` for more info).

Some things to note: 
- starting a job on GPU nodes with newer/more desirable cards will be more difficult (i.e. V100 cards), so if you don't want to wait, choosing an older card will be faster (i.e. P4). 
- GPU nodes do not have much system memory (sometimes <= 24GB) and if you try to ask for more memory than any of the GPU nodes have, you will not get a node. 
- Some of the GPU nodes have older CPUs, which don't always have the latest instructions (like AVX or AVX2), and some softwares (like tensorflow 2.0+) are compiled using these instructions and will crash (dump core) when trying to run. You may have to install an older version of software that was compiled without these instructions, or compile the software on the GPU nodes yourself. 

## Using Anaconda 

### Environment storage location/disk space issues
