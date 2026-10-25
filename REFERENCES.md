# 参考文献と出典対応

書誌・公式資料の確認日：2026年10月22日。

外部資料は化合物の構造、既報の観測、計算方法の典拠です。本研究固有の計算値は [保存した解析データ](research_results/READMEja.md)、[後期補足データ](supplementary/README.md)、[仮説11の記録](h11_evidence/README.md) を参照してください。過去に閲覧した全ページや当時の閲覧日時を完全に復元した一覧ではありません。

## 化合物・既報の観測

<a id="ref-1"></a>

**[1]** 厚生労働省．[2026年3月3日 薬事審議会 指定薬物部会 議事録](https://www.mhlw.go.jp/stf/newpage_73932.html)．審議物質③、資料No.3-3、(5)マウス体内での代謝の説明。1SB-LSD投与後のマウス血清をLC-MS/MSで分析しLSDを検出したとの報告。変換速度や1Bz-LSD中間体は示していない。同じ説明の(4)に受容体試験の記載がある。

<a id="ref-2"></a>

**[2]** 厚生労働省．[2025年8月28日 薬事審議会 指定薬物部会 議事録](https://www.mhlw.go.jp/stf/newpage_65805.html)．審議物質③、資料No.3、(5)マウス体内での代謝の説明。1Bz-LSDを投与した別の試験でLSDを検出したとの報告。[1]と合わせても1SB→1Bzの証拠にはならない。

<a id="ref-3"></a>

**[3]** Brandt, S. D., Kavanagh, P. V., Gare, S., Elliott, S. P., Stratford, A., and Halberstadt, A. L. [Analytical and Pharmacological Characterization of 1-(Furan-2-Carbonyl)-LSD (1F-LSD) and Comparison With 1-(Thiophene-2-Carbonyl)-LSD (1T-LSD)](https://doi.org/10.1002/dta.3829). *Drug Testing and Analysis* **17** (2025): 1283–1293. DOI: 10.1002/dta.3829. オンライン公開は2024年、巻号は2025年。1F/1T-LSDは1SB-LSDと別化合物であり、1SBの代謝速度を示す資料ではない。

<a id="ref-4"></a>

**[4]** Azuma, Y., Tanaka, M., Asada, A., and Doi, T. [In vitro metabolic fate of 1-[3-(trimethylsilyl)propanoyl] lysergic acid diethylamide (1S-LSD), a silicon-containing LSD analog](https://doi.org/10.1007/s11419-025-00735-2). *Forensic Toxicology* **44** (2026): 72–85. DOI: 10.1007/s11419-025-00735-2. オンライン公開は2025年、巻号は2026年。1S-LSDは1SB-LSDと異なる結合様式の類縁体であり、代謝結果をそのまま外挿しない。

<a id="ref-5"></a>

**[5]** National Center for Biotechnology Information. [PubChem Compound Summary: (+)-Lysergic acid diethylamide, CID 5761](https://pubchem.ncbi.nlm.nih.gov/compound/5761). LSDの名称・構造情報の参照先。発表でRDKit生成模型を使用する場合、その3D座標は計算による参考構造であり、PubChemの実験構造という意味ではない。

## ソフトウェアと主要解析法

<a id="ref-6"></a>

**[6]** Neese, F. [Software Update: The ORCA Program System—Version 6.0](https://doi.org/10.1002/wcms.70019). *WIREs Computational Molecular Science* **15** (2025): e70019. DOI: 10.1002/wcms.70019. 使用ソフトウェアはORCA **6.1.1**。[公式引用案内](https://www.faccts.de/docs/orca/6.1/manual/contents/preface/howtocite.html)がORCA 6向けに示す更新論文。ソフトウェアの引用と、実際に用いた計算法の引用は区別する。

<a id="ref-7"></a>

**[7]** Landrum, G. et al. [rdkit/rdkit: 2026_03_5 (Q1 2026) Release](https://doi.org/10.5281/zenodo.21741729). Zenodo (2026), Release_2026_03_5. DOI: 10.5281/zenodo.21741729. 主配座集合の記録にあるRDKit **2026.03.5**に対応する版付き出典。[公式引用案内](https://www.rdkit.org/new_docs/Overview.html)。

<a id="ref-8"></a>

**[8]** Bannwarth, C., Ehlert, S., and Grimme, S. [GFN2-xTB—An Accurate and Broadly Parametrized Self-Consistent Tight-Binding Quantum Chemical Method with Multipole Electrostatics and Density-Dependent Dispersion Contributions](https://doi.org/10.1021/acs.jctc.8b01176). *Journal of Chemical Theory and Computation* **15** (2019): 1652–1671. DOI: 10.1021/acs.jctc.8b01176. xTB予備探索の方法文献。ALPB溶媒モデルは下の方法補足も参照。

<a id="ref-9"></a>

**[9]** Szczepanik, D. W., Andrzejak, M., Dominikowska, J., Pawełek, B., Krygowski, T. M., Szatylowicz, H., and Solà, M. [The electron density of delocalized bonds (EDDB) applied for quantifying aromaticity](https://doi.org/10.1039/C7CP06114E). *Physical Chemistry Chemical Physics* **19** (2017): 28970–28981. DOI: 10.1039/C7CP06114E. 仮説2の断片EDDB解析の文献。[runEDDB公式ページ](https://aromaticity.uj.edu.pl/runeddb/)と[引用案内](https://aromaticity.uj.edu.pl/runeddb/manual.html)も参照。使用記録はビルド日**2026-Aug-15**で特定し、現在の配布版と同一とは扱わない。

## 計算方法の補足出典

詳細条件を追うための方法文献。ORCAが実行時に出力した追加引用候補は [NEB計算のBibTeX](h11_evidence/h11_orca_hydroxide_neb_v1/bz/placement_02/neb_ts/attempt_001/neb.bibtex) に、runEDDBが実際に提示したDOIは [実行ログ](supplementary/eddb_logs/pair001/sb_optimized/fragment_pi_manual_matched.log) にも残している。BibTeXは当時の自動生成物であり、書誌表記の最終校正済み一覧という意味ではない。

| 方法 | 出典 |
| --- | --- |
| ETKDG | Riniker, S., and Landrum, G. A. [Better Informed Distance Geometry: Using What We Know To Improve Conformation Generation](https://doi.org/10.1021/acs.jcim.5b00654). *J. Chem. Inf. Model.* **55** (2015): 2562–2574. |
| ETKDGの後続改良 | Wang, S., Witek, J., Landrum, G. A., and Riniker, S. [Improving Conformer Generation for Small Rings and Macrocycles Based on Distance Geometry and Experimental Torsional-Angle Preferences](https://doi.org/10.1021/acs.jcim.0c00025). *J. Chem. Inf. Model.* **60** (2020): 2044–2058. 使用実装の詳細は[RDKit Book](https://www.rdkit.org/docs/RDKit_Book.html)も参照。 |
| RDKitのMMFF実装 | Tosco, P., Stiefl, N., and Landrum, G. [Bringing the MMFF force field to the RDKit: implementation and validation](https://doi.org/10.1186/s13321-014-0037-3). *Journal of Cheminformatics* **6** (2014): 37. |
| B3LYP関連の交換混合 | Becke, A. D. [Density-functional thermochemistry. III. The role of exact exchange](https://doi.org/10.1063/1.464913). *J. Chem. Phys.* **98** (1993): 5648–5652. |
| LYP相関 | Lee, C., Yang, W., and Parr, R. G. [Development of the Colle-Salvetti correlation-energy formula into a functional of the electron density](https://doi.org/10.1103/PhysRevB.37.785). *Phys. Rev. B* **37** (1988): 785–789. |
| def2基底 | Weigend, F., and Ahlrichs, R. [Balanced basis sets of split valence, triple zeta valence and quadruple zeta valence quality for H to Rn: Design and assessment of accuracy](https://doi.org/10.1039/B508541A). *Phys. Chem. Chem. Phys.* **7** (2005). |
| PBE0 | Adamo, C., and Barone, V. [Toward reliable density functional methods without adjustable parameters: The PBE0 model](https://doi.org/10.1063/1.478522). *J. Chem. Phys.* **110** (1999): 6158–6170. |
| D3分散補正 | Grimme, S., Antony, J., Ehrlich, S., and Krieg, H. [A consistent and accurate ab initio parametrization of density functional dispersion correction (DFT-D) for the 94 elements H-Pu](https://doi.org/10.1063/1.3382344). *J. Chem. Phys.* **132** (2010): 154104. |
| BJ減衰 | Grimme, S., Ehrlich, S., and Goerigk, L. [Effect of the damping function in dispersion corrected density functional theory](https://doi.org/10.1002/jcc.21759). *J. Comput. Chem.* **32** (2011): 1456–1465. |
| ORCAのCPCM実装 | Garcia-Ratés, M., and Neese, F. [Effect of the Solute Cavity on the Solvation Energy and its Derivatives within the Framework of the Gaussian Charge Scheme](https://doi.org/10.1002/jcc.26139). *J. Comput. Chem.* **41** (2020): 922–939. |
| ALPB | Ehlert, S., Stahn, M., Spicher, S., and Grimme, S. [Robust and Efficient Implicit Solvation Model for Fast Semiempirical Methods](https://doi.org/10.1021/acs.jctc.1c00471). *J. Chem. Theory Comput.* **17** (2021): 4250–4261. |
| MBIS電荷 | Verstraelen, T. et al. [Minimal Basis Iterative Stockholder: Atoms in Molecules for Force-Field Development](https://doi.org/10.1021/acs.jctc.6b00456). *J. Chem. Theory Comput.* (2016). |
| CHELPG電荷 | Breneman, C. M., and Wiberg, K. B. [Determining atom-centered monopoles from molecular electrostatic potentials. The need for high sampling density in formamide conformational analysis](https://doi.org/10.1002/jcc.540110311). *J. Comput. Chem.* **11** (1990): 361–373. |
| NEB-TS | Ásgeirsson, V. et al. [Nudged Elastic Band Method for Molecular Reactions Using Energy-Weighted Springs Combined with Eigenvector Following](https://doi.org/10.1021/acs.jctc.1c00462). *J. Chem. Theory Comput.* **17** (2021): 4929–4945. |
| NAO／NPA | Reed, A. E., Weinstock, R. B., and Weinhold, F. [Natural population analysis](https://doi.org/10.1063/1.449486). *J. Chem. Phys.* **83** (1985): 735–746. |
| runEDDBのBOP | Szczepanik, D. W., Żak, E., Dyduch, K., and Mrozek, J. [Electron delocalization index based on bond order orbitals](https://doi.org/10.1016/j.cplett.2014.01.006). *Chem. Phys. Lett.* **593** (2014): 154–159. |
| EDDB密度分解 | Szczepanik, D. W. [A new perspective on quantifying electron localization and delocalization in molecular systems](https://doi.org/10.1016/j.comptc.2016.02.003). *Comput. Theor. Chem.* **1080** (2016): 33–37. |
| NOBD関連 | Szczepanik, D. W. et al. [A uniform approach to the description of multicenter bonding](https://doi.org/10.1039/C4CP02932A). *Phys. Chem. Chem. Phys.* **16** (2014): 20514–20523. |

runEDDBのfrozen-NMB構成の文献は、**当時の実行ログでは `in preparation`** と記載されている。この公開資料では、その記載を既刊論文として補完しない。手法と使用版はログと設定で特定する。現在の公式マニュアルは更新されるため、過去の計算の採用条件を確認する際は収録ログを優先する。

## 主張と出典の対応

| 主張・方法 | 出典 |
| --- | --- |
| LSDの名称・基本構造 | [5] |
| 1SB-LSD投与後にマウス血清でLSDを検出 | [1]。速度や主要経路の実証とは区別 |
| 1Bz-LSD投与後にLSDを検出 | [2]。1SB→1Bzの証拠とは区別 |
| N1アシル類縁体・Si含有類縁体の参考例 | [3][4]。1SBへの直接外挿はしない |
| ORCA、RDKit、GFN2-xTB | [6][7][8]と使用した計算法の補足出典 |
| runEDDBの断片・π非局在化解析 | [9]、NAO・BOP・EDDB密度分解・NOBDの補足出典、収録ログ |
| 本研究固有の数値・採否 | 解析保存データ、後期補足データ、仮説11の計算記録。「本研究の計算結果」と明記 |
