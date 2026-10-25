# 後期の仮説7とrunEDDBの補足記録

資料更新：2026年10月22日。元の計算データを選んだ複製です。[MANIFEST.json](MANIFEST.json) に元の相対パスと、元ファイル・公開ファイルのSHA-256を記録しています。個人を含む絶対パスの接頭部分だけを置換し、数値・条件・状態は保持しています。

## 仮説7：既存構造の予備検討から独立探索へ

初期の [N6プロトン化の予備検討](../research_results/comparison/protonation_screen/FINDINGS_JA.md) は、既存の共通骨格代表構造からの検討でした。その後、N6H+の両配置を含む独立ETKDG探索、GFN2-xTB/ALPB(水)最適化、Hessian・熱補正、選択構造のDFT単一点へ進んでいます。

| 資料 | 確認できること |
| --- | --- |
| [独立探索の短い結果](protonation_ensemble_refinement/FINDINGS_JA.md) | 各N6配置200候補から探索し、旧予備検討よりBzで約25.468、SBで約25.237 kJ/mol低い構造を得た |
| [独立探索の結果](protonation_ensemble_refinement/results.json)・[状態](protonation_ensemble_refinement/status.json) | 設定、候補、選択、由来、処理状態 |
| [熱化学サイクル](protonation_ensemble_refinement/thermochemistry_cycle.json)・[状態](protonation_ensemble_refinement/thermochemistry_status.json) | xTB修正RRHOを含む相対プロトン化差と限界 |
| [DFT単一点の結果](h7_h6_dft_singlepoints/results.json)・[状態](h7_h6_dft_singlepoints/status.json) | B3LYP-D3BJ/def2-TZVPの気相／CPCM(水)などの選択構造感度。水中の相対差は集計法により約−0.62〜+0.13 kJ/mol |

これらは絶対pKa、生理的なプロトン化率、完全な溶液配座分布や加水分解速度を求めたものではありません。旧予備検討と独立探索を同じ構造集合として混ぜません。

## 仮説2：runEDDBの実行ログ

`eddb_logs/` には、2配座組×3構造（Bz、SB、SBのTMS→H固定構造）について、断片全体・π成分・NAO手法感度・手動軌道対応・共役経路のログ48件を収録しています。波動関数そのものは含みません。

例として [pair001 SBの手動対応π解析](eddb_logs/pair001/sb_optimized/fragment_pi_manual_matched.log) では、ビルド日2026-Aug-15、NVB、frozen-NMB、9原子断片、選択7軌道、および実行時に提示された引用DOIを確認できます。[集約結果](../research_results/comparison/hypothesis2_validation/eddb/results.json) と [対応差CSV](../research_results/comparison/hypothesis2_validation/eddb/paired_deltas.csv) も併せて参照してください。

EDDBは基底状態の非局在化を表す解析指標です。NBO二次摂動エネルギー・遷移状態障壁・反応速度の代替値として解釈しません。実行ログでfrozen-NMBの方法文献が `in preparation` とされていることも保持しています。現在のマニュアルの追加機能・版を、この過去の計算で使用したとは扱いません。
