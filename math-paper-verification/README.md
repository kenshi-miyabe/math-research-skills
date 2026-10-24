# math-paper-verification

数学論文のVerification Notesを作成・更新するCodex Skill．説明と作業指示は日本語．

`SKILL.md` を含むこのディレクトリを `~/.codex/skills/` またはプロジェクトの `.agents/skills/` に配置する．

```text
$math-paper-verification
この論文の主定理を支える内部依存と引用を確認し，verification cardsを作成してください．
```

`references/CARD-SPEC.md` は添付された2つの仕様のうち `to_verify.md` を定義する詳細版を採用．`references/master-exposition-example.md` は特定論文用規則の参考例であり，普遍的な命名規則ではない．

`assets/verification.sty` はユーザー提供版を変更せず収録．
