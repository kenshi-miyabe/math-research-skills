# Verification Notes Rules

## 目的

Verification Notes は，Master Exposition に書かれた数学的内容について，**なぜそれを信頼できるのか**を記録するための監査文書である．

Master Exposition が現在の理解の全体像を表すのに対し，Verification Notes は，そのうち再確認コストの高い箇所について根拠と検証過程を保存する．

Verification Notes は exposition ではない．読みやすい説明よりも，正しさを後から再確認できることを優先する．

## 検証するもの

特に次を確認する．

- 証明中の非自明な計算や省略
- 定理・補題の内部依存と適用条件
- 仮定がどこで必要か
- 量化子，uniformity，effectivity
- 極限操作，定数依存，scale，境界ケース
- 自然な強化や仮定削除に対する反例
- 外部文献の theorem statement と現在必要な主張との対応
- 既知結果への還元
- 必要に応じた symbolic / numerical sanity check
- 独立な方法による cross-check

すべての自明なステップを記録する必要はない．
**後から再確認するのに時間がかかる箇所，壊れやすい接続点，外部依存，重要な計算**を優先する．

## 記録

検証記録には，必要に応じて次を残す．

- 対象となる theorem / lemma / equation
- 検証した claim
- 使用した仮定
- 展開した計算
- 依存する内部結果または外部文献
- source と現在必要な主張との差
- sanity check や反例探索
- 未解決の correctness issue
- 検証によって分かったこと

詳細な card の形式と運用は `CARD-SPEC.md` に従う．

## Master Exposition との関係

Verification Notes は Master Exposition を補助するが，その代わりではない．

- 誤りや仮定不足が見つかった場合は Master Exposition を修正する．
- Verification Notes にだけ訂正を書いて，Master Exposition に古い主張を残さない．
- Master Exposition が更新されたら，影響する verification item だけを再確認する．
- Master Exposition から内容が削除・移動されても，保存価値のある計算，文献照合，反例探索は Verification Notes に残してよい．
- Verification の作業ログを Master Exposition 本文にそのまま移さない．

## 区別

次を混同しない．

- **proof**：数学的証明
- **sanity check**：正しさを別方向から確かめる補助的確認
- **counterexample search**：主張や仮定の境界を探る試行
- **AI verification**：検証支援の一つであり，それ自体は数学的根拠ではない

複数の方法で同じ箇所を確認した場合，その重複には保存価値がある．

## 原則

Verification Notes の目的は，Master Exposition 全体をもう一度書き直すことではない．

**重要で再確認コストの高い箇所について，証拠，依存関係，未確認事項を残し，Master Exposition の更新に追随できるようにする．**
