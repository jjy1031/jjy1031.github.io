---
layout: default
title: How-to-use
nav_order: 3
---

# Example


This page provides a guide for using Dandelion, which efficiently generates an extensive database by sampling both equilibrium and reactive regions of chemical compound space.
<div align="center">
  <img width="1600" alt="all" src="https://github.com/user-attachments/assets/6ff5bf37-7ce5-4980-a268-ee0f1d2c185d">
</div>

You can download these structures from [HERE](https://github.com/mhyeok1/dand_docs/blob/docs/assets/mother_structures_for_tut.Zip){:download}

Let's assume that we are interested in expanding dataset from 5 given mother structures. First,  each mother structures needs to be optimized to serve as a good starting point for GSM. This can be achieved by performing geometry optimization using GFN2-xTB. Ensure that all the prepared mother structures are in specific `input_path`, and saved in `.xyz` file format. 

<style>
  /* 전체 폰트 스타일 유지 */
  body {
    font-family: system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
    margin: 0;
    padding: 0;
  }

  /* 탭 버튼 스타일 */
  .tab-container {
    display: flex;
    gap: 6px;
    padding: 10px 0;
  }

  .tab-button {
    background-color: #f8f9fa;
    border: 1px solid #d1d5db;
    padding: 8px 14px;
    cursor: pointer;
    font-weight: 500;
    font-size: 14px;
    border-radius: 4px;
    transition: background-color 0.2s ease-in-out, border 0.2s ease-in-out;
  }

  .tab-button:hover {
    background-color: #e2e6ea;
    border-color: #adb5bd;
  }

  .tab-button.active {
    background-color: #d1d5db;
    border-color: #adb5bd;
    color: #333;
  }

  /* 📌 큰 회색 박스 유지 (텍스트가 들어갈 영역) */
  #molecule-container {
    background-color: #f9f9f9; /* 회색 박스 */
    padding: 15px;
    border: 1px solid #ddd;
    border-radius: 4px;
    width: fit-content;
    max-width: 100%;
    overflow-x: auto; /* 가로 스크롤 가능 */
  }

  /* 📌 원자 좌표 데이터 스타일 (흰 배경 제거 + 포맷 유지) */
  #molecule-data {
    font-family: monospace;
    font-size: 13px;
    white-space: pre-wrap; /* 줄바꿈 유지 */
    margin: 0;
    padding: 0;
    border: none;
    background: none;
  }
</style>

<!-- 🔹 메인 탭 -->
<div class="tab-container">
  <button class="tab-button active" onclick="showMolecule('Cl7138', this)">Cl7138</button>
  <button class="tab-button" onclick="showMolecule('Cl7164', this)">Cl7164</button>
  <button class="tab-button" onclick="showMolecule('Cl7166', this)">Cl7166</button>
  <button class="tab-button" onclick="showMolecule('Cl7168', this)">Cl7168</button>
  <button class="tab-button" onclick="showMolecule('Cl7188', this)">Cl7188</button>
</div>

<!-- 📌 원자 좌표 데이터 표시 (큰 회색 박스 유지) -->
<div id="molecule-container">
  <pre id="molecule-data">
Cl          -2.26279631     0.43247998    -0.04641091
C           -0.53339796     0.40058085    -0.02301215
C            0.27488623     1.56165626    -0.05319137
C            1.59527547     1.26911727    -0.03881976
S            1.87989529    -0.43724943     0.01532471
C            0.17575256    -0.76865423     0.01684597
N           -0.31260451    -2.04617746     0.13293541
H           -0.12640769     2.55744176    -0.08718073
H            2.43239654     1.93559234    -0.05293046
H            0.29134973    -2.78353992    -0.19312943
H           -1.28066134    -2.14438544    -0.13694928
  </pre>
</div>

