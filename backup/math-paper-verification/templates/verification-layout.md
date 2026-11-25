# Verification Notesの構成

パスはプロジェクトルートを基準とする．

```text
papers/                  # ダウンロードした論文PDF・ユーザー提供の論文PDF
book-pages/              # ユーザー提供の本の該当ページ
verification/
  verification.sty      # Skillのassetsからコピー
  verification.tex      # templates/verification.texから作成する主ファイル
  to_verify.md          # templates/to_verify.mdから作成．未解決項目のみ
  index.md              # 主要定理の版・範囲・What・How・Resultとcardへの対応
  cards/
    E-semantic-title.tex
```

カードはTeXで書き，追加するたびに `verification.tex` の `\input{cards/<card-ID>.tex}` に登録する．主ファイルにはカード群と，必要なら `Suggestions`・`Open problems` の節を置く．未解決事項の中央管理は `to_verify.md` に一本化し，解決履歴はカードの `Log` に残す．

新規テンプレートは日本語を含むためLuaLaTeXを使う．`verification/` を作業ディレクトリとして次を実行する．

```sh
latexmk -lualatex -interaction=nonstopmode -halt-on-error verification.tex
```

既存プロジェクトではエンジン・クラス・共通マクロを合わせてよいが，主ファイルから全カードを読み込み，単独でコンパイルできる状態を保つ．原稿固有のマクロを必要に応じて共有し，原稿の本文全体を読み込んで代用しない．本文のlabelを文字列で記録する場合と，Notes内のcardへの `\ref` を区別し，未定義参照を残さない．

## index.md の最小形

```markdown
# 主要定理の検証範囲
| 主定理・版 | 確認対象・範囲（What） | 実施した方法（How） | Result | 根拠・card | 未確認箇所・次の確認 |
| --- | --- | --- | --- | --- | --- |
| thm:main / paper.tex @ abc1234 | V1・V4：引用の一様性条件 | M1：原文の主張と照合 | 部分的に確認済み | cards/E-uniformity.tex | パラメータに一様な定数か未確認．証明を調べる |
| thm:main / paper.tex @ abc1234 | V2・V3・V5：残る証明と主結果までの依存 | 未実施 | 未確認 | — | 未着手 |
```

行は対象範囲に合わせてまとめる・分ける．未着手の主要定理も載せる．全補題や全方法の組合せは列挙しない．確認済みはその版・範囲・手段に限定し，詳細な根拠はカード等に一度だけ記す．改訂で根拠が無効になり得る範囲は再検証まで未確認とし，旧版の結果は履歴に保持する．
