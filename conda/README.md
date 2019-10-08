# Conda

Conda is a super handy framework for installing and managing software packages, and it's not just for Python libraries!  Below is a basic step-thru for creating a new Conda environment, activating that environment, and installing packages into that environment.

### 1. **Install Conda**  
I recommend [installing Anaconda](https://docs.anaconda.com/anaconda/install/) on your machine.  This will provide you not only with the Conda for package management, but it will also install a ton of handy Python libraries.  If this isn't your first rodeo I'd suggest giving [Miniconda](https://docs.conda.io/en/latest/miniconda.html) a try (useful for using Conda on a HPC).

During the installation process you may be prompted with the following: “Do you wish the installer to initialize Anaconda3 by running conda init?”  Select "Yes" as this will add anaconda to your `$PATH` variable, allowing you to immediately use Conda from the command line.

Once Conda is installed, you should be able to use it at the command line:

```
$ conda --version
conda 4.7.12
```

### 2. **Create a new Conda environment**  
Once you're able to use `conda` at the command line I think it's helpful to try creating a new environment.  The "default" Conda environment is called "base".  This is where all new packages will be installed if you do not specify otherwise.  For each new project I start I find it helpful to create a new Conda environment, or I'll create Conda environments for software packages that I use frequently.

Here I'm going to create a new Conda environment called "basic_env" that will specifically be using Python version 3.4.

```
$ conda create --name basic_env python=3.4
```

Once that completes I can now view a list of the environments on my machine with the following command:

```
$ conda env list
base                  *  /usr/local/anaconda3
basic_env                /usr/local/anaconda3/envs/basic_env
```

Note that the asterisk denotes the active environment that I am using

There are loads of helpful commands for managing Conda environments and I find  [this page](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html) has been incredibly helpful.

### 3. **Activate the new Conda environment**  
Creating a new Conda environment is just the first step to using it, the next part is stepping in or activating it.  To do this:

```
$ conda activate basic_env
```

You may notice your command prompt will change from "base" to "basic_env".  You can also list the Conda environments again, but note that the asterisk position has changed.

```
$ conda env list
base                     /usr/local/anaconda3
basic_env             *  /usr/local/anaconda3/envs/basic_env
```

### 4. **Installing new packages**  
Now that the new environment "basic_env" is activated, we can now start installing some packages.  Here I'm going to install [BASIC](https://ttic.uchicago.edu/~aakhan/BASIC/), a tool used for semi-de novo assembly of B and T cell receptor genes.  To install BASIC in the "basic_env":

```
$ conda install basic
```

Hopefully all goes well and basic installs without a hitch.  To check try running:

```
$ python BASIC.py -h
usage: BASIC.py [-h] [-i TYPE] [-p NUM_THREADS] [-n NAME] [-SE FASTQ]
                [-PE_1 LEFT] [-PE_2 RIGHT] [-g GENOME] [-b BOWTIE] [-t TMPDIR]
                [-o OUTPUT_LOCATION] [-a] [-v] [--version]
```

Those are the basics for managing Conda environments!  You can certainly install more packages into the same environment, but again, I'd recommend creating new environments for projects or frequently used packages.  If you wanna jump out of the "basic_env" and go back to "base", simply activate the "base" environment.

```
$ conda activate base
```
