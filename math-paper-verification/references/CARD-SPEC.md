# Verification Card Specification

数学論文の verification notes を，AI を利用した**検証履歴**として残すための運用規約．
本ファイルは `verification_rules.md` の理念を具体化する実務仕様である．

- `verification_rules.md`：Verification Notes の目的・原則
- `CARD-SPEC.md`：何を card 化し，何を記録し，どう運用するか

Verification notes は正しさの認証書ではない．AI verification は人間の精読を代替しない．
目的は，誤り，暗黙の仮定，不自然な依存，量化・定数・スケールの問題を発見し，
後から人間が再確認できる証拠を残すことである．

---

## 1. Verification の二層

Verification は次の二つを分離する．

### 1.1 Correctness verification

数学的正しさに関わる確認．必要な場合に **evidence card** を作る．

#### C1. 外部文献・既知結果
外部の定理・既知結果との接続を確認する．

主な対象：
- 引用元の仮定と実際の使用条件の一致
- notation / parameter の対応
- uniformity，effectivity，parameter dependence
- citation consistency
- 現在の結果が既知結果へ還元できるか
- 還元できない場合，最初に破綻する条件は何か

基本比較：
\[
\text{source statement}
\longrightarrow
\text{notation / parameter map}
\longrightarrow
\text{statement needed here}.
\]

#### C2. 内部依存関係・適用条件
論文内部の theorem / lemma / proposition の接続を確認する．

主な対象：
- 適用条件が本当に成立しているか
- statement より強い形で使っていないか
- uniformity，effectivity，parameter dependence の追加要求
- parameter の読み替え
- 循環依存
- 証明順序と論理的依存順序のずれ

単なる字義通りの適用には原則 card を作らない．

#### C3. 局所的な数理操作
省略された計算・推論・記号操作を展開して確認する．

主な対象：
- `clearly`, `hence`, `it follows`, `routine computation`
- 不等式の向き
- \(\sup/\inf\)，\(\limsup/\liminf\)
- 量化子の順序
- 極限と \(\sup,\inf\) の交換
- index / scale shift
- 定数，係数，正規化，対数の底
- notation の取り違え

必要なら subtype として
`calculation / order / quantifier / limit / constant / scale / notation`
を記録する．

#### C4. 仮定・主張範囲・反例
定理が成立する領域の境界を確認する．

主な対象：
- 各仮定をどこで使うか
- 仮定を落とすと何が壊れるか
- 退化例・境界例
- theorem statement 自体への反例探索
- 自然な強化・量化子交換・conclusion 強化への反例探索
- 仮定が不要に強くないか
- statement が必要以上に強くないか

反例が見つからないことは証明ではない．探索範囲と方法を記録する．

#### C5. 独立 sanity check
本文の証明を追うのではなく，別方向から結論を確認する．

主な対象：
- trivial / finite / extremal case
- 具体例での直接計算
- 小さな有限モデルの全探索
- 数値実験
- 別表現による再計算
- 二つの独立な計算方法
- 既知の特殊ケースへの還元
- 本文と異なる原理による独立証明

C4 は壊す方向の stress test，C5 は別方向からの cross-check である．

### 1.2 Expository verification

数学的正しさではなく，読者が自然に理解できるかを確認する．
原則として card は作らず，中央 `Suggestions` に `SUGGEST` として残す．

- **E1 Proof structure**：より短い／概念的な証明，補題化，重複する proof pattern
- **E2 Roadmap**：証明前に目的・障害・方針・段階が見えるか
- **E3 Granularity**：記号過多，細分化しすぎ，省略しすぎ，reader load
- **E4 Consistency**：用語・notation・粒度・定理配置の一貫性
- **E5 Examples**：例，特殊ケース，failure example が理解を助けるか

Expository verification 中に correctness の疑義が生じた場合は C1--C5 に昇格する．
Correctness verification 中に説明改善を見つけた場合は card と分離して `SUGGEST` に置く．

---

## 2. 何を card 化するか

### 2.1 Card を作る場合

次のいずれかに当たる correctness issue だけを card 化する．

- 再確認に実質的な時間がかかる
- 複数の条件・結果を接続する
- 省略計算を再度追う価値がある
- 外部文献との対応を保存する価値がある
- 仮定・反例・独立確認など再利用可能な証拠が得られた
- 将来の改訂で壊れやすい接続点である

### 2.2 Card を作らない場合

- statement の字義通りの単純適用
- 数秒で再確認できる trivial step
- correctness に関係しない文章改善
- 単なる感想や研究上のアイデア

原則：
\[
\boxed{\text{C1--C5} \Rightarrow \text{card}}
\qquad
\boxed{\text{E1--E5} \Rightarrow \text{SUGGEST}}
\]

一つの箇所が複数カテゴリに該当しても card は原則1枚とする．

