# 数学論文の執筆・推敲

想定読者が，何を示すか，なぜ正しいか，なぜ重要かを適切な労力で理解できる原稿にする．すべての文・補題にこの説明を加える必要はない．

## 二つの仕事

- **全体構造を単純化する．** 各章の節が増えすぎないようにし，各節で何を示すか，章の目的にどうつながるかを明確にする．同じ目的の話題は一つの節にまとめ，必要に応じて `\subsection` などで整理する．[構成と読者負担](references/exposition-refactor.md)
- **局所的に読みやすくする．** 議論の冒頭に目的を書き，参照する箇所に `\label` を付ける．文献を引用するときは著者名を本文に出し，指示語は具体的な対象名や記号に置き換える．[説明と根拠](references/exposition-message.md)，[用語・記号・参照の統一](../references/consistency-and-references.md)，[出典・引用・先行研究](references/related-work-and-audience.md)

## 優先すること

- 定義・仮定・量化子・結論・論理的依存を保つ．数学的内容の変更は文章修正と分け，著者の意図や未確認の事実を推測で補わない．
- 主結果・核心・補助的な議論を区別し，著者の研究方針を尊重する．短縮・説明追加そのものを目的としない．
- 出典と非自明な主張の根拠を追えるようにする．読んでいない文献や未実施の確認を，確認済みとしない．
- 数学的な疑義は正誤を推測で決めず，種別「数学」として `review/todo.md` に追加する．[指摘の管理と修正メモ](../references/issues-and-memos.md)

## 進め方

1. 原稿から編集範囲・主結果・想定読者を確認し，依頼された範囲で執筆・編集する．`review/todo.md` の読みやすさの指摘に対応する依頼では，指摘IDごとに1件ずつ処理する．提案のみの依頼では原稿を変更しない．
2. [用語・記号・参照の統一](../references/consistency-and-references.md)を必ず読み，編集前に対象範囲の用語・記号・参照・後続で使う評価を照合する．章をまたぐ整合性は関係する章も確認し，閲覧できない範囲は未確認とする．その他は「二つの仕事」と下記の参照資料から，作業に関係するものを読む．
3. 変更後の文脈と差分を確認し，7項目を再点検する．必要ならビルドする．指摘に対応した場合は，[指摘の管理と修正メモ](../references/issues-and-memos.md)に従って `backup_memo/` に記録し，`review/todo.md` を更新する．主要な変更，数学的内容に触れる提案，未確認事項を簡潔に報告し，原稿を変更した場合は本文・参考文献を含む全差分を示す．

## 必要時の参照

- Abstract・Introduction・Conclusion・意義と成果が開く問いの検討：[references/claims-and-positioning.md](references/claims-and-positioning.md)
- 英語・LaTeX・改稿後の確認：[references/latex-writing.md](references/latex-writing.md)
- 重要な方針が定まらず著者と検討する場合：[references/author-decisions.md](references/author-decisions.md)
- 外部文献を扱う場合：[文献の保存と照合](../references/source-materials.md)
