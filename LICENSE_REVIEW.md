# License Review

## status

v0.1の適用条件を以下に統一しました。本書は対象ファイルのライセンス記載と配布範囲の整理であり、包括的な法的保証ではありません。

## upstream

対象は [jamesondh/chimera-vocal-synth](https://github.com/jamesondh/chimera-vocal-synth)、基準commit `092b16ce12b927d473c884ca2dfae53ce1b995df`。

- [当該commitのLICENSE](https://github.com/jamesondh/chimera-vocal-synth/blob/092b16ce12b927d473c884ca2dfae53ce1b995df/LICENSE)：**MIT License**、`Copyright (c) 2026 Jameson Hodge`。
- [当該commitのREADME](https://github.com/jamesondh/chimera-vocal-synth/blob/092b16ce12b927d473c884ca2dfae53ce1b995df/README.md)：MITであること、同梱のCMUdict・フォントは個別ライセンスであることを記載。
- ローカルの原文に加え、commit固定のGitHub raw LICENSE / READMEも読み取り確認した。原文の著作権表示・許諾文・無保証条項を [licenses/CHIMERA-MIT.txt](licenses/CHIMERA-MIT.txt) に変更せず同梱した。

MIT原文はソフトウェアと付随文書について、使用・複製・変更・公開・配布・販売等を許諾しています。条件は著作権表示と許諾通知をソフトウェアの複製または実質的な部分に含めることです。無保証条項も含め、原文を維持します。元作者による推薦・保証を意味しません。

## distribution_scope

| item | treatment |
|---|---|
| Phase 2C生成の試聴WAV 9点 | そのままコピー。録音サンプルの再配布ではなく、物理モデルによる生成音声 |
| 説明文・投稿文・manifest・プレイリスト | 独自部分をCC0 1.0で提供（公開者が保有する権利の範囲） |
| CHIMERAのソース・CLI・WASM・依存ライブラリbinary | 本セットに含めない |
| CMUdict辞書本体 | 含めない。発音決定に使用した出典として個別通知を同梱 |
| フォント・画像・CSD/TSP等の第三者録音 | 含めない |

CMUdictの [個別ライセンス](https://github.com/jamesondh/chimera-vocal-synth/blob/092b16ce12b927d473c884ca2dfae53ce1b995df/public/data/CMUDICT-LICENSE.txt) は、ソース再配布時に著作権・条件・免責を保持し、binary再配布時は文書等にそれらを掲載する条件です。`Copyright (C) 1993-2015 Carnegie Mellon University` を含む全文を [licenses/CMUDICT-LICENSE.txt](licenses/CMUDICT-LICENSE.txt) に保存しています。辞書を同梱しない今回の通知は保守的な出典表示であり、生成音声へその条件が自動適用されるとの主張ではありません。

元プロジェクトのArchivoはOFL 1.1、AVHersheyはCC0 1.0 / WTFPLの個別通知をローカルで確認しました。フォントを一切含めない本セットの範囲外としています。後にソース・binary・辞書・フォント等を配布対象に追加する場合は、依存物も含め別途ライセンス確認が必要です。

## output_terms

READMEと共通の条件は次のとおりです。

| material | terms |
|---|---|
| CHIMERA由来コード | MIT（元の著作権表示・許諾通知を維持） |
| 独自追加コード | MIT |
| 生成WAV・独自文書・独自メタデータ・プレイリスト | CC0 1.0（公開者が保有する著作権・関連権利の範囲） |
| 第三者由来のライセンス・通知 | 原条件を維持。CC0の対象外 |

CC0は[公式概要](https://creativecommons.org/publicdomain/zero/1.0/)と[公式Legal Code](https://creativecommons.org/publicdomain/zero/1.0/legalcode.en)に従います。公開者の指定に基づき、その保有する著作権・関連権利について、法令上可能な最大限の放棄と、放棄が有効でない場合の補完的許諾を表明します。

**元CHIMERAのMITを音声へ自動適用したものではありません。** 独自追加コードはMITですが、今回コードは配布対象に含めません。CC0は第三者が保有する権利を処分するものではなく、商標・特許の権利も放棄・許諾しません。無保証であり、第三者権利の不存在等を保証しません。元のMIT・CMUdict通知は変更せず、その原条件を維持します。

## claim_review

- 「同一F0」は**同一の目標F0（220 Hz）**と明記する。既定のjitter/driftにより瞬時F0は完全一定ではない。
- 声質差の聴覚評価は**開発者本人による主観評価**。第三者ブラインド試験・統計的な一般化ではない。
- 今回の比較セットはfemale、/ɑ/・/i/・/u/、離散倍率1.00/1.05/1.10の9条件。
- 人間音声の完全再現、日本語TTS完成、未検証の連続倍率の安全性、一般的なキャラクター声質の一貫性を主張しない。
- upstream公式リリースや、元作者・CMUによる承認・推薦と誤認させない。

## publication_gate

本セットの対象は9音声と説明資料です。ライセンス方針は上記のとおり確定しています。後にソース・binary・辞書・フォント等を配布対象へ追加する場合は、その配布物の元の表示と個別条件を別途確認します。
