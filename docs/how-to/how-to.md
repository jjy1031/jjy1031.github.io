---
layout: default
title: How-to-use
nav_order: 6
---

## Example 
<html lang="en">
                        <p>This page provides a guide for using Dandelion, which efficiently generates an extensive database by sampling both equilibrium and reactive regions of chemical compound space.</p>
                        <div align="center">
                            <img width="1600" alt="all" src="https://github.com/user-attachments/assets/6ff5bf37-7ce5-4980-a268-ee0f1d2c185d"/>
                        </div>
                        <p>
                            You can download these structures from <a href="https://github.com/mhyeok1/dand_docs/blob/docs/assets/mother_structures_for_tut.Zip">HERE</a>
                        </p>
                        <p>
                            Let’s assume that we are interested in expanding dataset from 5 given mother structures. First, each mother structures needs to be optimized to serve as a good starting point for GSM. This can be achieved by performing geometry optimization using GFN2-xTB. Ensure that all the prepared mother structures are in specific <code class="language-plaintext highlighter-rouge">input_path</code>
                            , and saved in <code class="language-plaintext highlighter-rouge">.xyz</code>
                            file format.
                        </p>
                        <!-- 파일명: _includes/tabs1.html -->
                        <style>
                            /* 외부 탭 (상위 탭) CSS */
                            .outer-tabs {
                                display: flex;
                                flex-wrap: wrap !important;
                                /* 절대 줄바꿈 X */
                                width: 100% !important;
                                /* 부모 너비만큼 확장 */
                                max-width: none !important;
                                /* 테마의 max-width 제한 해제 */
                                overflow-x: auto !important;
                                margin-bottom: 1rem;
                                
                            }

                            .outer-tabs input[type="radio"] {
                                display: none;
                            }

                            .outer-tabs label {
                                background: #eee;
                                padding: 0.5rem 1rem;
                                margin-right: 0.2rem;
                                cursor: pointer;
                                border-radius: 5px 5px 0 0;
                            }

                            .outer-tabs .outer-tab {
                                display: none;
                                z-index:2;
                                left:20px;
                                top: 647px;
                                width: 90%;
                                position:absolute;
                                margin: 0; 
                                border: 1px solid #ccc;
                                padding: 1rem;
                                border-radius: 0 5px 5px 5px;
                                background: #f9f9f9;
                                height:450px;
                            }
                            .next{
                                position:relative;
                            }
                            .outer-tabs input[type="radio"]:checked + label {
                                background: #ddd;
                                
                            }

                            .outer-tabs input[type="radio"]:checked + label + .outer-tab {
                                display: block;
                            }

                            /* 내부(하위) 탭 CSS */
                            .nested-tabs {
                                position:relative;
                                display: flex;
                                flex-wrap: wrap;
                                margin-bottom: 1rem;
                            }

                            .nested-tabs input[type="radio"] {
                                display: none;
                            }

                            .nested-tabs label {
                                background: #eee;
                                padding: 0.4rem 0.8rem;
                                margin-right: 0.2rem;
                                cursor: pointer;
                                border-radius: 3px 3px 0 0;
                                font-size: 0.9rem;
                            }

                            .nested-tabs .nested-tab {
                                position: absolute;
                                display: none;
                                top: 35px;
                                width: 100%;
                                border: 1px solid #ccc;
                                padding: 1rem;
                                border-radius: 0 3px 3px 3px;
                                background: #f9f9f9;
                                font-size: 0.9rem;
                            }

                            .nested-tabs input[type="radio"]:checked + label {
                                background: #ddd;
                            }

                            .nested-tabs input[type="radio"]:checked + label + .nested-tab {
                                display: block;
                            }

                            /* 트리 구조 전체에 폰트를 강제 적용하는 예시 */
                            .tree-structure {
                                font-family: "Courier New", Courier, monospace;
                                white-space: pre;
                                /* 트리 구조 줄맞춤 유지 */
                                font-size: 14px;
                                /* 필요에 따라 조정 */
                            }
                        </style>
                        <div class="outer-tabs">
                            <!-- 상위 탭 1: Structure -->
                            <input type="radio" name="outer-tabs" id="outer-tab-structure" checked=""/>
                            <label for="outer-tab-structure">Molecular Structure</label>
                            <div class="outer-tab">
                                <!-- 내부 탭: Structure 1 ~ 5 -->
                                <div class="nested-tabs">
                                    <!-- Structure 1 탭 -->
                                    <input type="radio" name="nested-tabs" id="nested-tab-1" checked=""/>
                                    <label for="nested-tab-1">Cl7138</label>
                                    <div class="nested-tab">
                                        <pre>11

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
                                    <!-- Structure 2 탭 -->
                                    <input type="radio" name="nested-tabs" id="nested-tab-2"/>
                                    <label for="nested-tab-2">Cl7164</label>
                                    <div class="nested-tab">
                                        <pre>11

