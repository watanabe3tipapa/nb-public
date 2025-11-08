---
title: nb - Usage
---

nb はコマンドラインとローカルウェブのプレーンテキストノートブック、ブックマーク、アーカイブ、知識ベースアプリケーションです。
Git バックエンドのバージョン管理、Pandoc バックエンドの変換、wiki スタイルのリンク、タグ付け、検索、暗号化などを備えています。

## 基本的な使い方

### ノートブックとノート

- **ノートブック**: ノートを整理するためのフォルダ。デフォルトで `home` ノートブックが作成されます。
- **ノート**: Markdown ファイルとして保存されます。

### 基本コマンド

- **ノートを作成**: `nb add "ノート内容"`
- **ノートを編集**: `nb edit ノートID` または `nb edit ノート名`
- **ノートを表示**: `nb show ノートID`
- **ノートを削除**: `nb delete ノートID`
- **ノートをリスト**: `nb ls` または `nb`

### ブックマーク

- **ブックマークを作成**: `nb https://example.com`
- **ブックマークをリスト**: `nb bookmark`
- **ブックマークを開く**: `nb open ブックマークID`

### 検索

- **ノートを検索**: `nb search "キーワード"`
- **ブックマークを検索**: `nb bookmark search "キーワード"`

### ブラウズ

- **ノートをブラウズ**: `nb browse`
- **GUI ブラウザで開く**: `nb browse --gui`

### ノートブック管理

- **ノートブックをリスト**: `nb notebooks`
- **ノートブックを切り替え**: `nb use ノートブック名`
- **新しいノートブックを作成**: `nb notebooks add ノートブック名`

### 設定

- **設定を表示**: `nb settings`
- **エディタを設定**: `nb set editor vim`

### ヘルプ

- **ヘルプを表示**: `nb help`
- **サブコマンドのヘルプ**: `nb help add`

nb は Git を使用して変更を自動的にコミットし、バージョン管理を行います。詳細は `nb help` を参照してください。

## GitHub との同期

nb は各ノートブックを Git リポジトリとして管理しており、リモートリポジトリ（GitHub など）と同期することができます。これにより、複数のデバイス間でノートブックを共有・同期できます。

### リモートリポジトリの設定

- **リモートを設定**: `nb remote set https://github.com/username/repo.git`
- **リモートを削除**: `nb remote remove`

### 同期

- **手動同期**: `nb sync`
- **自動同期を有効化**: `nb set auto_sync 1`（デフォルトで有効）
- **すべてのノートブックを同期**: `nb sync --all`

### プライベートリポジトリ

プライベートリポジトリを使用する場合、Git の認証を設定する必要があります。HTTPS の場合、クレデンシャルをキャッシュするか、SSH キーを使用します。

### 競合解決

同期中に競合が発生した場合、nb は競合マーカーをファイルに挿入します。`nb edit` でファイルを編集し、競合を解決してください。

詳細は `nb help sync` および `nb help remote` を参照してください。

## タグ付け

ノートにタグを付けて分類・整理できます。

### タグの操作

- **タグを追加**: `nb <ノートID> --tag "タグ名"`
- **複数のタグを追加**: `nb <ノートID> --tag "タグ1" --tag "タグ2"`
- **タグを削除**: `nb <ノートID> --tag "タグ名" --delete`
- **すべてのタグを表示**: `nb tags`
- **特定のタグでフィルタリング**: `nb ls --tag "タグ名"` または `nb --tag "タグ名"`

### タグ検索

- **タグで検索**: `nb search --tag "タグ名"` または `nb search --tags "タグ名1,タグ名2"`

## Wikiスタイルのリンク

ノート間を `[[リンク名]]` 形式でリンクできます。

### リンクの作成

Markdownファイル内で `[[ノート名]]` または `[[ノートID]]` と記述すると、他のノートへのリンクになります。

- **リンクの表示**: `nb show <ノートID> --render` でリンクが自動的に変換されます
- **リンク先ノートを開く**: `nb browse` のWebインターフェースからクリックできます
- **リンクされているノートを確認**: `nb backlinks <ノートID>`

## 暗号化機能

機密情報を含むノートを暗号化して保護できます。

### 暗号化の操作

- **ノートを暗号化**: `nb encrypt <ノートID>`（パスフレーズを設定）
- **暗号化ノートを復号化して表示**: `nb decrypt <ノートID>`
- **暗号化ノートを復号化して編集**: `nb edit <ノートID>`（自動的に復号化）
- **暗号化ノートのリスト**: `nb ls --encrypted`
- **暗号化を解除**: `nb decrypt <ノートID> --unencrypt`

### 注意事項

暗号化されたノートは、パスフレーズを入力しないと内容を確認できません。パスフレーズを忘れないように注意してください。

## Pandoc変換

Pandocを使用して、ノートを様々な形式に変換できます。

### 変換形式

- **PDF**: `nb export <ノートID> --to pdf`
- **HTML**: `nb export <ノートID> --to html`
- **Word (docx)**: `nb export <ノートID> --to docx`
- **EPUB**: `nb export <ノートID> --to epub`
- **LaTeX**: `nb export <ノートID> --to latex`

### 変換オプション

- **出力ファイル名を指定**: `nb export <ノートID> --to pdf --output "ファイル名.pdf"`
- **すべてのノートを変換**: `nb export --to html --all`
- **ノートブック全体を変換**: `nb export <ノートブック名> --to pdf`

## フィルタリング・ソート

ノートリストを様々な条件で絞り込んだり、並び替えたりできます。

### フィルタリング

- **タグでフィルタ**: `nb ls --tag "タグ名"`
- **タイプでフィルタ**: `nb ls --type markdown` または `nb ls --type bookmark`
- **日付でフィルタ**: `nb ls --after "2024-01-01"` または `nb ls --before "2024-12-31"`
- **検索と組み合わせ**: `nb search "キーワード" --tag "タグ名"`

### ソート

- **日付順（新しい順）**: `nb ls --sort modified`（デフォルト）
- **日付順（古い順）**: `nb ls --sort modified:asc`
- **タイトル順**: `nb ls --sort title`
- **ファイルサイズ順**: `nb ls --sort size`

## 統計情報

ノートブックやノートの統計情報を確認できます。

- **ノート数を表示**: `nb count` または `nb --count`
- **ノートブック別の統計**: `nb notebooks --count`
- **詳細な統計情報**: `nb stats` または `nb statistics`

## エイリアス・ショートカット

よく使うコマンドに短縮名を設定できます。

### エイリアスの設定

シェル設定ファイル（`.zshrc` や `.bashrc`）に以下を追加：

```bash
# nb コマンドのエイリアス
alias n="nb"
alias na="nb add"
alias ne="nb edit"
alias ns="nb show"
alias nd="nb delete"
alias nl="nb ls"
alias nls="nb ls"
```

### よく使うショートカット

- `nb a` = `nb add`
- `nb e` = `nb edit`
- `nb s` = `nb show`
- `nb d` = `nb delete`
- `nb l` = `nb ls`

## テンプレート機能

新しいノートを作成する際に、テンプレートを使用できます。

### テンプレートの作成

1. テンプレートファイルを作成: `nb edit templates/テンプレート名.md`
2. テンプレートの内容を記述（プレースホルダーとして `{{title}}` などを使用可能）

### テンプレートの使用

- **テンプレートを指定してノート作成**: `nb add --template "テンプレート名" "ノートタイトル"`
- **デフォルトテンプレートを設定**: `nb set default_template "テンプレート名"`
- **テンプレートのリスト**: `nb templates list`

## 履歴とバージョン管理

Git を使用したバージョン管理機能を活用できます。

### 履歴の確認

- **変更履歴を表示**: `nb history <ノートID>` または `nb log <ノートID>`
- **すべての履歴**: `nb history --all`
- **簡易表示**: `nb history --oneline`

### バージョンの操作

- **差分を表示**: `nb diff <ノートID>` または `nb diff <ノートID> <コミットID>`
- **特定のバージョンを表示**: `nb show <ノートID> --version <コミットID>`
- **過去のバージョンに戻す**: Git コマンドを使用して復元
- **特定のコミットを確認**: `nb git show <コミットID>`

## インポート/エクスポート

他のアプリケーションやファイルからデータを取り込んだり、エクスポートしたりできます。

### インポート

- **Markdownファイルをインポート**: `nb import /path/to/file.md`
- **複数ファイルをインポート**: `nb import /path/to/directory/`
- **URLからインポート**: `nb import https://example.com/article`
- **標準入力からインポート**: `cat file.md | nb import --stdin`

### エクスポート

- **ノートをエクスポート**: `nb export <ノートID> --to markdown`
- **複数のノートをエクスポート**: `nb export --to markdown --all`
- **ノートブック全体をエクスポート**: `nb export <ノートブック名> --to markdown`

## アーカイブ機能

古いノートや使用頻度の低いノートをアーカイブできます。

### アーカイブの操作

- **ノートをアーカイブ**: `nb archive <ノートID>`
- **複数のノートをアーカイブ**: `nb archive <ノートID1> <ノートID2>`
- **アーカイブを表示**: `nb archive list` または `nb archive`
- **アーカイブから復元**: `nb archive unarchive <ノートID>`
- **条件に基づいてアーカイブ**: `nb archive --before "2023-01-01"`（指定日以前のノートをアーカイブ）

### アーカイブノートブック

- **アーカイブノートブックを作成**: `nb notebooks add archive`
- **アーカイブノートブックに移動**: `nb move <ノートID> archive`

## プラグイン・拡張機能

nb の機能を拡張するプラグインを利用できます。

### プラグインの管理

- **プラグインをインストール**: `nb plugins install <プラグイン名>`
- **プラグインをアンインストール**: `nb plugins uninstall <プラグイン名>`
- **インストール済みプラグインをリスト**: `nb plugins list`
- **プラグインを更新**: `nb plugins update`
- **利用可能なプラグインを検索**: `nb plugins search`

### カスタマイズ

- **プラグインディレクトリの設定**: `nb set plugins_dir /path/to/plugins`
- **プラグインの有効化/無効化**: `nb plugins enable <プラグイン名>` / `nb plugins disable <プラグイン名>`
- **カスタムスクリプト**: `~/.nb/scripts/` ディレクトリにスクリプトを配置

### よくあるプラグイン

- **Web クローラー**: Webページの内容を取得してノート化
- **PDF リーダー**: PDFファイルをインポートしてテキスト抽出
- **画像処理**: 画像の最適化や変換
- **コードハイライト**: コードブロックのシンタックスハイライト強化

詳細な情報については `nb help plugins` を参照してください。

---

*初回発行: 2025年11月1日*
*最終更新: 2025年11月5日*
