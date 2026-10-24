# math-research-skills

数学論文の執筆，証明の検証，読者レビューを支援する再利用可能なCodex Skills集．

## 収録スキル

| スキル | 用途 |
| --- | --- |
| [math-paper-writing](math-paper-writing/SKILL.md) | 英語LaTeX原稿の新規執筆・推敲・構成改善．数学的内容と著者の研究方針を尊重しながら，定理・証明の説明，記号，関連研究の記述を整える． |
| [math-paper-verification](math-paper-verification/SKILL.md) | 数学論文の定理・証明の検証とVerification Notesの作成・更新．引用，内部依存，計算，仮定，反例，sanity checkの根拠と未確認事項をevidence cardに記録する． |
| [math-paper-review](math-paper-review/SKILL.md) | 原稿を編集せず，独立した初読・全体の編集レビュー・修正箇所の再レビューを行う．読みやすさ，説明の必要性，参照の明確さを点検する． |

執筆・推敲と独立した証明検証は，それぞれのスキルで扱う．Verification Notesは再確認可能な根拠を残すための記録であり，数学的正しさの認証書ではない．

読者レビューは説明の評価であり，証明の正しさの検証とは分ける．初読では新しい文脈の読者に原稿を順番に渡し，未提示の後続部分や執筆履歴を渡さない．

## 配置方法

利用するスキルのディレクトリを，`SKILL.md` と参照資料・テンプレートなどを含めて，次のいずれかに配置する．

- 個人用：`~/.codex/skills/`
- プロジェクト用：プロジェクト内の `.agents/skills/`

## 使用例

### 数学論文の執筆・推敲

```text
$math-paper-writing
paper.texのIntroductionを推敲してください．数学的内容は保ち，主結果の意義と関連研究との関係が伝わるようにしてください．
```

### 定理・証明の検証

```text
$math-paper-verification
paper.texの主定理を支える内部依存と引用を確認し，verification cardsを作成してください．未確認事項はTODOとして記録してください．
```

### 読者としてのレビュー

```text
$math-paper-review
paper.texを近隣分野の数学者向けに，全体の編集レビューをしてください．原稿は編集せず，説明の重複と参照対象の曖昧さを箇所付きで報告してください．
```

各スキルの詳しい手順と出力形式は，リンク先の`SKILL.md`を参照．

## 参考にしたリポジトリ

以下のリポジトリの設計を参考にしている．

- [frenzymath/Danus](https://github.com/frenzymath/Danus)
- [gyf9712/stat-theory-skills](https://github.com/gyf9712/stat-theory-skills)
- [gyf9712/stat-writing-skills](https://github.com/gyf9712/stat-writing-skills)
- [haruhisa-enomoto/math-paper-skills](https://github.com/haruhisa-enomoto/math-paper-skills)

専用の実行基盤・外部スクリプトを導入せず，本リポジトリの運用向けに記述している．

## 参考文献

- Bjorn Poonen, [Practical Suggestions for Mathematical Writing](https://math.mit.edu/~poonen/papers/writing.pdf)，2026年1月6日付．[全65項目との照合記録](docs/poonen-writing-crosswalk.md)は改訂時の作業記録であり，通常のSkill実行では読み込まない．
