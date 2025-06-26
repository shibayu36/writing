# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## リポジトリ概要

このリポジトリは「blog.shibayu36.org」（はてなブログ）の記事管理用です。技術記事、読書記録、個人的なノートを日本語で執筆しています。

## ディレクトリ構造

```
writing/
├── shibayu36.hatenablog.com/entry/  # 公開済みブログ記事
│   ├── 2010-2012/                  # 旧形式（タイムスタンプ）  
│   └── YYYY/MM/DD/HHMMSS.md       # 新形式（日付ベース）
├── drafts/                         # 下書き記事
└── WRITING.md                      # 執筆スタイルガイド
```

## 記事フォーマット

### 公開記事の構造
すべての公開記事はYAMLフロントマターを使用：
```yaml
---
Title: [記事タイトル]
Category:
- tech
- book
Date: YYYY-MM-DDTHH:MM:SS+09:00
URL: https://blog.shibayu36.org/entry/YYYY/MM/DD/HHMMSS
EditURL: https://blog.hatena.ne.jp/shiba_yu36/shibayu36.hatenablog.com/atom/entry/[ID]
---
```

### 下書きファイル
- `drafts/`ディレクトリに配置
- フロントマター不要
- 日本語の説明的なファイル名を使用

## textlint設定

### 利用可能な依存関係
- `textlint@11.9.0`
- `textlint-rule-preset-ja-spacing@2.0.2`
- `textlint-rule-preset-ja-technical-writing@4.0.1`
- `textlint-rule-spellcheck-tech-word@5.0.0`

### textlint実行方法
設定ファイルがないため、コマンドラインオプションを使用：
```bash
# 基本的なlint
npx textlint --preset preset-ja-spacing --preset preset-ja-technical-writing --rule spellcheck-tech-word [ファイル名]

# 自動修正
npx textlint --fix --preset preset-ja-spacing --preset preset-ja-technical-writing --rule spellcheck-tech-word [ファイル名]
```

## 執筆スタイル

詳細なスタイルガイドは`WRITING.md`を参照。主要ポイント：
- 過度な敬語を使わないカジュアルで丁寧な文体
- 技術記事の構成：問題提起 → 解決策 → 実装 → まとめ
- 実践的な例とコードサンプルを含める
- 構造化された見出し（主に`###`）を使用
- 謙虚で学習志向の姿勢を維持

## コンテンツカテゴリ

- `tech`: 技術記事・チュートリアル
- `book`: 書評・読書ノート
- `misc`: 個人的な振り返り・雑記

## はてなブログとの同期

このリポジトリはblogsyncなどのツールを使ってはてなブログと同期していると推測されます。フロントマターのEditURLが自動同期を示唆しています。