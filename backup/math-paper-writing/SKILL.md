---
name: math-paper-writing
description: 数学研究論文の英語LaTeX原稿の執筆・推敲・構成改善に使う．定理・証明の説明，章節構成，記号，関連研究の記述を改善する．独立した証明検証は行わない．
---

# 数学論文の執筆・推敲

想定読者が，何を示すか，なぜ正しいか，なぜ重要かを適切な労力で理解できる原稿にする．すべての文・補題にこの説明を加える必要はない．指示と報告は原則日本語，論文本文は依頼に応じた言語で書く．

## 優先すること

- 定義・仮定・量化子・結論・論理的依存を保つ．数学的内容の変更は文章修正と分け，著者の意図や未確認の事実を推測で補わない．
- 主結果・核心・補助的な議論を区別し，著者の研究方針を尊重する．短縮・説明追加そのものを目的としない．
- 出典と非自明な主張の根拠を追えるようにする．読んでいない文献や未実施の確認を，確認済みとしない．
- 数学的な疑義は箇所と未確認事項を報告する．推敲で問題を隠さず，本格的な証明検証は別の作業として扱う．未解決の疑義は恒久IDと対象labelを付け，`verification/to_verify.md` の書式で重複を避けて追記し，報告にも含める（未作成なら報告のみとする）．

## 進め方

1. 原稿から編集範囲・主結果・想定読者を確認し，依頼された範囲で執筆・編集する．提案のみの依頼では原稿を変更しない．
2. `references/consistency-and-references.md` を必ず読み，編集前に対象範囲の用語・記号・参照・後続で使う評価を照合する．章をまたぐ整合性は関係する章も確認し，閲覧できない範囲は未確認とする．その他は関係する下記資料だけを読む．出典・引用の確認は作業の種類と依頼範囲に合わせ，`references/related-work-and-audience.md` に従う．
3. 変更後の文脈と差分を確認し，必読資料の7項目を再点検する．必要ならビルドする．主要な変更，数学的内容に触れる提案，未確認事項を簡潔に報告し，原稿を変更した場合は本文・参考文献を含む全差分を示す．

## 必要時の参照

- 局所的な説明・根拠・曖昧さ：`references/exposition-message.md`
- 構成・重要度・読者負担：`references/exposition-refactor.md`
- 出典・引用・先行研究：`references/related-work-and-audience.md`
- Abstract・Introduction・Conclusion・意義と成果が開く問いの検討：`references/claims-and-positioning.md`
- 英語・LaTeX・改稿後の確認：`references/latex-writing.md`
- 重要な方針が定まらず著者と検討する場合：`references/author-decisions.md`

参考：Bjorn Poonen, [Practical Suggestions for Mathematical Writing](https://math.mit.edu/~poonen/papers/writing.pdf)，2026年1月6日付．文体上の助言は無条件の禁止規則にしない．

未解決の疑義に外部文献の確認が必要なら，文献ID，著者・論文題名／書名・年／版等の判明している書誌情報，DOI／URL，必要な定理・頁と確認内容も記す．不明な情報は推測で埋めない．論文PDFは `papers/`，ユーザー提供の本の該当ページは `book-pages/` にあるか確認する（独立した読者には初読の範囲制限を優先する）．解決済みの項目は `to_verify.md` に残さず，根拠は関連するTeXカードの `Log` に残す．
