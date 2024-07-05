# Dandelion 
Dandelion is a code for Automated and Efficient Sampling of Chemical Reaction Space.

Documentation : <https://jjy1031.github.io/>

## Installation
- Prerequisites
  - conda
  - openmpi

### Setup conda environment

```python
git clone
cd 
```

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
Please move orca folder to /home/username/package.

### Setup environment variable

```python
export PATH="/home/mhyeok/package/orca/orca_5_0_4:$PATH" \
export PYTHONPATH=/home/mhyeok/package/pyGSM:$PYTHONPATH \
export OMP_STACKSIZE=16G \
ulimit -s unlimited\
export OMP_NUM_THREADS=1
```

Be sure to change 'mhyeok' to your username please.

## Workflow

### Single-ended Growing String Method

- **1_create_gsm_jobs.ipynb**

  You can change `input_path` and `output_path` in config.

  `input_path` should contain XYZ files of mother structures.
  
  `output_path` will be the directory where generated coordinates(seeds) will be stored.

  You can get coordinates from mother structures in this process.

- **2_run_gsm_jobs.ipynb**
  
  
- **3_filter_reactions.ipynb**


### Nudged Elastic Band 
1. 1_neb_xtb.py
2. 2_make_rxns_json.ipynb
3. 3_compile_xtb_h5.py

### wB97X/6-31g(d) refinement
1. 1_wb97x_on_xtb_h5.py
2. 2_compile_wb97x_h5.ipynb


## References 


## Citation
If you are using Dandelion in your research, please cite:
