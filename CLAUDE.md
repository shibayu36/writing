# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 記事を書くときの注意点
記事を書くときは必ず @WRITING.md を参照してください。
また書こうとしている記事の内容から、それに似た最近の記事をランダムに数記事ピックアップし、

- 構成を参考にしてください
- 文体をできる限り模倣してください

執筆するときは @WRITING_GUIDELINE.md も参照してください。

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
- タイトルをファイル名にする。`{タイトル}.md`
- フロントマター不要

## textlint実行方法
```bash
# 基本的なlint
npm exec -- textlint [ファイル名]

# 自動修正
npm exec -- textlint --fix [ファイル名]
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
