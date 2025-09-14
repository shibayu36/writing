以下の規則に従って Markdown でプレゼンを作成してください。

# Markdown を用いたプレゼン記述ルール

https://github.com/k1LoW/deck を使ってMarkdownでプレゼンを作成しています。特に指定がない限り、以下に従ってください。

## 基本構造
- 行頭から行末まで、3 つ以上の連続するハイフン（`---`, `----` 等）だけの行でスライドの区切りを示す
- 他の水平線（`- - -`, `***`, `___` 等）はコンテンツ内の視覚的な区切りとして残り、複数の本文プレースホルダを分ける用途に使える
- 各スライド内では、最小の見出しレベルをタイトル、次のレベルをサブタイトルとして扱う。より深い見出しは本文。スライドごとにタイトル見出しは 1 つにするのが推奨

## YAML フロントマター
ファイル先頭に YAML フロントマターを含められます:
```yaml
---
title: "Presentation Title"
presentationID: "presentation_id"
breaks: true
author: "Author Name"
date: "2024-01-01"
tags: ["tag1", "tag2"]
custom:
    nested: "value"
    number: 42
---
```

## 対応する Markdown 構文
スライド本文で使える構文:

### テキスト装飾
- **太字**（`**bold**`）
- *斜体*（`*italic*` または `__italic__`）
- `インラインコード`（<code>\`code\`</code>）
- 複合装飾（例: ***bold and italic***)

### リスト
- 箇条書き（`-` または `*`）
- 番号付き（`1.` または `1)`）
- 適切なインデントで入れ子
- アルファベットリスト（a. b. c.）

### リンクと画像
- リンク（`[Link text](https://example.com)`）
- 山括弧オートリンク（`<https://example.com>`）
- 画像（`![alt text](image.jpg)`）
- PNG/JPEG/GIF をサポート
- ローカルファイルと URL（HTTP/HTTPS）の両方に対応

### ブロック要素
- 引用（`> quoted text`）
- 入れ子の引用
- 言語指定付きコードブロック:
    ```language
    code content
    ```
- Mermaid（言語 `mermaid` のコードブロック）

### テーブル
- GitHub Flavored Markdown（GFM）テーブル
- ヘッダ行は自動で太字
- セル内で太字・斜体・コードなどのインライン装飾可
- 例:
    ```markdown
    | Header 1 | Header 2 | Header 3 |
    |----------|----------|----------|
    | Cell 1   | **Bold** | `code`   |
    | Cell 2   | *Italic* | Normal   |
    ```
- ヘッダ行は自動で太字＋灰色背景
- Google Slides 上でユーザが作成した表は保持される

### HTML 要素
以下のインライン HTML を利用可:
- `<strong>`, `<em>`, `<b>`, `<i>`, `<mark>`, `<small>`
- `<code>`, `<kbd>`, `<cite>`, `<q>`, `<ruby>`, `<rt>`
- `<span>`, `<u>`, `<s>`, `<sub>`, `<sup>`, `<var>`
- `<samp>`, `<data>`, `<dfn>`, `<time>`, `<abbr>`, `<rp>`
- `<br>`（改行）
- カスタムスタイルには `class` 属性を利用

### 改行の扱い
- 既定（`breaks: false`）: ソフト改行はスペースに
- `breaks: true`: ソフト改行を実際の改行に
- 明示的な改行には `<br>` を使用

## ページ設定
HTML コメントをページ設定とスピーカーノートに利用:
- ページ設定: `<!-- {"layout": "title-and-body"} -->`
- 利用可能な設定: `"freeze": true`, `"ignore": true`, `"skip": true`
- スピーカーノート: `<!-- This is a speaker note -->`（設定 JSON とは別コメントに記述）

## 重要な注意
- コメント（`<!-- -->`）に JSON が含まれている場合はページ設定なので、上書きしない
- ページ設定に `"freeze": true` がある場合、そのページの内容は一切変更しない
- スピーカーノートは JSON 設定コメントではなく別コメントに書く
- コードブロックは `--code-block-to-image-command` オプションで画像化可能
