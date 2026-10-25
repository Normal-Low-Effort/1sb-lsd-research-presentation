# 軽量解析データの目次

このフォルダは主に2026年8月23日までの解析保存データです。計算条件と仮説ごとの判定は [研究本文](../METHODS_AND_RESULTS_JA.md)、データの原本対応と注意点は [公開データ案内](../RESEARCH_DATA_GUIDEja.md) を参照してください。以下の表・JSONは作成時点の集合と解釈を保持しています。

| 内容 | 読むファイル |
| --- | --- |
| Bz/SB予備比較・仮説1と2 | [PRELIMINARY_COMPARISON_JA.md](comparison/PRELIMINARY_COMPARISON_JA.md) |
| para-H/Me/iPr/tBu/TMSの対照系列 | [FINDINGS_JA.md](comparison/para_substituent_series/FINDINGS_JA.md) |
| 仮説4・5：配座・分子内接触の元集計 | [FINDINGS_JA.md](comparison/hypotheses4_5/FINDINGS_JA.md) |
| 仮説6：明示的水1分子予備検討 | [FINDINGS_JA.md](comparison/explicit_water_screen/FINDINGS_JA.md) |
| 仮説7：初期のN6プロトン化予備検討 | [FINDINGS_JA.md](comparison/protonation_screen/FINDINGS_JA.md) |
| 仮説2：固定構造・手法の感度 | [analysis.json](comparison/hypothesis2_validation/analysis.json) |
| 仮説2：EDDB解析 | [results.json](comparison/hypothesis2_validation/eddb/results.json)、[対応差CSV](comparison/hypothesis2_validation/eddb/paired_deltas.csv) |
| 代謝情報の証拠と推論の境界 | [METABOLIC_INFERENCE_LIMITS_JA.md](context/METABOLIC_INFERENCE_LIMITS_JA.md) |
| 分子ごとの計算集合 | [Bzの計算要約](ensembles/1Bz-LSD_RR/RUN_SUMMARY.md)、[SBの計算要約](ensembles/1SB-LSD_RR/RUN_SUMMARY.md) |
| 再利用・失敗履歴・実装上の来歴 | [IMPLEMENTATION_NOTES.md](provenance/IMPLEMENTATION_NOTES.md)、[operational_history.json](provenance/operational_history.json) |
| 保存データの原本位置とハッシュ | [SNAPSHOT_MANIFEST.json](SNAPSHOT_MANIFEST.json) |

後期の仮説7の独立探索・DFT感度とrunEDDBログは [supplementary](../supplementary/README.md)、2026年8月25〜26日を含む仮説11の選択資料は [h11_evidence](../h11_evidence/README.md) にあります。

`current_best_structures/` のXYZは各runで得た探索内最良候補です。実験構造や大域最小の証明ではありません。Freqが部分集合のみであること、共通骨格の群数が対象集合で変わること、電子エネルギー重みが実測存在比ではないことに注意してください。
