# 新規プロジェクト向け推奨構成

```text
verification/
  verification.sty      # LaTeXを使う場合．Skillのassetsからコピー
  verification.tex      # card群と中央TODO/Suggestions/Open problemsを束ねる
  to_verify.md          # 未着手候補のinbox
  index.md              # manuscript label → card ID
  notation.md           # 必要に応じた記号一覧
  cards/
    C-semantic-title.tex
```

## to_verify.md の最小形

```markdown
# Active candidates
- candidate: ...
  target: ...
  category: C1 / C2 / C3 / C4 / C5
  issue: ...
  reason: ...
  next check: ...
  status: candidate

# Resolved candidates
- YYYY-MM-DD: ... → card-created / rejected （理由，card ID）
```

中央 `TODO list`，`Suggestions`，`Open problems` は既存フォーマットを尊重し，存在しなければ `verification.tex` の通常のsectionとして作る．
