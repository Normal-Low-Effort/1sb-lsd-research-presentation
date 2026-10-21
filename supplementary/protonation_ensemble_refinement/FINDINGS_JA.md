# 仮説7 N6H+独立ensemble refinement

N6H+の両配置を明示し、各配置200 ETKDG conformersから力場選別後、GFN2-xTB/ALPB(水)で最適化した。既存screenは読み取り専用で比較対象として保持した。これはpKa計算でもORCA計算でもない。

| molecule | previous minimum / Eh | refined minimum / Eh | refined−previous / kJ mol⁻¹ | unique xTB clusters | new representatives |
| --- | ---: | ---: | ---: | ---: | ---: |
| 1Bz-LSD_RR | -89.760505641393 | -89.770205818179 | -25.468 | 22 | 18 |
| 1SB-LSD_RR | -101.981166109611 | -101.990778391497 | -25.237 | 24 | 19 |

新規低エネルギーbasinまたは反対N6配置が残る場合、それらを含めて相対プロトン移動cycleを組む。xTB順位だけでpKa差を断定しない。