<script>
  function showMolecule(molecule, button) {
    const moleculeData = {
      "Cl7138": `Cl          -2.26279631     0.43247998    -0.04641091
C           -0.53339796     0.40058085    -0.02301215
C            0.27488623     1.56165626    -0.05319137
C            1.59527547     1.26911727    -0.03881976
S            1.87989529    -0.43724943     0.01532471
C            0.17575256    -0.76865423     0.01684597
N           -0.31260451    -2.04617746     0.13293541`,
      "Cl7164": `24

(in this line a comment or an energy can be placed)
O  0.470000   2.568800   0.000600
O -3.127100  -0.443600  -0.000300
N -0.968600  -1.312500   0.000000
N  2.218200   0.141200  -0.000300
N -1.347700   1.079700  -0.000100
N  1.411900  -1.937200   0.000200
C  0.857900   0.259200  -0.000400
C  0.389700  -1.025400  -0.000400
C  0.030700   1.422000  -0.000600
C -1.906100  -0.249500  -0.000400
C  2.503200  -1.199800   0.000300`,
      "Cl7166": `좌표 데이터 없음`,
      "Cl7168": `좌표 데이터 없음`,
      "Cl7188": `좌표 데이터 없음`
    };

    document.getElementById("molecule-data").innerText = moleculeData[molecule];

    document.querySelectorAll('.tab-button').forEach(btn => btn.classList.remove('active'));
    button.classList.add('active');
  }
</script>

To run dandelion, your current conda environment should be **ts**.
You can enter the following command in terminal for more information:

``` python
$ dandelion_sample -h

usage: dandelion_sample [-h] -i INPUT_PATH -o OUTPUT_PATH -n MAX_WORKERS

Do SEGSM and NEB from mother structures, Other parameters can be set in each
modules

options:
  -h, --help            show this help message and exit
  -i INPUT_PATH, --input_path INPUT_PATH
                        Input path of mother structures
  -o OUTPUT_PATH, --output_path OUTPUT_PATH
                        Output path of dandelion
  -n MAX_WORKERS, --max_workers MAX_WORKERS
                        Number of worker processes
```

Assuming your mother structures are saved as 'struc.xyz' in `/home/pekora/example/mother_strucs`, you can initiate sampling with the following command:

```python
python dandelion_sample -i /home/pekora/example/mother_strucs -o /home/pekora/example/outputs -n 30
```

Then the following 6 steps will be executed automatically:

```


                                                     `;:`  BREAK 1 2
                                         .;:;         /    BREAK 3 4
        _____                   _      _;::;         `     ADD 1 3
        |  __ \                | |    | |';:;'
        | |  | | __ _ _ __   __| | ___| |  _  ___  _ __
        | |  | |/ _` | '_ \ / _` |/ _ \ | | |/ _ \| '_ \
        | |__| | (_| | | | | (_| |  __/ | | | (_) | | | |
        |_____/ \__,_|_| |_|\__,_|\___|_| |_|\___/|_| |_|

                   Chemical compound space sampling
           near transition state using xTB, SE-GSM and NEB
                          Ver. 0.6.2 by mlee



```

Dandelion first generates possible driving coordinates(seeds) from each mother structures.

```
╔════════════════════════════════════════════════════════════════════╗
║                          1. Creating GSM                           ║
╚════════════════════════════════════════════════════════════════════╝

Arguments provided:
  input_path: /home/pekora/example/mother_strucs
  output_path: /home/pekora/example/outputs/1_gsm
  maxbreak: 2
  maxform: 2
  maxchange: 3
  minbreak: 0
  minform: 0
  minchange: 1
  ignore_single_change: True
  equiv_Hs: False

280 Seeds were generated from ClGeom-m7138-i1-c1-opt
276 Seeds were generated from ClGeom-m7164-i1-c1-opt
275 Seeds were generated from ClGeom-m7166-i1-c1-opt
276 Seeds were generated from ClGeom-m7168-i1-c1-opt
299 Seeds were generated from ClGeom-m7188-i1-c1-opt

Creating GSM finished!
```

Based on generated GSM jobs, GSM can be executed. Some jobs can fail to converge or reach the product within the predefined maximum number of nodes and should be filtered out.

```
╔════════════════════════════════════════════════════════════════════╗
║                           2. Running GSM                           ║
╚════════════════════════════════════════════════════════════════════╝

Arguments provided:
  input_path: /home/pekora/example/output/1_gsm
  max_workers: 30

GSM on seeds: 100%|████████████████████████| 1406/1406 [4:57:13<00:00]
GSM finished!

```

Dandelion excludes some trivial pathways with strictly uphill energy trajectories, negligible energy variations, unfeasible structures, or those that are repetitive.

```
╔════════════════════════════════════════════════════════════════════╗
║                          3. Filtering GSM                          ║
╚════════════════════════════════════════════════════════════════════╝

