# 仮説11：Bz小モデルの検討経緯と到達点

文章更新：2026年10月25日。収録した計算記録は2026年8月26日まで。

仮説11では「非酵素的な化学反応が分解に寄与し得るか」という広い候補のうち、OH⁻が関わるN1脱アシル化の一部を小モデルで検討しました。OH⁻の直接攻撃が実際の代謝機構であるかは未確認です。xTBで候補を予備探索し、Bz側をORCAで検証しました。直接OptTSは採用できるTSに収束せず、端点OptとNEB-TS、Freqへ進みました。その後、IRCの前方停止に対して継続計算を行い、切断後の構造最適化まで実施しています。

**確認した中心は、四面体中間体側からのC–N切断段階です。** 収録記録の時点では、終点Freq、その先のプロトン移動、SB側との同条件比較は未実施です。以下は確認できた計算記録の流れであり、計算の選択動機や未記録の発見を補ったものではありません。

## モデルと条件

| 項目 | 条件 |
| --- | --- |
| 対象 | N-ベンゾイルindole由来のBz小モデル。OH由来原子を含む30原子。完全な1Bz-LSD／1SB-LSDではない |
| 電荷・多重度 | −1、1（一重項） |
| 手法 | ORCA 6.1.1、B3LYP/def2-SVP、TightSCF、CPCM(水)。明示的水のプロトンリレーは含めない |
| 採用NEB-TS | Bz placement 02、NEBの入力指定NImages 8、NEBとTSのMaxIter各200、Calc_Hess true、Freq |
| IRC | 初回Direction both、MaxIter 40、TS Hessian読込。前方継続はDirection down、MaxIter 80 |
| 終点Opt | COpt（Cartesian最適化）、MaxIter 300 |
| 資源設定 | 16 MPIプロセス、maxcore 1000 MB/プロセス。再実行時の必要資源を保証する値ではない |

## 計算段階と採否

| 段階 | 記録された結果・採否 | 主要資料 |
| --- | --- | --- |
| xTB段階的予備検討 | 8候補を処理。経路候補を選ぶ予備探索 | [状態](h11_hydroxide_stepwise_matrix_v1/status.json) |
| 直接OptTS | `FAILED`。採用TSではない。状態だけから失敗原因を一つに断定しない | [状態](h11_orca_hydroxide_ts_v1/status.json)、[結果](h11_orca_hydroxide_ts_v1/results.json) |
| 端点Opt＋NEB-TS＋Freq | Bz placement 02の採用TS候補。最終Freqの虚振動は1個、−191.86 cm⁻¹。主成分はC–N切断 | [結果](h11_orca_hydroxide_neb_v1/results.json)、[入力](h11_orca_hydroxide_neb_v1/bz/placement_02/neb_ts/attempt_001/neb.inp)、[出力](h11_orca_hydroxide_neb_v1/bz/placement_02/neb_ts/attempt_001/neb.out)、[TS座標](h11_orca_hydroxide_neb_v1/bz/placement_02/neb_ts/attempt_001/neb_NEB-TS_converged.xyz)、[Hessian](h11_orca_hydroxide_neb_v1/bz/placement_02/neb_ts/attempt_001/neb.hess) |
| 初回IRC | backwardは四面体中間体側へ収束、forwardは40反復上限。親runは `PARTIAL` | [結果](h11_orca_hydroxide_irc_v1/results.json)、[状態](h11_orca_hydroxide_irc_v1/status.json)、[入力](h11_orca_hydroxide_irc_v1/bz/placement_02/irc/attempt_001/irc.inp)、[出力](h11_orca_hydroxide_irc_v1/bz/placement_02/irc/attempt_001/irc.out) |
| 前方継続 | Direction downで収束。C–N切断・プロトン未移動側へ接続 | [結果](h11_orca_hydroxide_irc_v1/forward_continuation/results.json)、[入力](h11_orca_hydroxide_irc_v1/forward_continuation/bz/placement_02/downhill/attempt_001/continue.inp)、[出力](h11_orca_hydroxide_irc_v1/forward_continuation/bz/placement_02/downhill/attempt_001/continue.out) |
| 切断後終点Opt | 最適化成功。C–N 3.373 Å、O–H 0.975 Å、N–H 3.710 Å。Freq未実施のため局所極小性は未確認 | [結果](h11_orca_hydroxide_irc_v1/forward_continuation/endpoint_optimization/results.json)、[入力](h11_orca_hydroxide_irc_v1/forward_continuation/endpoint_optimization/bz/placement_02/opt/attempt_001/opt.inp)、[出力](h11_orca_hydroxide_irc_v1/forward_continuation/endpoint_optimization/bz/placement_02/opt/attempt_001/opt.out)、[座標](h11_orca_hydroxide_irc_v1/forward_continuation/endpoint_optimization/bz/placement_02/opt/attempt_001/opt.xyz) |

