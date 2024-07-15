# Dandelion 
Dandelion is a code for Automated and Efficient Sampling of Chemical Reaction Space.

Documentation : <https://jjy1031.github.io>

## Installation
- Prerequisites
  - conda
  - openmpi

### Download Dandelion

You can install the code from our repository:

```python
git clone https://github.com/mhyeok1/dandelion_test.git
cd dandelion_test
```
If you run into an authentification error, you should get [personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token-classic).

### Setup conda environment

This command is used to create a new Conda environment using the specifications provided in an `environment.yml` file.

```python
conda env create -f environment.yml
conda activate ts
pip install -e .
```

### Install pyGSM

Visit the [pyGSM repository](https://github.com/ZimmermanGroup/pyGSM) for instructions or simply use:

```python
pip install -e git+https://github.com/ZimmermanGroup/pyGSM.git#egg=pyGSM
```

### Install Orca

You can install ORCA [here](https://orcaforum.kofo.mpg.de/app.php/portal).
To extract a tar.xz file, you can use the following command.

```python
tar -xf orca.tar.xz
```

### Setup environment variables in `.bashrc`

You can open your `.bashrc` file using:
```python
vi ~/.bashrc
```

Add the following lines to your `.bashrc` file:

1. Add ORCA to your path :
```python
export PATH="/path/to/your/orca/directory:$PATH" \
```

2.Set the `PYTHONPATH` for pyGSM:
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

### Verifying Installation

By executing `python dandelion_sample.py -h`, 


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
