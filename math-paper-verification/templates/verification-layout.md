# 新規プロジェクト向け推奨構成

既存の形式を優先し，必要なファイルだけ使う．

```text
verification/
  verification.sty      # LaTeXの場合．Skillのassetsからコピー
  verification.tex      # LaTeXの場合．card群と中央TODO/Suggestions/Open problems
  to_verify.md          # 未着手候補のinbox
  index.md              # 主要定理の検証範囲・結果とcardへの対応
  notation.md           # 必要な場合だけ記号一覧
  cards/
    E-semantic-title.md # または .tex．既存のcard IDは変えない
```

## to_verify.md の最小形

```markdown
# Active candidates
- candidate: ...
  target: label in file.tex @ version，範囲
  what: V1 / V2 / V3 / V4 / V5 （判明したものだけ，複数可）
  issue: ...
  reason: 記録する価値・優先度
  next check: 方法と次の確認（予定）
  status: candidate

# Resolved candidates
- YYYY-MM-DD: ... → card-created / recorded / rejected （処理理由，card IDや記録先）
```

候補の処理状態は数学的な確認結果ではない．既存の候補の書式も受け入れる．

## index.md の最小形

```markdown
# 主要定理の検証範囲
| 主定理・版 | 確認対象・範囲（What） | 実施した方法（How） | Result | 根拠・card | 未確認箇所・次の確認 |
| --- | --- | --- | --- | --- | --- |
| thm:main / paper.tex @ abc1234 | V1・V4：引用の一様性条件 | M1：原文の主張と照合 | 部分的に確認済み | cards/E-uniformity.md | パラメータに一様な定数か未確認．証明を調べる |
| thm:main / paper.tex @ abc1234 | V2・V3・V5：残る証明と主結果までの依存 | 未実施 | 未確認 | — | 未着手 |
```

行は対象範囲に合わせてまとめる・分ける．未着手の主要定理も載せる．全補題や全方法の組合せは列挙しない．確認済みはその版・範囲・手段に限定し，詳細な根拠はカード等に一度だけ記す．改訂で根拠が無効になり得る範囲は再検証まで未確認とし，旧版の結果は履歴に保持する．
中央 `TODO list`，`Suggestions`，`Open problems` は既存形式を尊重する．必要なら `verification.tex` の通常のsectionまたはMarkdownの見出しで作る．