NEB出力には初期Hessianと最終TSの複数の振動数ブロックがあります。TS判定には最後の `VIBRATIONAL FREQUENCIES` ブロックと、対応するHessianを使います。初回IRCだけで全経路が収束したとは扱えません。継続と終点Optまで確認します。

## +1.410 kcal/molの基準

四面体中間体側の最適化構造の電子エネルギーは−783.123499069830 Eh、TSは−783.121252017982 Ehです。この差が約+1.410 kcal/molです。[反応物側のOpt出力](h11_orca_hydroxide_neb_v1/bz/placement_02/reactant_opt/attempt_001/opt.out)、[NEB出力](h11_orca_hydroxide_neb_v1/bz/placement_02/neb_ts/attempt_001/neb.out)

これは**四面体中間体側の構造を基準とするC–N切断の電子エネルギー障壁**です。アミド＋OH⁻からの付加、プロトン移動、標準状態・濃度・エントロピー等を合わせた全加水分解自由エネルギー障壁ではなく、生理的な速度や半減期へ換算できません。

## NEBの生成物側端点とIRC終点は異なる

NEBに用いた別途最適化済みの生成物側端点では、N–Hが約1.044 Åでした。一方、前方IRCを継続し、さらにOptした終点はN–Hが約3.710 Å、O–Hが約0.975 Åの**プロトン未移動**構造でした。したがって、NEBの両端を与えたことだけで「C–N切断とプロトン移動を一段階で確認した」とは言えません。

`h11_orca_hydroxide_neb_v1/results.json` の `reaction_electronic_kcal_mol`（約−32.617）は、最初に別途最適化した生成物側端点とのエネルギー差です。**実際にIRCで確認した切断後・プロトン未移動終点の反応エネルギーではありません。** また、初回IRCの古い `connection_validation.note` にあるendpoint minimaの説明は、後の継続結果まで反映した最終判定ではありません。解釈には継続IRCと終点Optの記録を優先します。[NEB端点の結果](h11_orca_hydroxide_neb_v1/results.json)、[切断後終点の結果](h11_orca_hydroxide_irc_v1/forward_continuation/endpoint_optimization/results.json)

## 未完了と次の課題

1. 切断後・プロトン未移動終点のFreqで局所極小性を確認する。
2. 必要ならプロトン移動を別段階として探索する。
3. Bzの経路定義を固め、同条件のSBと比較する。
4. 全加水分解を扱う場合は、アミド＋求核剤からの付加段階も評価する。

上記は収録記録の時点で未実施だった課題です。収録結果から、1SB-LSDの全加水分解、主要代謝経路、Bz/SBの障壁差を結論しません。

## 収録ファイルの範囲

[MANIFEST.json](MANIFEST.json) に選択した41ファイルの原本位置とハッシュを記録しています。採用NEB・端点Opt・IRC・継続・終点Optの入力、入力が参照する座標・Hessian、選択出力と座標を補いました。計算ソフトウェア本体、波動関数、全失敗attempt、全xTB scanを含む完全アーカイブではありません。ローカルパスの接頭部分だけを伏せ、相対位置を保持しています。
