# Dandelion 
Dandelion is a code for Automated and Efficient Sampling of Chemical Reaction Space.

Documentation : <https://jjy1031.github.io/>

## Installation
- Prerequisites
  - conda
  - openmpi

## Install from source

```python
git clone
cd 
```

### Setup conda environment

```python
conda env create -f ts.yaml
```

### Install pyGSM

```python
conda activate ts
pip install -e
```
Please move pyGSM folder to /home/username/package.

### Install Orca

```python
tar -xf orca.tar.xz
```
Please move Orca folder to /home/username/package.

### Setup environment variable

export PATH="/home/mhyeok/package/orca/orca_5_0_4:$PATH" \
export PYTHONPATH=/home/mhyeok/package/pyGSM:$PYTHONPATH \
export OMP_STACKSIZE=16G \
ulimit -s unlimited\
export OMP_NUM_THREADS=1

Be sure to change 'mhyeok' to your username please.

## Examples



## References 


## Citation
If you are using Dandelion in your research, please cite:
