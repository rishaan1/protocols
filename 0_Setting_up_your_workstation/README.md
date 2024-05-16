# Session 0 - Setting up your workstation with `conda`

## Goal
To do bioinformatics, you need to be able to run existing software written and distributed by someone else, called *packages*. Those packages in turn 
will require other third-party packages to run, called *dependencies*, which will in turn require more dependencies, etc. You'll need to use a 
*package manager* to easily install and run external bioinformatics software. Here we set up a bioinformatics workstation using the `conda` package 
manager.

## Dependencies

This tutorial was written and tested on Mac OS 13.5 using the `Terminal` app. Similar results can be achieved using the command line terminal (Linux)
or WSL (Windows). 

## Tutorial
1. [Download](https://docs.anaconda.com/free/miniconda/index.html) and run the miniconda[^1] installer corresponding to your operating system.
2. sad

[^1]: `conda` is the package manager software itself. Anaconda, miniconda, mamba and micromamba are flavors of the same thing, with the following 
notable differences:
- `anaconda` is developed by Anaconda, Inc. and comes with lots of packages preinstalled. 
- `miniconda` is a minimal installation of conda and includes only Python, conda, and a few other useful packages. This is my preferred option.
- In the late 2010s, `conda`'s dependency solver algorithm became insufficient for the increasingly complex dependency trees of modern packages.
  A group of freelance developers spun off `mamba`, an open-source implementation of `conda` with a more efficient solver algorithm. The `mamba`
  algorithm is now an option in `conda` which we will set as default in this tutorial.
- `micromamba` is the minimal installation of `mamba`.