### 2.3 Card 化候補の一時記録

correctness issue を発見したが，まだ card の作成・検証に着手していない場合は，
`verification/to_verify.md` に card 化候補として記録する．
このファイルは verification の **inbox** であり，evidence card そのものではない．
したがって，候補として記録されているだけでは，その主張を確認済みとはみなさない．

候補には最低限，次を記録する．

- 仮の短い題名
- manuscript の target label または該当箇所
- 想定カテゴリ C1--C5
- 疑問・危険箇所・確認したい主張
- card 化する価値があると考える理由
- 次に行う確認
- status：`candidate` / `card-created` / `rejected`

`to_verify.md` には `Active candidates` と `Resolved candidates` を設ける．
card を作成した場合は，候補を `Resolved candidates` に移し，作成した card ID と
日付を記録する．card 化しないと判断した場合も，理由と日付を記録する．
expository issue だと判明した場合は中央 `Suggestions` へ，現在の correctness を
妨げない研究課題なら中央 `Open problems` へ移す．

候補段階では `Paper lines` や `Source text` を完全に埋める必要はない．
ただし card を実際に作成するときは，本仕様の標準欄と禁止事項をすべて適用する．

---

## 3. Card の標準欄

欄は必要なものだけを書く．内容がなければ欄ごと省略する．

### 3.1 `Target` — 必須

論文側の label を原則1個指定する．
card ID は論文内の位置ではなく数学的内容に基づく恒久名とする．

例：
`C-measure-to-machine`

section 番号や appendix 番号を ID に含めない．

### 3.2 `Paper lines` — 必須

card が依拠する論文本文を **verbatim** でコピーする．

- 言い換え禁止
- 要約禁止
- 記号統一禁止
- 必要最小限，通常 2--6 行
- 式番号・label が重要なら含める

目的は，論文改訂時に card が古くなったかを短時間で判定できるようにすること．

### 3.3 `Expanded step` — C3 では原則必須

本文で省略された部分だけを，目視で追える粒度まで展開する．

- 各行の根拠を示す
- 定数・係数を可能な限り保持する
- 意味不明な `O(1)` を残さない
- 長い場合は (a), (b), (c) に分ける

C4 では反例探索の論理，C5 では独立証明をここに書いてよい．

### 3.4 `Where the hypotheses are used` — C2/C4 で必要に応じて

各仮定について，どこで使用するかを書く．

例：
- 仮定 \(A\) は step (c) の compactness にのみ使用
- 仮定 \(B\) は不等式には不要で，effectivity のためだけに必要

弱めた場合に何が壊れるかも，分かる範囲で記録する．

### 3.5 `Locator` — C1/C2 で必須

C1：
- 著者
- 論文・書籍名
- 掲載情報
- 頁・定理番号
- DOI または arXiv 番号
- 実際に参照した版

C2：
- 被参照 label
- 参照した manuscript の版（日付または commit）

**分からない情報を推測しない．**

### 3.6 `Source text` — C1/C2 で必須

依拠する外部文献または論文内別 label の statement を verbatim で記録する．

原文が手元にない場合：
`[TO FILL]`

そのうえで，「原文から何を確認する必要があるか」だけを書く．

AI は，実際に原文が与えられていない `Source text` を生成してはならない．

### 3.7 `Notation map` — C1 で任意

原文の記号と現在の論文の記号の対応だけを書く．
論文内部の一般的 notation list は別ファイルで管理する．

### 3.8 `Gap` — C1/C2 で必須

「source が与えるもの」と「現在必要なもの」の差を書く．

差がなければ：
> 差なし．原文の主張をそのまま適用できる．

差がある場合：
- 何が不足しているか
- 追加議論で埋まるか
- 埋まらないなら最初の障害は何か

を記録する．

### 3.9 `Tests` — 任意，重要箇所では推奨

まず手で追える単純な例を優先する．

例：
- 一点集合
- 有限集合
- 一様測度
- Dirac 測度
- 最小の非自明な有限構造
- boundary / extremal case

数値実験を行った場合は，
- parameter
- precision
- random seed
- 理論上の期待
- 実測結果

を記録する．

実行していない計算を実施済みとして書かない．

C3 で向き・順序が本質的なら，可能なら一つを入れ替えると壊れる例を作る．
C4 の反例探索では探索範囲を残す．
C5 では本文と独立な方法で同じ結論になるかを見る．

### 3.10 `Not settled` — 任意

**現在の correctness verification を完了するために未確認な事項**だけを書く．

説明改善や研究上の一般化は含めない．

ここに項目を追加した場合，中央 `TODO list` にも同じ項目を置く．
解決したら両方から削除し，解決内容を `Log` に残す．

### 3.11 `Open problems` — 任意

現在の correctness を妨げない研究課題を書く．

