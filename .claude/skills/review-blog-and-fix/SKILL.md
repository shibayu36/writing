---
name: review-blog-and-fix
description: ブログ記事を core-message-reviewer / style-reviewer / (技術系記事のみ) tech-accuracy-reviewer で一斉レビューし、各指摘の妥当性を検証して妥当なものだけ反映する
argument-hint: [記事ファイル] [reviewer名]
user-invocable: true
---

以下の手順を順番に実行してください。

## ステップ1: 引数の解釈

$ARGUMENTS を以下のルールで解釈してください：

- 第一引数: レビュー対象の記事ファイルパス
  - 省略時は、今回のセッションで書いた・編集した記事ファイルを対象にする
  - セッション内から対象を特定できない場合はユーザーに確認する
- 第二引数: reviewer名（省略時は対象reviewerを全て並列実行）

### 利用可能なreviewer名

- `core-message-reviewer` - core-message-writingの基準でのコアメッセージのレビュー
- `style-reviewer` - WRITING.md / WRITING_GUIDELINE.mdと過去記事を基準にした構成・文体のレビュー
- `tech-accuracy-reviewer` - 記事中の技術的なやり方が公式推奨に反していないかのレビュー

reviewer名が上記のいずれにも一致しない場合は、エラーとしてユーザーに利用可能なreviewer名を案内してください。

## ステップ2: レビュー実行

- 対象記事を読み、**技術系記事（ツール・コード・設定・コマンドなど何らかの技術的な手順を説明する記事）かどうかを判定**する。
  - 技術系記事の場合: `core-message-reviewer` / `style-reviewer` / `tech-accuracy-reviewer` の3reviewerを起動する
  - 技術系記事でない場合（book/miscなど）: `tech-accuracy-reviewer` を除く `core-message-reviewer` / `style-reviewer` の2reviewerを起動する
- 第二引数でreviewer名が指定されている場合は、上記の技術系判定に関わらずそのreviewerのみを起動する
- 起動対象が複数ある場合は、**同時に並列起動**する。各reviewerには対象記事のファイルパスを渡す

## ステップ3: レビュー修正

すべてのレビューが完了したら、/fix-blog-review-comments スキルを実行して、レビュー指摘に対応してください。