Cl          -2.39258127     0.28231570    -0.01385005
C           -0.68310066     0.20635979    -0.00403803
C            0.16552497     1.27600708     0.00026502
N            1.44362678     0.77431569     0.00784403
C            1.39365231    -0.58454810     0.00826508
C            0.08349707    -0.98200816     0.00096948
O            2.50361977    -1.35609092     0.01501512
H           -0.03190061     2.32693767    -0.00140328
H            2.27812655     1.33804774     0.01230499
H           -0.28142194    -1.98626313    -0.00060125
H            3.29566201    -0.80722536     0.01951589
        </pre>
                                    </div>
                                    <!-- Structure 3 탭 -->
                                    <input type="radio" name="nested-tabs" id="nested-tab-3"/>
                                    <label for="nested-tab-3">Cl7166</label>
                                    <div class="nested-tab">
                                        <pre>11

Cl          -2.00893918     0.40295557    -0.00764421
C           -0.29771663     0.35154368    -0.00075549
C            0.54793878     1.43295658     0.00409959
N            1.81992358     0.96593316     0.00865862
C            1.80854293    -0.39913088     0.00682335
C            0.50099341    -0.81752681     0.00095918
O            0.01488146    -2.08621568    -0.00268068
H            0.31666509     2.47770505     0.00452804
H            2.64817101     1.53578659     0.01277203
H            2.71386897    -0.97278066     0.00975244
H            0.74959357    -2.70839460    -0.00051687         
        </pre>
                                    </div>
                                    <!-- Structure 4 탭 -->
                                    <input type="radio" name="nested-tabs" id="nested-tab-4"/>
                                    <label for="nested-tab-4">Cl7168</label>
                                    <div class="nested-tab">
                                        <pre>11

Cl          -2.01971811     0.41732375    -0.00701530
C           -0.30596543     0.36509037    -0.00029388
C            0.56777110     1.47712449     0.00608804
C            1.83906018     0.98609080     0.00989984
N            1.77171936    -0.38218797     0.00608191
C            0.46616306    -0.77046403    -0.00014784
O            0.07632092    -2.06553918    -0.00504359
H            0.26865357     2.50434058     0.00754660
H            2.78137460     1.49355488     0.01497598
H            2.56698811    -0.99998241     0.00769027
H            0.84415267    -2.64700730    -0.00383202
        </pre>
                                    </div>
                                    <!-- Structure 5 탭 -->
                                    <input type="radio" name="nested-tabs" id="nested-tab-5"/>
                                    <label for="nested-tab-5">Cl7188</label>
                                    <div class="nested-tab">
                                        <pre>11

O           -2.77130538     0.48671433    -0.01587455
N           -1.38919947     0.48754498    -0.00810904
C           -0.59828425     1.57889594    -0.00382135
C            0.70875931     1.15154908     0.00349984
C            0.66708077    -0.25141656     0.00339239
C           -0.65288767    -0.64382920    -0.00390799
Cl           2.01857151    -1.30606170     0.01101477
H           -3.06365189     1.40967237    -0.01669118
H           -1.00051429     2.57314043    -0.00614438
H            1.58418729     1.76695954     0.00832626
H           -1.10380593    -1.61309521    -0.00634078
        </pre>
                                    </div>
                                </div>
                            </div>
                            <!-- 상위 탭 2: File Structure -->
                            <input type="radio" name="outer-tabs" id="outer-tab-file"/>
                            <label for="outer-tab-file">File Structure</label>
                            <div class="outer-tab">
                                <pre class="tree-structure">📂 mother_strucs
 ├── 📂 Cl7138
 │   └── 📂 ClGeom-m7138-i1-c1-opt
 │       └── 📄 struc.xyz
 ├── 📂 Cl7164
 │   └── 📂 ClGeom-m7164-i1-c1-opt
 │       └── 📄 struc.xyz
 ├── 📂 Cl7166
 │   └── 📂 ClGeom-m7166-i1-c1-opt
 │       └── 📄 struc.xyz
 ├── 📂 Cl7168
 │   └── 📂 ClGeom-m7168-i1-c1-opt
 │       └── 📄 struc.xyz
 └── 📂 Cl7188
     └── 📂 ClGeom-m7188-i1-c1-opt
         └── 📄 struc.xyz
    </pre></div> </div><p class="next"><pre>













        




        
    </pre>To run dandelion, your current conda environment should be <strong>ts</strong>. You can enter the following command in terminal for more information:</p> <div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="err">$</span> <span class="n">dandelion_sample</span> <span class="o">-</span><span class="n">h</span>