例：
- 一般化
- 必要十分条件
- 仮定の弱化
- characterization
- 別モデルへの拡張

関連 card と中央 `Open problems` の双方から追跡できるようにする．

### 3.12 `Log` — 必須

日付つきで **何を発見したか** を書く．

悪い例：
> 2026-09-01 確認した．

良い例：
> 2026-09-01 step (b) を展開し，必要な最小定数が \(n-1\) であることを確認．本文では定数未指定．

### 3.13 `Dependencies` — 改訂の影響を追う場合

依拠する内部結果の label，関連 card ID，必要な外部文献の Locator を記す．
card がない単純な適用のために新規 card を作る必要はない．
前提として使う結果と，比較・参考のためだけに挙げる結果を区別する．
仮定付きの結果を引用しても，その仮定が現在の対象で成立することまでは示せない．
依存先の未確認事項を，引用するだけで解決済みとして扱わない．

### 3.14 `Interface check` — C1/C2 の接続が複雑な場合

既存の `Notation map`，`Where the hypotheses are used`，`Gap` だけでは
接続条件を見渡しにくい場合に用いる．同じ内容を重複して書く必要はない．

| 適用先が要求する条件 | 引用元が与えるもの | 現在の対象での照合・根拠 | 未確認事項 |
| --- | --- | --- | --- |
| 必要な仮定・量化・一様性など | 対応する結論とその成立条件 | label・導出・定義の対応 | 残る確認，なければ「なし」 |

同じ用語でも定義が一致するとは限らない．必要な箇所では定義式と量化子まで比較する．
対象の存在と，その対象が必要な性質を満たすことを別々に確認する．
未確認事項は `Not settled` と中央 `TODO list` から追跡できるようにする．

---

## 4. 中央マーカー

Verification 全体では次の5種類を区別する．

### `TO VERIFY`
card 化候補だが，まだ correctness verification と evidence card の作成を
完了していない項目．`verification/to_verify.md` で管理する．
`TODO` や確認済みの証拠を意味しない．

### `TODO`
Correctness に関係し，著者による判断・修正・確認が必要．
card の `Not settled` と中央 `TODO list` を同期する．

### `TO FILL`
必要な証拠がまだ手元にない．
典型例は外部文献の `Source text`，Locator の頁・版など．

### `SUGGEST`
Correctness には直接影響しない説明・構成・notation・例などの改善案．
card に入れず，中央 `Suggestions` に置く．

### `Open problems`
現在の正しさを妨げない一般化・拡張・特徴付け問題．
`TODO` と混同しない．

---

## 5. AI による作成時の禁止事項

以下は厳守する．

1. 原文を与えられていない `Source text` を生成しない．
2. Locator の頁・DOI・版・定理番号を推測しない．
3. 論文にない文言を `Paper lines` に書かない．
4. 実行していない数値実験の結果を書かない．
5. 導出できていない step を補完したふりをしない．`Not settled` に送る．
6. AI が確認したこと自体を数学的証拠とみなさない．
7. `Verified` というラベルだけで検証済み扱いにしない．証拠を書く．
8. Expository issue だけの card を作らない．

AI が生成した card は，人間が少なくとも
`Paper lines`，`Source text`，主要な `Expanded step`，実行結果
を確認してから採用する．

---

## 6. 最小出力フォーマット

Markdown で作る場合の標準形：

```markdown
## C-semantic-title / target-label

### Paper lines
```tex
... verbatim ...
```

### Expanded step
...

### Where the hypotheses are used
...

### Locator
...

### Source text
> [TO FILL] ...

### Notation map
...

### Gap
...

### Tests
...

### Not settled
- ...

### Open problems
- ...

### Log
- YYYY-MM-DD ...
```

不要な任意欄は省略する．

正式な LaTeX 版では `verification/verification.sty` の対応マクロを用いてよい．
マクロ仕様自体は verification の数学的規約ではなく実装仕様なので，
必要なら別途 `VNOTES-FORMAT.md` に分離する．

---

## 7. 運用規則

### 7.1 ファイル

原則として card 1枚 = 1ファイルとする．

例：

```text
verification/
  verification.sty
  verification.tex
  to_verify.md
  cards/
    C-cutler-weak-duality.tex
    C-measure-to-machine.tex
  index.md
  notation.md
```

- `index.md`：manuscript label → card ID
- `notation.md`：論文全体の記号一覧
- `to_verify.md`：card 化候補の inbox と disposition の記録
- `verification.tex`：card と中央 TODO / Suggestions / Open problems を束ねる

### 7.2 Card 化候補の処理

新しい correctness issue が見つかったら，直ちに大きな card を作るのではなく，
まず `to_verify.md` に候補として記録してよい．その後，次のいずれかに分類する．

