# 予備比較の実装記録

## 変更したソースファイル

以下は、元の解析を実装した時点の記録です。機能の追加履歴を示すもので、molecule2fbxの開発動機を説明するものではありません。

- `molecule2fbx/structures.py`
  - 全重原子・共通骨格・反応中心の原子集合を追加した。
  - Bz/TMS-Bz間の原子対応を、分子グラフに基づいて一定の手順で決める処理を追加した。
  - 入力原子の識別を保ち、対称原子を自動で入れ替えない。

- `molecule2fbx/ensemble.py`
  - Freqがない場合は `imaginary_modes: null` を出力する。
  - Freqの選択数・完了数・利用可能数・再利用数を分ける。
  - 最終的なDFT計算の失敗と、再開時の復旧履歴を分ける。
  - Opt/Freqと配座候補集合の由来を記録する。
  - 共通骨格と反応中心のRMSD情報も出力する。

- `molecule2fbx/pipeline.py` と `molecule2fbx/quantum/reuse.py`
  - 新規計算、ローカルでの再開、外部結果の再利用を区別する。
  - 過去の再利用結果に、現在の候補集合の力場情報を割り当てない。

- `molecule2fbx/comparison.py`
  - 保存済み配座集合の情報を、一度だけバックアップしてから修正する。
  - 保存済みORCA出力から、電子分布、Mayer結合次数、双極子、軌道、Freq、Hessian、熱化学量を読み出す。
  - カルボニルを中心とする方向別の立体アクセスを計算する。
  - 配座集合の内部と、異なる集合間のRMSDを計算する。
  - 全代表構造の重み、共通骨格の重複を除いた重み、Freq/Gibbsがある部分集合だけの重みを区別する。
  - JSON、CSV、英語の要約、日本語の考察を出力する。

- `tests/test_comparison.py`
  - TMSの除外、TMSだけの動き、Bz/SBの原子対応、立体指標、ORCA物性の読込、Freqがnullとなる場合の意味、由来と失敗履歴の区別、共通骨格の重複を除いた重み付けをテストする。

- `README.md`
  - RMSDの原子対応、対称性の仮定、重み付けの範囲、解析の再生成方法を記載した。

## 解析を実行するスクリプト

次のコマンドは元の作業環境で使ったものです。

```powershell
work\test-venv\Scripts\python.exe work\analyze_bz_sb_preliminary.py
work\test-venv\Scripts\python.exe work\run_sb_pool_xtb.py
work\test-venv\Scripts\python.exe work\run_low_energy_properties.py
```

`work/run_sb_pool_singlepoints.py` は、選択から漏れたSBの二つの配座領域を確認する条件付きの追加処理です。GFN2-xTBの予備探索で必要と判断された場合にだけ実行する方針でした。

## テストの状態

当時のテスト出力は次のとおりです。

```text
69 passed
```

これらの変更では、既存のOpt結果を上書き・削除していません。新しいFreq、xTB、物性計算の結果は別のフォルダへ保存しています。過去の未完了の起動試行も保存され、復旧できる状態にあります。
