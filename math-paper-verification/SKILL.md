---
name: math-paper-verification
description: 数学論文やMaster Expositionの定理・証明を検証し，再確認可能な証拠をVerification Notesのevidence cardとして記録・更新する．外部引用，内部依存，計算，仮定，反例，sanity check，原稿改訂時の再確認に使用する．
---

# 数学論文のVerification Notes

## 目的・優先順位

数学論文の正しさに関する**再確認コストの高い根拠・依存関係・未確認事項**を監査可能な記録として残す．Verification Notesは本文の再執筆でも，数学的正しさの認証書でもない．AIによる確認を証拠として扱わない．

作業に入る前に，必ず `references/verification_rules.md` と `references/CARD-SPEC.md` を読む．項目，分類，禁止事項，更新規則はこれらに従う．競合するときは最新の `CARD-SPEC.md` にある `to_verify.md` の候補管理を採用する．

## 対象と境界

- 対象はユーザーが指定した原稿と関連資料．Master Exposition，投稿論文，過去のverification filesのどれが基準かを明示する．自動的に同一視しない．
- 執筆・英語推敲・expository refactorは別のSkillの役割．ここでは文章改善だけの問題を `SUGGEST` に記録し，correctness evidence cardを作らない．
- 研究上の一般化は `Open problems`，現在の主張の正しさに関わる未解決問題は `TODO` と区別する．
- 特定プロジェクトに存在する構成規則があれば尊重する．`references/master-exposition-example.md` は個別プロジェクトの**例**であり，記載されたメインファイル名やディレクトリ名を他の論文に強制しない．

## 作業手順

1. **対象を特定する**：主張・証明のlabel，参照する原稿ファイルと版・commit，必要なら外部文献の実際に入手した版を特定する．既存の `verification/` と `cards/` を確認し，重複カードを作らない．
2. **リスクを抽出する**：C1 外部文献，C2 内部依存，C3 局所計算，C4 仮定・主張範囲・反例，C5 独立sanity checkを検討する．量化子，一様性，計算可能性，定数依存，極限交換，境界ケースを重点化する．
3. **候補を仕分ける**：まだ証拠を作っていない重要な候補は `verification/to_verify.md` に `TO VERIFY` として登録できる． `Active candidates` と `Resolved candidates`，statusと処理理由を維持する．候補だけで「検証済み」と言わない．単純・自明な箇所をカード化しない．
4. **証拠を調べる**：証明の欠けた操作を根拠付きで展開する．引用は原文，記号対応，必要な結論との差を比較する．必要に応じて小さい例，反例探索，独立な計算を行い，実行した範囲・パラメータを残す．失敗，未入手，未確認を区別する．
5. **カードを作成・更新する**：原則card 1枚=1ファイル．IDは意味に基づく恒久名でsection番号を含めない．`Target`，原稿から**逐語コピー**した `Paper lines`，日付入りで発見内容を書く `Log` は必須．C1/C2は `Locator`，逐語の `Source text`，`Gap` が必須．C3は原則 `Expanded step` を記す．必要な任意欄だけ追加する．
6. **中央ファイルを同期する**：`index.md` の target label→card ID対応，必要なら `notation.md`，中央 `TODO list`，`Suggestions`，`Open problems`を更新する．`Not settled` は中央TODOと同期する．候補を処理したら `to_verify.md` を更新する．
7. **改訂に追随する**：保存した `Paper lines` と現行の原稿本文を比較する．差異があれば該当カード・依存先のみ再確認し，`Log` に変更と得られた知見を残す．節移動でcard IDは変えない．原稿から削除された結果でも再利用価値のある証拠は保存する．
8. **報告する**：新規・更新card，確認した根拠，未解決TODO，未入手資料，実施したtests，変更したファイルを短く報告する．「検証済み」という総括だけで済ませない．

## 不可欠な制約

- 原稿から読んでいない `Paper lines` や文献から読んでいない `Source text` を生成しない．原文がなければ `[TO FILL]` と記す．
- 頁，定理番号，DOI，版，commitを捏造・推測しない．参照できなければ未確認とする．
- 計算，コード，数値実験，探索を実行していないのに実行済みと記載しない．反例が出ないことを証明と呼ばない．
- 未導出のステップを導出済みとしない．間違いの可能性と確定した反例を区別する．
- **正しさに問題を見つけたら原稿側へ修正が必要なことを伝える．** Verification Notesだけ修正して誤った原稿を残さない．ただしユーザーの編集権限・依頼範囲を超えて原稿を黙って変更しない．
- 出典の逐語記載は，作業用の参照原文の範囲に留め，公に再配布する場合の著作権・ライセンスに注意する．

## 出力形式

既存のプロジェクト形式を優先する．新規作成する場合，`templates/verification-layout.md` を参照する．Markdown cardには `templates/card.md` を用いる．LaTeX形式では `assets/verification.sty` の**実在する**マクロだけを用い，`templates/card.tex` を参照する．`verification.sty` に実装されていない中央管理マクロを仮定しない．

ユーザーから対象指定がない場合は，現在のプロジェクト内のMaster Expositionと既存verification filesを探索し，主結果を支える重要箇所から着手する．原稿が利用できない場合はcard内容を創作せず，空のテンプレートのみ準備する．