1. card 化する：`cards/` に card を作り，`index.md` と必要な中央 TODO を更新する．
2. 既存 card に統合する：既存 card の該当欄と `Log` を更新する．
3. `SUGGEST` に移す：correctness ではなく exposition の問題だった場合．
4. `Open problems` に移す：現在の正しさを妨げない研究課題だった場合．
5. 棄却する：trivial，重複，対象外などの理由を残す．

処理後は `Resolved candidates` に日付，結論，関連 card ID または移動先を記録する．
`to_verify.md` の候補を card の代用として長期間放置しない．

### 7.3 改訂時

論文を改訂したら，関連する `Paper lines` を現在の本文と比較する．
一致しなければ card の該当部分を再確認する．

`Paper lines` が一致していても，依存する補題・定義・外部文献の版が変われば
確認の根拠は古くなりうる．`Dependencies` と本文の参照をたどり，
影響する card とその下流を再確認の対象にする．依存記録は網羅的とは限らないので，
記録にないことだけを理由に影響なしと判断しない．

影響する根拠が未確認の間は，中央 `TODO list` に変更元と対象 card を記し，
各 card の `Not settled` と同期する．再確認の結果と使用した版を `Log` に残す．
依存元の誤りが判明しても，下流の結論まで偽と確定するわけではない．
使えなくなった証明・根拠と，反例で否定された主張を区別する．
代替の根拠で影響なしと確認できた箇所は，理由を残して再確認の対象から外す．

結果が別 section に移動しても card ID は変えない．

### 7.4 削除された結果

論文から結果が削除されても，有用な計算・文献照合・反例探索を含む card は原則残す．
削除日と理由を `Log` に記録する．

### 7.5 Master Text との関係

Verification Notes は Master Text / Paper の誤りを修正するための監査記録である．
問題が見つかった場合，verification 側だけに訂正を残して本文を放置しない．

一方，Verification Notes に含まれる作業ログ・AI利用履歴・反例探索履歴を
Master Text 本文にそのまま移さない．

### 7.6 失敗した方針と反例探索

再試行を避ける価値がある失敗は，関連 card の `Log` に，試した方針，
使用した仮定，最初に進めなくなった箇所，具体的な障害，再検討する条件を残す．
複数の card にまたがる場合だけ，中央に短い一覧を置き，詳細は card を参照する．

「この方法では示せない」「主張が反例で否定された」「探索が不十分」を区別する．
反例の場合は仮定がすべて成立することと，結論が破れることを示す．
反例が見つからない場合は探索範囲と限界を `Tests` に残し，証明の代わりにしない．
失敗が現在の証明に穴を残すなら `Not settled` / `TODO`，
現在の正しさを妨げない別方針なら `Log` または `Open problems` で扱う．
失敗の記録だけを目的に，自明な試行を card 化しない．

---

## 8. Card 完了時の短い自己点検

毎回すべての詳細チェックを機械的に行う必要はない．最低限，次だけ確認する．

- [ ] correctness issue であり，card 化する価値があるか
- [ ] `Paper lines` は verbatim か
- [ ] C1/C2 なら `Source text` と `Gap` があるか
- [ ] 省略計算は再確認できる粒度まで展開したか
- [ ] 仮定・量化・定数・scale の危険箇所を確認したか
- [ ] 実施していない test を実施済みと書いていないか
- [ ] `Not settled` と `Open problems` を混同していないか
- [ ] 説明改善は `SUGGEST` に分離したか
- [ ] `Log` に「何を発見したか」が残っているか

---

## 9. 設計原則

この規約の目的は card を増やすことではない．

良い card は，
- 後から短時間で再確認できる
- manuscript のどの主張を支えているか明確
- source と manuscript の差が明確
- 未確認事項が明確
- 改訂で壊れた箇所だけを再検証できる

ものである．

Verification Notes は「全部を再証明した巨大な副論文」ではなく，
**再確認コストの高い箇所について，証拠と監査履歴を残す局所的なインフラ**
として運用する．

## 参考にした設計

接続条件の表，依存関係に沿った再確認，失敗の再利用は，Danus の
[elaboration](https://github.com/frenzymath/Danus/blob/6d92e8d415933ca2ef52fd1a4da73fdfcd418f1c/.agents/skills/elaboration/SKILL.md)，
[fact graph](https://github.com/frenzymath/Danus/blob/6d92e8d415933ca2ef52fd1a4da73fdfcd418f1c/danus/core/factgraph.py)，
[identify-key-failures](https://github.com/frenzymath/Danus/blob/6d92e8d415933ca2ef52fd1a4da73fdfcd418f1c/agents/skills/worker/identify-key-failures/SKILL.md)
の設計を参考に，本仕様の evidence card 運用に合わせて記述した．
Danus の専用ツールや verifier による正しさの認定は前提としない．