Arguments provided:
  input_path: /home/pekora/example/outputs/1_gsm
  output_path: /home/pekora/example/outputs/2_gsm_filtered
  barrier_min: 5
  barrier_max: 200
  delta_e_min: 5

◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢
   mother: ClGeom-m7138-i1-c1-opt
Initial seeds:                   280
GSM success reactions:           115
Profile filtered reactions:       41
Structure filtered reactions:     38
Unique reactions:                 28

◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢
   mother: ClGeom-m7164-i1-c1-opt
Initial seeds:                   276
GSM success reactions:           111
Profile filtered reactions:       42
Structure filtered reactions:     38
Unique reactions:                 32

◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢
   mother: ClGeom-m7166-i1-c1-opt
Initial seeds:                   275
GSM success reactions:            96
Profile filtered reactions:       31
Structure filtered reactions:     28
Unique reactions:                 25

◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢
   mother: ClGeom-m7168-i1-c1-opt
Initial seeds:                   276
GSM success reactions:            87
Profile filtered reactions:       37
Structure filtered reactions:     35
Unique reactions:                 29

◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢◤◢
   mother: ClGeom-m7188-i1-c1-opt
Initial seeds:                   299
GSM success reactions:           102
Profile filtered reactions:       40
Structure filtered reactions:     33
Unique reactions:                 30

Filtering GSM finished!

```

Using the outputs of gsm, Dandelion runs NEB or Climbing-Image NEB. NEB can optimize some energy path using the concept of maximum force.

```
╔════════════════════════════════════════════════════════════════════╗
║                           4. Running NEB                           ║
╚════════════════════════════════════════════════════════════════════╝

Arguments provided:
  input_path: /home/pekora/example/output/2_gsm_filtered
  output_path: /home/pekora/example/output/3_neb
  max_workers: 30
  n_images: 10
  neb_fmax: 0.5
  cineb_fmax: 0.05
  steps: 500

Seeds: 100%|███████████████████████████████████| 144/144 [04:34<00:00]
xTB-NEB completed!

```

In the fifth step, data is filtered based on specific criteria. For example, non-convergent reactions and those without a single negative eigenvalue in their Hessian matrices are excluded. This ensures focus on structures near valid paths. NEB results are further refined to avoid redundant structural data. A new band iteration is chosen only when the cumulative Fmax exceeds 0.1 eV/Å, saving DFT calculations and preventing overfitting to narrow PES regions.

```

╔════════════════════════════════════════════════════════════════════╗
║                          5. Filtering NEB                          ║
╚════════════════════════════════════════════════════════════════════╝

Arguments provided:
  input_path: /home/pekora/example/output/3_neb
  output_path: /home/pekora/example/output/4_neb_filtered

Mothers: 100%|█████████████████████████████████████| 5/5 [00:20<00:00]

40/53 rxns were saved to /home/pekora/example/output/4_neb_filtered/reactions.json
Filtering NEB finished!

```

Sixth step is to compile samples:
```

╔════════════════════════════════════════════════════════════════════╗
║                        6. Compiling samples                        ║
╚════════════════════════════════════════════════════════════════════╝

Arguments provided:
  input_path: /home/pekora/example/output/4_neb_filtered/reactions.json
  output_path: /home/pekora/example/output/xtb.h5
  fmax_threshold: 0.1

Compiling reactions: 100%|███████████████████████| 40/40 [00:03<00:00]
Compiling finished!

```
And there will be newly generated file in your output path, `xtb.h5` file.

Next step is to execute dandelion_refine.
You can enter -h or --help for more information:

```
$ dandelion_refine -h
usage: dandelion_refine [-h] -i INPUT_PATH -n MAX_WORKERS --orca ORCA

Refine force on obtained samples, Other parameters can be set in each modules

options:
  -h, --help            show this help message and exit
  -i INPUT_PATH, --input_path INPUT_PATH
                        Input path of working directory containing xtb.h5
  -n MAX_WORKERS, --max_workers MAX_WORKERS
                        Number of worker processes
  --orca ORCA           Path of the orca binary file
