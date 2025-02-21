---
layout: default
title: Installation
nav_order: 2
---

# Installation
- Prerequisites
  - [miniconda](https://docs.anaconda.com/miniconda/install/)
  - [OpenMPI 4.1.1](https://www.open-mpi.org/software/ompi/v4.1/)

{: .highlight }
> OpenMPI 4.1.1 is required for ORCA 5.0.4.

## Download Dandelion

You can install the code from [our repository](https://github.com/mhyeok1/dand):

```shell
$ git clone https://github.com/mhyeok1/dand.git
$ cd dand
```

## Setup conda environment

This creates a new conda environment according to the specifications in the `environment.yml` file.

```shell
$ conda env create -f environment.yml
$ conda activate ts
$ pip install -e .
```

{: .important }
> Double-check that you are working in the 'ts' environment!


## Install pyGSM

Visit the [pyGSM repository](https://github.com/ZimmermanGroup/pyGSM) for more detailed instructions, or simply use:

```shell
$ git clone https://github.com/ZimmermanGroup/pyGSM
$ pip install -e .
```
By executing `gsm` in the terminal, you can verify that the program has been successfully installed.



## Install Orca

You can install ORCA 5.0.4 from [here](https://orcaforum.kofo.mpg.de/app.php/portal).
The following command extracts a `tar.xz` file.

```shell
$ tar -xf orca.tar.xz
```

## Setup environment variables in `.bashrc`

You can open your `.bashrc` file using:
```shell
$ vi ~/.bashrc
```

Add the following lines to your `.bashrc` file:

```shell
export PATH="/path/to/your/orca/directory:$PATH" \
export PYTHONPATH=/path/to/your/pyGSM/directory:$PYTHONPATH \
export OMP_NUM_THREADS=1
export OMP_STACKSIZE=16G \
ulimit -s unlimited\
```

Apply changes:
```shell
$ source ~/.bashrc
``` 
