# CHIMERA Voice Identity — Initial Demo v0.1

CHIMERAを利用した声質設計PoCの音響実験成果です。今回の公開対象は9音声と説明資料のみで、独立したキャラクター声質設計ツールの配布ではありません。元プロジェクトの公式リリースではない、非公式の技術デモです。

**CHIMERAの物理声道モデルに、既存bodyから独立した主声道長制御を追加し、同一の目標F0で異なる声質を生成できることを、開発者本人の主観的な聴覚評価で確認しました。** 第三者によるブラインド試験や統計的評価ではありません。

## listen

まず同じ母音を **1.00 → 1.05 → 1.10** の順に聴き比べてください。全9ファイルはPhase 2Cの試聴WAVを無加工でコピーしたものです。

| vowel | 1.00 | 1.05 | 1.10 |
|---|---|---|---|
| /ɑ/ | [01](audio/01_ah_scale_1.00.wav) | [02](audio/02_ah_scale_1.05.wav) | [03](audio/03_ah_scale_1.10.wav) |
| /i/ | [04](audio/04_i_scale_1.00.wav) | [05](audio/05_i_scale_1.05.wav) | [06](audio/06_i_scale_1.10.wav) |
| /u/ | [07](audio/07_u_scale_1.00.wav) | [08](audio/08_u_scale_1.05.wav) | [09](audio/09_u_scale_1.10.wav) |

- [playlist_by_vowel.m3u8](playlist_by_vowel.m3u8)：上記01〜09順。同一母音で倍率の違いを比較。
- [playlist_by_scale.m3u8](playlist_by_scale.m3u8)：01→04→07、02→05→08、03→06→09順。同一倍率で3母音を比較。

プレイリスト対応のローカルプレイヤーで再生できます。Webプレイヤーは実装していません。

## method

追加した `vocal_tract_length_scale` は生成開始時に固定され、咽頭・口腔の**音響的な長さ**だけを同じ倍率で伸ばします。断面積分布、鼻腔・気管の寸法、body、声門設定、調音ジェスチャは維持し、歯の音源位置は伸長後の音響座標に整合させています。頭部の描画形状を拡大する機能ではありません。

条件は **female body × /ɑ/・/i/・/u/ × 1.00・1.05・1.10** の9通り。目標F0は220 Hz、breathinessは0.05、出力48 kHz・内部2倍処理、各3.70秒、mono PCM16です。試聴音声はPhase 2Cで固定ゲインのみを適用し、共通−23 LUFSに調整済み（再測定−23.01〜−22.98 LUFS、クリッピングなし）。本セットでは再合成・再加工していません。

## limitations

- 同じなのは**目標F0**です。既存のjitter/driftが残り、瞬時F0の完全一致ではありません。
- 今回の倍率は離散3点のみ。中間値・短縮を含む未検証の連続範囲の安全性は主張しません。
- 人間の声の完全再現、日本語TTSの完成、声質の一般的な一貫性・品質保証を主張するものではありません。
- 聴覚評価は開発者本人による主観評価です。各試聴者による差の識別や、キャラクター声質としての有用性を保証しません。

## attribution

元プロジェクト：[CHIMERA — jamesondh/chimera-vocal-synth](https://github.com/jamesondh/chimera-vocal-synth)

`Copyright (c) 2026 Jameson Hodge` — MIT License。原文は [licenses/CHIMERA-MIT.txt](licenses/CHIMERA-MIT.txt) に同梱しました。発音決定に利用したCMUdictの通知も [licenses/CMUDICT-LICENSE.txt](licenses/CMUDICT-LICENSE.txt) に保存しています。元作者・CMUによる承認や推薦を意味しません。

基準commitは `092b16ce12b927d473c884ca2dfae53ce1b995df`。音声はその上にローカルのPhase 1・Phase 2B差分を適用した派生実装で生成しました。**元commit単体には追加パラメータはありません。** 本セットは音声・説明資料のみで、エンジン、CLI、修正ソース、辞書本体、フォント、第三者の録音は含みません。条件とSHA-256は [manifest.json](manifest.json) に記録しています。

## license

| material | terms |
|---|---|
| CHIMERA由来コード | MIT（元の著作権表示・許諾通知を維持） |
| 独自追加コード | MIT |
| 生成WAV・独自文書・独自メタデータ・プレイリスト | CC0 1.0（公開者が保有する著作権・関連権利の範囲） |
| 第三者由来のライセンス・通知 | 原条件を維持。CC0の対象外 |

コードは本セットに含めません。音声・独自資料には公開者の指定で[CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/)を適用します。適用範囲・条件は[公式Legal Code](https://creativecommons.org/publicdomain/zero/1.0/legalcode.en)を参照してください。第三者の権利、商標・特許等に新たな許諾を与えるものではありません。

元CHIMERAのMITが生成音声へ自動適用されるという意味ではありません。詳細：[LICENSE_REVIEW.md](LICENSE_REVIEW.md)。