```

Make sure that the path of the orca should point an orca **executable file**.

If you enter like this:
```
$ dandelion_refine -i /home/pekora/example/outputs -n 15 --orca /home/pekora/package/orca/orca_5_0_4/orca
```

2 steps below will be executed automatically !

```
         ⢀⣀⣀⣀⣀⣀⡀       ⢀⢀⣀⢀⠞⠖⠁⠡⡂⡆ ⡠⢀⡀
         ⠺⢿⣿⣿⣿⣿⣿⣿⣷⣦⣠⣤⣤⣤⣄⣀⣀ ⡏⢸  ⢀ ⠣⠈ ⡠⡋⡨⡋⡂
           ⠙⢿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣷⣦⣄⡀⡎⢀⡰⢀⢎⠌⢀⠔⣐⠠⣄⣀
       ⢀ ⡔⢀⣴⣾⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⠿⠿⠿⣿⣿⣷⣄⠂ ⢊⠎ ⠠⠂⡀⠕⠌⠌ ⡄⡠⢄
    ⢀⡆⠄⠁⢈⢠⣾⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣀   ⣀⣿⣿⣿⣆⠐    ⡨⠒⠁⡀⢠⣦⠍⠇⡀⢲⠂⡄⠄
   ⠨⡀⠑⡈ ⢠⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⣿⡄   ⠈  ⣬⠠⣰⣿ ⢳⢹⡄⡆⠄⢀⢼
 ⡄⠱⠈⠁⠑⢄⠐⣾⣿⣿⡿⠋⠁⣀⣠⣬⣽⣿⣿⣿⣿⣿⣿⠿⠿⠿⠿⠿⠿⠿⠿⠟⠁⡟⣅⡢⠁⠠⠜⡄⡑⢌⢧⡀ ⡀⣰⢁⡐⢁⢄⣡⣧⡤⠄
⠠⡐⠓⠂⠌  ⢀⣿⣿⡏⢀⣴⣿⠿⠛⠉⠉⠶⢸⣿⣿⠿⠁⠢⠨⢀⣻⣿⣿⣿⣿⢟⣿⣝⠂  ⠠⡠⢆⠈⡂⠱⡇ ⣅⠫⠂⡠⢂⡪⠋  ⠁⡆
⡶⠉ ⢀⡀⠁⡁⢸⣿⣿⢠⣾⡟⠁⣿⣿⡇ ⢀⠈⠉⠁    ⣀⠷⣹⣏⣷⢏⠹⠁    ⠈⢈ ⢇ ⢸⠱⢸⡏⡀⡶⡸⠎  ⠰⠁⡸
⢈⡕⡈⠁⠐⠂⢀⢸⣿⣿⣾⠏⣿⣿⡿⣻⣿⢞⡢⠄ ⠈ ⡀⡤⠂⠁⠉⠌       ⢀⢀⠠⠐⢄ ⡀⢆⠎⢹⣶⣷⣧⡈⠈⠉⠤⠂⠉⢀⠱⡀
⢠⡊    ⠁⣸⣿⣿⣿⣀⠉⡻⡏⠋⠁ ⠁⠒⠒⡀⣍⠍⠁ ⡀ ⢠⠂     ⢀⠈⠄⢀⠄⡒⠅⠈⢄⢡ ⢿⣿⣷⣿⡄ ⠐⠄⠤ ⠜⢀
⠐⠁ ⠤⠒⢠⣾⣿⣿⣿⣿⣿⣷⣄⢄  ⢀ ⡏ ⢰⣃⠊⡐⠐⠁⢀⠈  ⣀ ⠰⠢⢀⠂⡰⠈⠂  ⡱⠂⢂⡇⡈⠻⢿⣿⠇   ⡤⠄⣀⡰⠁
    ⠁⣾⣿⣿⣿⣿⣿⣿⣿⣿⣦ ⠄ ⠉   ⠸⠫⢞⠈⣰⠈ ⡐⢲⣿⡏       ⢠⡾ ⣀⠊⢱ ⠠⡀    ⢈⢀⡐⠤⣕⡄
    ⢰⣿⡿⠛⠉   ⠈⠙⠛         ⠈⠈ ⠻⠔⠁⢸⡍⡇      ⢀⣏ ⢀⠠⠆ ⠣⡀⠈⡠⡀⠉⠢⡤⠢⣈⡡⣢⠦