<span class="n">usage</span><span class="p">:</span> <span class="n">dandelion_sample</span> <span class="p">[</span><span class="o">-</span><span class="n">h</span><span class="p">]</span> <span class="o">-</span><span class="n">i</span> <span class="n">INPUT_PATH</span> <span class="o">-</span><span class="n">o</span> <span class="n">OUTPUT_PATH</span> <span class="o">-</span><span class="n">n</span> <span class="n">MAX_WORKERS</span>

<span class="n">Do</span> <span class="n">SEGSM</span> <span class="ow">and</span> <span class="n">NEB</span> <span class="k">from</span> <span class="n">mother</span> <span class="n">structures</span><span class="p">,</span> <span class="n">Other</span> <span class="n">parameters</span> <span class="n">can</span> <span class="n">be</span> <span class="nb">set</span> <span class="ow">in</span> <span class="n">each</span>
<span class="n">modules</span>

<span class="n">options</span><span class="p">:</span>
  <span class="o">-</span><span class="n">h</span><span class="p">,</span> <span class="o">--</span><span class="n">help</span>            <span class="n">show</span> <span class="n">this</span> <span class="n">help</span> <span class="n">message</span> <span class="ow">and</span> <span class="nb">exit</span>
  <span class="o">-</span><span class="n">i</span> <span class="n">INPUT_PATH</span><span class="p">,</span> <span class="o">--</span><span class="n">input_path</span> <span class="n">INPUT_PATH</span>
                        <span class="n">Input</span> <span class="n">path</span> <span class="n">of</span> <span class="n">mother</span> <span class="n">structures</span>
  <span class="o">-</span><span class="n">o</span> <span class="n">OUTPUT_PATH</span><span class="p">,</span> <span class="o">--</span><span class="n">output_path</span> <span class="n">OUTPUT_PATH</span>
                        <span class="n">Output</span> <span class="n">path</span> <span class="n">of</span> <span class="n">dandelion</span>
  <span class="o">-</span><span class="n">n</span> <span class="n">MAX_WORKERS</span><span class="p">,</span> <span class="o">--</span><span class="n">max_workers</span> <span class="n">MAX_WORKERS</span>
                        <span class="n">Number</span> <span class="n">of</span> <span class="n">worker</span> <span class="n">processes</span>
</code></pre></div></div> <p>Assuming your mother structures are saved as ‘struc.xyz’ in <code class="language-plaintext highlighter-rouge">/home/pekora/example/mother_strucs</code>, you can initiate sampling with the following command:</p> <div class="language-python highlighter-rouge"><div class="highlight"><pre class="highlight"><code><span class="n">python</span> <span class="n">dandelion_sample</span> <span class="o">-</span><span class="n">i</span> <span class="o">/</span><span class="n">home</span><span class="o">/</span><span class="n">pekora</span><span class="o">/</span><span class="n">example</span><span class="o">/</span><span class="n">mother_strucs</span> <span class="o">-</span><span class="n">o</span> <span class="o">/</span><span class="n">home</span><span class="o">/</span><span class="n">pekora</span><span class="o">/</span><span class="n">example</span><span class="o">/</span><span class="n">outputs</span> <span class="o">-</span><span class="n">n</span> <span class="mi">30</span>
</code></pre></div></div> <p>Then the following 6 steps will be executed automatically:</p> <div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>

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



</code></pre></div></div> <p>Dandelion first generates possible driving coordinates(seeds) from each mother structures.</p> <div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>╔════════════════════════════════════════════════════════════════════╗
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
</code></pre></div></div> <p>Based on generated GSM jobs, GSM can be executed. Some jobs can fail to converge or reach the product within the predefined maximum number of nodes and should be filtered out.</p> <div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>╔════════════════════════════════════════════════════════════════════╗
║                           2. Running GSM                           ║
╚════════════════════════════════════════════════════════════════════╝

Arguments provided:
  input_path: /home/pekora/example/output/1_gsm
  max_workers: 30

GSM on seeds: 100%|████████████████████████| 1406/1406 [4:57:13&lt;00:00]
GSM finished!

</code></pre></div></div> <p>Dandelion excludes some trivial pathways with strictly uphill energy trajectories, negligible energy variations, unfeasible structures, or those that are repetitive.</p> <div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>╔════════════════════════════════════════════════════════════════════╗
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

</code></pre></div></div> <p>Using the outputs of gsm, Dandelion runs NEB or Climbing-Image NEB. NEB can optimize some energy path using the concept of maximum force.</p> <div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>╔════════════════════════════════════════════════════════════════════╗
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

Seeds: 100%|███████████████████████████████████| 144/144 [04:34&lt;00:00]
xTB-NEB completed!

