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










       
 
