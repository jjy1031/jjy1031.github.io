---
layout: default
title: Installation
parent: Userguide
nav_order: 1
---

# Installation
- Prerequisites
  - conda
  - openmpi

## Download Dandelion

You can install the code from our repository:

```python
git clone https://github.com/mhyeok1/dandelion_test.git
cd dandelion_test
```
If you run into an authentification error, you should get [personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token-classic).

## Setup conda environment

This command is used to create a new Conda environment using the specifications provided in an `environment.yml` file.

```python
conda env create -f environment.yml
conda activate ts
pip install -e .
```

## Install pyGSM

Visit the [pyGSM repository](https://github.com/ZimmermanGroup/pyGSM) for instructions or simply use:

```python
pip install -e git+https://github.com/ZimmermanGroup/pyGSM.git#egg=pyGSM
```

## Install Orca

You can install ORCA [here](https://orcaforum.kofo.mpg.de/app.php/portal).
To extract a tar.xz file, you can use the following command.

```python
tar -xf orca.tar.xz
```

## Setup environment variables in `.bashrc`

You can

```python
export PATH="/path/to/your/orca/directory:$PATH" \
```
```python
export PYTHONPATH=/path/to/your/pyGSM/directory:$PYTHONPATH \
```
```python
export OMP_STACKSIZE=16G \
ulimit -s unlimited\
```

```python
export OMP_NUM_THREADS=1
```

## Verifying Installation

By executing `python dandelion_sample.py -h`, 

