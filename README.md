# math-research-skills

数学研究の探索，論文執筆，証明検証，独立レビューを支援するCodexスキル．[`$math-research-skills`](math-research-skills/SKILL.md) を呼び出し，依頼する作業を指定する．

## 作業と出力先

| 作業 | 用途 | プロジェクト内の出力 |
| --- | --- | --- |
| [explore](math-research-skills/explore/workflow.md) | 証明・予想・反例，仮定や結論の変更，類似の概念や証明技術などの探索 | `explore/` に日付またはトピックで保存する研究メモ・再現用資料 |
| [write](math-research-skills/write/workflow.md) | 本文の執筆・推敲，全体構造の単純化と局所的な読みやすさの改善，読みやすさの指摘への対応 | 対象の原稿，または依頼された提案．`backup_memo/` の修正記録 |
| [verify](math-research-skills/verify/workflow.md) | 数学の指摘を1件ずつ検証し，定理・証明を検証 | `verification/cards/` のTeXカード．原稿を直した場合は `backup_memo/` の修正記録 |
| [review](math-research-skills/review/workflow.md) | 原稿を独立に読み，すぐに確認できない主張と読みやすさの問題を洗い出す | `review/todo.md` に集約した指摘 |

未解決の指摘は `review/todo.md`（ID `R-NNN`）の1か所で管理し，原稿の修正記録は `backup_memo/` に置く．引用文献は全作業で共有し，論文を `papers/`，書籍・抜粋を `books/` に置く．各ディレクトリは対象の研究プロジェクトに作成する．

## 配置方法

`math-research-skills/` を，`SKILL.md` と配下の手順・参照資料・テンプレートを含めて，個人用の `~/.codex/skills/` またはプロジェクト用の `.agents/skills/` に配置する．旧版を配置済みの場合は，旧3スキルのディレクトリをスキルの検索対象から外し，このディレクトリに切り替える．リポジトリの旧版と作業記録は `backup/` に保管している．

## 使用例

| 作業 | `$math-research-skills` に続けて指定する依頼 |
| --- | --- |
| explore | 主定理の仮定を弱められるか，境界例と反例候補を調べて `explore/` に記録してください． |
| write | `paper.tex` のIntroductionを推敲し，主結果の意義と関連研究との関係が伝わるようにしてください． |
| verify | `review/todo.md` の数学の指摘を1件ずつ検証し，根拠をTeXカードに残してください． |
| write | `review/todo.md` の読みやすさの指摘を1件ずつ直し，修正メモを残してください． |
| review | `paper.tex` を独立に読み，すぐに確認できない主張と読みやすさの問題を，版と箇所を付けて `review/todo.md` に記録してください． |

## 参考にしたリポジトリ

以下のリポジトリの設計を参考にしている．

- [frenzymath/Danus](https://github.com/frenzymath/Danus)
- [gyf9712/stat-theory-skills](https://github.com/gyf9712/stat-theory-skills)
- [gyf9712/stat-writing-skills](https://github.com/gyf9712/stat-writing-skills)
- [haruhisa-enomoto/math-paper-skills](https://github.com/haruhisa-enomoto/math-paper-skills)

専用の実行基盤・外部スクリプトを導入せず，本リポジトリの運用向けに記述している．

## 参考文献

- Bjorn Poonen, [Practical Suggestions for Mathematical Writing](https://math.mit.edu/~poonen/papers/writing.pdf)，2026年1月6日付．
