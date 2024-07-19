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

You can install the code from [our repository](https://github.com/mhyeok1/dandelion_test):

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
git clone https://github.com/ZimmermanGroup/pyGSM
pip install -e .
```

## Install Orca

You can install ORCA [here](https://orcaforum.kofo.mpg.de/app.php/portal).
To extract a tar.xz file, you can use the following command.

```python
tar -xf orca.tar.xz
```

## Setup environment variables in `.bashrc`

You can open your `.bashrc` file using:
```python
vi ~/.bashrc
```

Add the following lines to your `.bashrc` file:

1. Add ORCA to your path :
```python
export PATH="/path/to/your/orca/directory:$PATH" \
```

2. Set the `PYTHONPATH` for pyGSM:
```python
export PYTHONPATH=/path/to/your/pyGSM/directory:$PYTHONPATH \
```

3. Adjust the `OMP_NUM_THREADS`:
```python
export OMP_NUM_THREADS=1
```

4. Set the xtb configuration:
```python
export OMP_STACKSIZE=16G \
ulimit -s unlimited\
```
Apply the changes:
```python
source ~/.bashrc
``` 
