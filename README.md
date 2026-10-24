# math-research-skills

数学論文の執筆，証明の検証，文献調査など，数学研究を支援する再利用可能なCodex Skills集．

## 収録スキル

| スキル | 用途 |
| --- | --- |
| [math-paper-writing](math-paper-writing/SKILL.md) | 英語LaTeX原稿の新規執筆・推敲・構成改善．数学的内容と著者の研究方針を尊重しながら，定理・証明の説明，記号，関連研究の記述を整える． |
| [math-paper-verification](math-paper-verification/SKILL.md) | 数学論文の定理・証明の検証とVerification Notesの作成・更新．引用，内部依存，計算，仮定，反例，sanity checkの根拠と未確認事項をevidence cardに記録する． |

執筆・推敲と独立した証明検証は，それぞれのスキルで扱う．Verification Notesは再確認可能な根拠を残すための記録であり，数学的正しさの認証書ではない．

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

各スキルの詳しい手順と出力形式は，リンク先の`SKILL.md`を参照．
