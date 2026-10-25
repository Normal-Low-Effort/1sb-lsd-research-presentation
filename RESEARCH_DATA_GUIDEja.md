# 公開用データの読み方

本パッケージの目次は [README.md](README.md)、仮説・条件・結果の対応は [METHODS_AND_RESULTS_JA.md](METHODS_AND_RESULTS_JA.md) にあります。

## 三つのデータ群

| 場所 | 内容と対象時点 | 原本との対応 |
| --- | --- | --- |
| `research_results/` | 主に2026年8月23日までの既存の軽量保存データ | [SNAPSHOT_MANIFEST.json](research_results/SNAPSHOT_MANIFEST.json) |
| `supplementary/` | 仮説7の後期探索とDFT感度、runEDDBログ | [MANIFEST.json](supplementary/MANIFEST.json) |
| `h11_evidence/` | 2026年8月25〜26日を含むBz小モデルの選択記録 | [MANIFEST.json](h11_evidence/MANIFEST.json) |

保存データに付属するMarkdownやJSONは、その作成時点の記録を保持しています。たとえば「仮説11はこの保存データには未収録」との記述は `research_results/` 自体の範囲を指し、今回追加した `h11_evidence/` とは区別します。また、manifestの `source_policy` に残る「outputsはGit対象外」という説明は元環境の当時の方針です。完全アーカイブの現在のGit LFS設定を説明するものではありません。

## パスとハッシュ

`${WORKSPACE}` は複製元の研究作業フォルダを表す置換記号です。その後ろの `outputs/...` は原本の相対位置を示しますが、その原本がすべて公開パッケージ内にあるわけではありません。`${USER_PROFILE}` はユーザーのホームフォルダ接頭部分の伏字です。

保存データのmanifestには複製元・保存データの両ハッシュ、追加二群のmanifestには複製元・今回公開するファイルの両ハッシュを記録しています。初回公開時には文献整理 `METABOLIC_INFERENCE_LIMITS_JA.md` 1件の断定表現と履歴注を修正しました。今回の日本語化・推敲による文書の変更も、[PUBLIC_DOCUMENT_EDITS.json](PUBLIC_DOCUMENT_EDITS.json)に旧公開版と修正後のハッシュを記録しています。元の保存データのmanifestは当時の記録として保持しているため、現行のMarkdownを照合するときは文書の変更履歴も参照してください。数値データは変更していません。

保存データの選択XYZ 5件は、Git checkout時のCRLFから、既存manifestと一致するLFへ改行のみ戻しました。座標数値と原子順序は変更していません。

全体の検証には [PACKAGE_FILES_SHA256.txt](PACKAGE_FILES_SHA256.txt) を使います。この一覧は自分自身を除く全公開ファイルを対象とします。

## 集計対象の違い

仮説4・5の元の再解析ではBz/SBとも共通骨格9群、後の最終採用集合に限ったpara置換基系列ではBz 9群／SB 8群です。対象構造・選択履歴が異なるため、同一集合の二つの値として比較しません。構造数や群数を引用するときは、表・JSONと集合定義を一緒に示してください。

各runの `confNNN` はrun内の識別子です。異なる分子の同番号や、旧計算・再生成した候補集合の番号だけで同じ配座とは判断せず、共通骨格の原子対応とRMSDを確認します。電子エネルギーによる重みは、実際の溶液中存在比や完全な自由エネルギー分布ではありません。

## 計算状態の読み方

- `SUCCESS` はその計算段階の処理成功です。化学的な妥当性や研究全体の完了を自動的に保証しません。
- Opt、Freq、TS、IRCは別の確認です。Freq未実施の虚振動数は `null` とし、0個とは扱いません。
- 主配座集合の虚振動数は−20 cm⁻¹の集計閾値を確認してください。小さい負の振動数を含めた全モードの扱いは出力に戻って判断します。
- 仮説11の初回IRCは `PARTIAL`、前方継続は `SUCCESS` です。片方だけを読まず、到達点Optまで追ってください。
- 原データの古い解釈欄より、後の計算記録と更新版の説明を優先します。仮説11のNEB端点とIRC終点の違いは [専用説明](h11_evidence/README.md) に記載しています。
