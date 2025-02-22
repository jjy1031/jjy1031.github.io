---
layout: default
title: Installation
nav_order: 2
---

# Installation Guide

## Prerequisites
- [Miniconda](https://docs.anaconda.com/miniconda/install/)
- [OpenMPI 4.1.1](https://www.open-mpi.org/software/ompi/v4.1/)

{: .highlight }
> ORCA 5.0.4 specifically requires OpenMPI version **4.1.1**



## Step-by-Step Installation

Clone the repository and navigate to the directory:

```shell
$ git clone https://github.com/mhyeok1/dand.git
$ cd dand
```

## Set Up Conda Environment

Create and activate the environment:

```shell
# Create environment from configuration file
$ conda env create -f environment.yml

# Activate the environment
conda activate ts

# Install Dandelion
pip install -e .
```



{: .important }
> Always ensure you are in the 'ts' environment when using Dandelion



## Install pyGSM

Install the [Growing String Method implementation](https://github.com/ZimmermanGroup/pyGSM):

```shell
$ git clone https://github.com/ZimmermanGroup/pyGSM
$ cd pyGSM
$ pip install -e .
```

Test the installation by running:

```shell
$ gsm
```


## Install ORCA

1. Download ORCA 5.0.4 from the [ORCA portal](https://orcaforum.kofo.mpg.de/app.php/portal).
1. Extract the downloaded file:
   
```shell
$ tar -xf orca.tar.xz
```

## Configure Environment Variables

Add these settings to your .bashrc file:

```shell
# Open .bashrc
vi ~/.bashrc

# Add these lines:
export PATH="/path/to/orca:$PATH"
export PYTHONPATH=/path/to/pyGSM:$PYTHONPATH
export OMP_NUM_THREADS=1
export OMP_STACKSIZE=16G
ulimit -s unlimited
```

Apply changes:
```shell
$ source ~/.bashrc
``` 

## Verification
After installation, verify that all components are working:

1. Ensure you're in the 'ts' environment
1. Check if commands `dand`, `gsm`, and `orca` work

[Continue: How-to-use](https://mhyeok1.github.io/dand_docs/docs/how-to.html){: .btn .btn-purple }