</code></pre></div></div> <p>In the fifth step, data is filtered based on specific criteria. For example, non-convergent reactions and those without a single negative eigenvalue in their Hessian matrices are excluded. This ensures focus on structures near valid paths. NEB results are further refined to avoid redundant structural data. A new band iteration is chosen only when the cumulative Fmax exceeds 0.1 eV/Å, saving DFT calculations and preventing overfitting to narrow PES regions.</p> <div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>
╔════════════════════════════════════════════════════════════════════╗
║                          5. Filtering NEB                          ║
╚════════════════════════════════════════════════════════════════════╝

Arguments provided:
  input_path: /home/pekora/example/output/3_neb
  output_path: /home/pekora/example/output/4_neb_filtered

Mothers: 100%|█████████████████████████████████████| 5/5 [00:20&lt;00:00]

40/53 rxns were saved to /home/pekora/example/output/4_neb_filtered/reactions.json
Filtering NEB finished!

</code></pre></div></div> <p>Sixth step is to compile samples:</p> <div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>
╔════════════════════════════════════════════════════════════════════╗
║                        6. Compiling samples                        ║
╚════════════════════════════════════════════════════════════════════╝

Arguments provided:
  input_path: /home/pekora/example/output/4_neb_filtered/reactions.json
  output_path: /home/pekora/example/output/xtb.h5
  fmax_threshold: 0.1

Compiling reactions: 100%|███████████████████████| 40/40 [00:03&lt;00:00]
Compiling finished!

</code></pre></div></div> <p>And there will be newly generated file in your output path, <code class="language-plaintext highlighter-rouge">xtb.h5</code> file.</p> <p>Next step is to execute dandelion_refine. You can enter -h or –help for more information:</p> <div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>$ dandelion_refine -h
usage: dandelion_refine [-h] -i INPUT_PATH -n MAX_WORKERS --orca ORCA

Refine force on obtained samples, Other parameters can be set in each modules

options:
  -h, --help            show this help message and exit
  -i INPUT_PATH, --input_path INPUT_PATH
                        Input path of working directory containing xtb.h5
  -n MAX_WORKERS, --max_workers MAX_WORKERS
                        Number of worker processes
  --orca ORCA           Path of the orca binary file
</code></pre></div></div> <p>Make sure that the path of the orca should point an orca <strong>executable file</strong>.</p> <p>If you enter like this:</p> <div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>$ dandelion_refine -i /home/pekora/example/outputs -n 15 --orca /home/pekora/package/orca/orca_5_0_4/orca
</code></pre></div></div> <p>2 steps below will be executed automatically !</p> <div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>         ⢀⣀⣀⣀⣀⣀⡀       ⢀⢀⣀⢀⠞⠖⠁⠡⡂⡆ ⡠⢀⡀
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
</code></pre></div></div> <p>In this phase, we use DFT calculations with Orca 5.0. The default setting uses wB97X functional and 6-31(d) basis set, but these settings can be adjusted as needed.</p> <div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>╔════════════════════════════════════════════════════════════════════╗
║                         7. Refining forces                         ║
╚════════════════════════════════════════════════════════════════════╝
Arguments provided:
  input_path: /home/pekora/example/output/xtb.h5
  output_path: /home/pekora/example/output/wb97x.db
  max_workers: 15
  orca: /home/pekora/package/orca/orca_5_0_4/orca

Restarting calculation from /home/pekora/example/output/wb97x.db
640 points are skipped.

Formulas: 100%|██████████████████████| 2/2 [85:50:01&lt;00:00, ? hour/it]
wB97X calculation finished!

</code></pre></div></div> <p>You can check your compiled database using ASE:</p> <div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>$ ase db wb97x.db
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
</code></pre></div></div> <p>Finally, compile our wb97x.db sample :</p> <div class="language-plaintext highlighter-rouge"><div class="highlight"><pre class="highlight"><code>╔════════════════════════════════════════════════════════════════════╗
║                     8. Compiling final samples                     ║
╚════════════════════════════════════════════════════════════════════╝
Arguments provided:
  input_path: /home/pekora/example/output/wb97x.db
  output_path: /home/pekora/example/output/wb97x.h5

Compiled successfully!
</code></pre></div></div> </main> <hr> <footer> <p><a href="#top" id="back-to-top">Back to top</a></p> <p class="text-small text-grey-dk-100 mb-0">Copyright &copy; 2023 Minhyeok Lee. Distributed by an <a href="https://raw.githubusercontent.com/mhyeok1/dand/refs/heads/main/LICENSE">MIT license.</a></p> <div class="d-flex mt-2"> <p class="text-small text-grey-dk-000 mb-0"> <a href="https://github.com/mhyeok1/dand_docs/edit/docs/docs/how-to.md" id="edit-this-page">Edit this page on GitHub.</a> </p> </div> </footer> </div> </div> <div class="search-overlay"></div> </div> </body> </html>