⠈⠁           ⢻⣇               ⢸⡇⡇      ⣼⡿⠉  ⢀⡇ ⠑⡄⠑⣌⢄ ⠙⢄⠠⡪⣅
             ⠈⣾⡆              ⢸⣏⡇     ⢠⣿⠇   ⠸⢌⢢⢄⡠⠣⠈⠢⡁⡈⣎⢢⡬⠃

               Energy refinement on samples using orca
                          Ver. 0.6.2 by mlee
```

In this phase, we use DFT calculations with Orca 5.0. The default setting uses wB97X functional and 6-31(d) basis set, but these settings can be adjusted as needed.

```
╔════════════════════════════════════════════════════════════════════╗
║                         7. Refining forces                         ║
╚════════════════════════════════════════════════════════════════════╝
Arguments provided:
  input_path: /home/pekora/example/output/xtb.h5
  output_path: /home/pekora/example/output/wb97x.db
  max_workers: 15
  orca: /home/pekora/package/orca/orca_5_0_4/orca

Restarting calculation from /home/pekora/example/output/wb97x.db
640 points are skipped.

Formulas: 100%|██████████████████████| 2/2 [85:50:01<00:00, ? hour/it]
wB97X calculation finished!

```

You can check your compiled database using ASE:
```
$ ase db wb97x.db
id|age|user   |formula |calculator|    energy|natoms| fmax|pbc|charge|   mass
 1| 5d|pekora|C4ClH4NO|orca      |-20266.198|    11|5.874|FFF| 0.000|117.532
 2| 5d|pekora|C4ClH4NO|orca      |-20269.074|    11|0.470|FFF| 0.000|117.532
 3| 5d|pekora|C4ClH4NO|orca      |-20268.333|    11|5.994|FFF| 0.000|117.532
 4| 5d|pekora|C4ClH4NO|orca      |-20268.047|    11|1.195|FFF| 0.000|117.532
 5| 5d|pekora|C4ClH4NO|orca      |-20266.059|    11|3.630|FFF| 0.000|117.532
 6| 5d|pekora|C4ClH4NO|orca      |-20266.920|    11|4.553|FFF| 0.000|117.532
 7| 5d|pekora|C4ClH4NO|orca      |-20266.081|    11|1.022|FFF| 0.000|117.532
 8| 5d|pekora|C4ClH4NO|orca      |-20265.240|    11|4.314|FFF| 0.000|117.532
 9| 5d|pekora|C4ClH4NO|orca      |-20265.014|    11|7.924|FFF| 0.000|117.532
10| 5d|pekora|C4ClH4NO|orca      |-20268.711|    11|3.512|FFF| 0.000|117.532
11| 5d|pekora|C4ClH4NO|orca      |-20266.886|    11|5.938|FFF| 0.000|117.532
12| 5d|pekora|C4ClH4NO|orca      |-20266.322|    11|3.704|FFF| 0.000|117.532
13| 5d|pekora|C4ClH4NO|orca      |-20266.081|    11|1.021|FFF| 0.000|117.532
14| 5d|pekora|C4ClH4NO|orca      |-20265.532|    11|3.059|FFF| 0.000|117.532
15| 5d|pekora|C4ClH4NO|orca      |-20267.115|    11|3.885|FFF| 0.000|117.532
16| 5d|pekora|C4ClH4NO|orca      |-20262.912|    11|6.171|FFF| 0.000|117.532
17| 5d|pekora|C4ClH4NO|orca      |-20268.863|    11|1.657|FFF| 0.000|117.532
18| 5d|pekora|C4ClH4NO|orca      |-20265.663|    11|4.222|FFF| 0.000|117.532
19| 5d|pekora|C4ClH4NO|orca      |-20263.405|    11|5.723|FFF| 0.000|117.532
20| 5d|pekora|C4ClH4NO|orca      |-20267.567|    11|5.143|FFF| 0.000|117.532
Rows: 53842 (showing first 20)
```

Finally, compile our wb97x.db sample :
```
╔════════════════════════════════════════════════════════════════════╗
║                     8. Compiling final samples                     ║
╚════════════════════════════════════════════════════════════════════╝
Arguments provided:
  input_path: /home/pekora/example/output/wb97x.db
  output_path: /home/pekora/example/output/wb97x.h5

Compiled successfully!
```








