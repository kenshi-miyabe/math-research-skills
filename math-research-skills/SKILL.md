---
name: math-research-skills
description: 数学研究の探索，論文・Master Expositionの執筆や推敲，定理・証明の検証，独立した原稿レビューに使う．研究メモ，LaTeX原稿，Verification Notes，Markdownの指摘一覧を依頼に応じて作成・更新する．
---

# 数学研究と論文

対象プロジェクトと依頼された作業を特定し，該当する手順を読む．複数の作業が依頼されたら，指定された順序と各作業の出力先に従う．指示と報告は原則日本語とし，論文本文は依頼に応じた言語で書く．

| 作業 | 選ぶとき | プロジェクト内の出力 |
| --- | --- | --- |
| [explore](explore/workflow.md) | 予想，未解決問題の証明，別証明，反例，主張の変形，類似の概念・証明技術などを探索する | `explore/` に日付またはトピックで保存する研究メモと再現用資料 |
| [write](write/workflow.md) | 本文を書き，全体構造を単純化し，局所的に読みやすくする．`review/todo.md` の読みやすさの指摘を直す | 対象の原稿，または依頼された提案．`backup_memo/` の修正記録 |
| [verify](verify/workflow.md) | `review/todo.md` の数学の指摘を1件ずつ検証する，または指定の主張・証明を検証する | `verification/cards/` のTeXカード．原稿を直した場合は `backup_memo/` の修正記録 |
| [review](review/workflow.md) | 原稿を独立に読み，すぐに確認できない主張と読みやすさの問題を洗い出す | `review/todo.md` に集約した指摘 |

全作業で共有する規則：

- 未解決の指摘・疑義は `review/todo.md` の1か所で管理し，原稿の修正記録は `backup_memo/` に置く．[指摘の管理と修正メモ](references/issues-and-memos.md)
- 用語・記号・参照の統一規則．[用語・記号・参照の統一](references/consistency-and-references.md)
- プロジェクトルートに共通の `papers/` と `books/` を用意し，既存資料を再利用する．[文献の保存と照合](references/source-materials.md)

各作業の出力先は実施時に作成する．
