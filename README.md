# Dandelion 
Dandelion is a code for Automated and Efficient Sampling of Chemical Reaction Space.

Documentation : <https://jjy1031.github.io/>

## Installation
- Prerequisites
  - conda
  - openmpi

### Setup conda environment

```python
git clone https://github.com/mhyeok1/dandelion_test.git
cd dandelion_test
```
If you have authentification error, you should get personal access token.

```python
conda env create -f environment.yml
conda activate ts
pip install -e
```

### Install pyGSM

```python

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

We automated the generation of mother structures and the corresponding driving coordinates in this process. 

- **1_create_gsm_jobs.ipynb**

  You can change `input_path` and `output_path` in config.

  `input_path` should contain XYZ files of mother structures.
  
  `output_path` will be the directory where generated coordinates(seeds) will be stored.
  
  You can get coordinates from mother structures.

- **2_run_gsm_jobs.ipynb**

```python
$ python 2_run_gsm_jobs.py --input_path INPUT_PATH --max_workers MAX_WORKERS
```
  `input_path` should contain XYZ files of mother structures.
  
  You can run SE-GSM in this process.
  
- **3_filter_reactions.ipynb**
  
 You should modify the `input_path` and `output_path` of the config file. 

 `input_path` should contain XYZ files of generated coordinates(seeds).

 `output_path` will be the directory where filtered coordinates(seeds) will be stored.
 
  If you run this cell, you can get filtered structures. This filtering algorithm excludes trivial    pathways with strictly uphill energy trajectories, negligible energy variations, unfeasible
  2 structures, or those that are repetitive.

### Nudged Elastic Band 
- 1_neb_xtb.py
- 
```python
$ python 2_run_gsm_jobs.py --input_path INPUT_PATH --max_workers MAX_WORKERS
```
- 2_make_rxns_json.ipynb
- 3_compile_xtb_h5.py

### wB97X/6-31g(d) refinement
- 1_wb97x_on_xtb_h5.py
- 2_compile_wb97x_h5.ipynb


## References 


## Citation
If you are using Dandelion in your research, please cite:
