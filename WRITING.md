# shibayu36ブログの執筆スタイルガイド

このドキュメントは、2024-2025年のブログ記事を分析して抽出した執筆スタイルをまとめたものです。

## 1. 全体的な文体とトーン

### 基本的な文体
- **敬語を使わない丁寧語スタイル**
  - 「〜です」「〜ます」調は基本的に使わない
  - 「〜だ」「〜である」「〜した」という断定形・過去形で統一
  - 例：「最近は〜というやり方で読書をしている。こういう流れだ。」

### 親しみやすさを演出する表現
- **カジュアルな語り口調**
  - 「いやー」「こんな感じで」「〜ですね」など
  - 例：「いやー、YAPC::Hiroshima 2024楽しかったですね」
  - 例：「こんな感じでやりたいことができました」

- **感情表現を素直に入れる**
  - 「とにかく楽しすぎる」「超便利」「良い」など
  - 例：「最近AIによる開発は楽しすぎるが、基礎学習が疎かになりそうで怖い」

### 謙虚で誠実な姿勢
- **完璧ではないことを認める表現**
  - 「間違ってる可能性も高いので、ツッコミあれば教えてください」
  - 「他に良いやり方があれば募集」
  - 「まだまだ人が使えるレベルではないが」

## 2. カテゴリ別の書き方と特徴

### A. 技術記事（最も多い）

**典型的な構成：**

1. **冒頭**：課題・動機の提示
   - 「〜したいなと思い」「〜という問題がある」
   - 例：「自分の推しアバター展示ワールドの写真から写っているワールドへ移動できるといいな〜と思ったのでやってみました。」

2. **本文**：解決策の実装
   - 「### やり方」「### ハマったポイント」などの見出しで構造化
   - コードブロックを多用（```sh、```go、```javascriptなど言語指定）
   - 画像・動画での説明（`[f:id:shiba_yu36:xxxxx]`形式）

3. **締め**：学びや今後の展望
   - 「〜のでメモしておく」（備忘録的）
   - 「今後は〜してみたいと思っている」
   - 例：「このやり方を使えばマスターデータシートの変更に多少強くデータを読み込めて便利である。」

**特徴的な要素：**
- 具体的な実装例は必ず含める
- 参考資料へのリンクを「### 参考」セクションにまとめる
- 脚注で補足説明を追加（`[^1]:`形式）

### B. 読書記録

**典型的な構成：**

1. **冒頭**：読んだ背景や動機
   - 「〜を読んだ」
   - 例：「ユーザーインタビューについて体系的に学びたくて、『ユーザーインタビューのやさしい教科書』を読んだ。」

2. **本文**：内容のまとめと感想
   - 「印象に残った部分は以下のとおり」として箇条書き
   - 他の本との比較を含める
   - 例：「『はじめてのUXリサーチ』のほうがアカデミックで理論的」

3. **締め**：評価と推薦
   - 誰に向いているか明記
   - 例：「データ分析担当になった人はもちろん、エンジニアやPMなどもさっと目を通すと参考になりそうだ。」

4. **付録**：詳細な読書ノート
   - 章ごとのまとめ
   - ⭐️マークで重要度を表現
   - ページ番号付き

### C. イベント参加記録

**典型的な構成：**

1. **冒頭**：全体の感想から開始
   - 感情を素直に表現
   - 例：「いやー、YAPC::Hiroshima 2024楽しかったですね」

2. **本文**：印象的な発表やエピソード
   - 発表者への感謝を含める
   - 具体的な学びを記載
   - 懇親会での交流も記録

3. **締め**：感謝と次回への期待
   - 運営への感謝
   - 「次回も楽しみにしています」

### D. 生活・振り返り系

**典型的な構成：**

1. **冒頭**：現在の状況報告
   - 「今回も進捗状況と学びを共有する」
   - 前回記事へのリンクを列挙

2. **本文**：具体的な活動と学び
   - 「### 現在の様子」で画像付き報告
   - 失敗談も正直に共有
   - 例：「うまくいかなかった理由は〜だった」

3. **締め**：今後の課題
   - 「どこかのタイミングで〜も取り入れたい」

## 3. 定番のフォーマットと表現

### 記事の基本フロー
```
問題提起・動機 → 試行錯誤・実装 → 結果・学び → 今後の展望
```

### よく使うフレーズ集

**冒頭部分：**
- 「〜したいなと思い」
- 「〜という問題がある」
- 「最近〜している」
- 「前やったことあるがブログに書いてなかったのでメモしておく」

**説明部分：**
- 「こういう流れだ」
- 「例えば〜」
- 「そこで〜することにした」
- 「しかし〜だった。原因は〜だった」

**締め部分：**
- 「こんな感じで〜」
- 「〜のでメモしておく」
- 「他に良いやり方があれば募集」
- 「〜について学べて良かった」
- 「今後も続けていこうと思う」

### リンクの記法
- **関連記事**：`[https://blog.shibayu36.org/entry/xxxx:title]`
- **外部サイト**：URLそのまま、または`[タイトル](URL)`
- **書籍**：`[asin:xxxx:detail]`
- **画像**：`[f:id:shiba_yu36:xxxxx]`（`:w300`でサイズ調整可）
- **Twitter**：`<blockquote class="twitter-tweet">`で埋め込み

### 構造化の方法
- 見出しは`###`を基本使用（`##`はほとんど使わない）
- 箇条書きは`-`で統一
- 番号付きリストは`(1)`形式も使用
- コードブロックは必ず言語指定
- 重要な補足は脚注`[^1]:`を活用

## 4. 特徴的なスタイル

### 技術的な内容でも堅くならない
- 専門用語を使いつつも、親しみやすい表現を混ぜる
- 「超便利」「楽しすぎる」など感情表現を恐れない

### 実践重視の姿勢
- 理論だけでなく、必ず実装例や具体例を示す
- 「やってみた」「試してみた」という実験的アプローチ

### 読者との対話的な関係
- 「ツッコミあれば教えてください」
- 「他に良いやり方があれば募集」
- 完成度より共有と議論を重視

## 5. 記事タイプ別テンプレート

### 技術記事テンプレート
```markdown
〜したいなと思ったので、〜してみた。

### 背景・課題
〜という問題がある。例えば〜

### やり方
（具体的な実装方法）

### ハマったポイント
しかし〜だった。原因は〜だった。

### まとめ
こんな感じで〜できた。他に良いやり方があれば募集。

### 参考
- [リンク1](URL)
- [リンク2](URL)
```

### 読書記録テンプレート
```markdown
〜について学びたくて、『書籍名』を読んだ。

[asin:xxxx:detail]

### 読んだ背景
〜

### 印象に残った部分
印象に残った部分は以下のとおり。

- ポイント1
- ポイント2
- ポイント3

### 感想
〜と感じた。〜な人にオススメ。

### 読書ノート
（詳細なメモを別途記載）
```