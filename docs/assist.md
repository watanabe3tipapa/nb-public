---
title: nb - Public - assist
---

# nb関連の備忘録＆チートシート

## Markdown チートシート

以下は、Markdownの主要な記法を網羅的にまとめたものです。

---

## 1. 見出し (Headers)

見出しは `#` の数でレベルを表現します。

```markdown
# 見出し 1
## 見出し 2
### 見出し 3
#### 見出し 4
##### 見出し 5
###### 見出し 6
```

---

## 2. 段落と改行 (Paragraphs and Line Breaks)

段落は1行以上の空行で区切られます。強制的に改行を入れたい場合は、行末に2つ以上のスペースを入れます。

```markdown
これは最初の段落です。

これは次の段落です。

この行の最後にはスペースが2つ入っています。
そのため、ここで改行されます。
```

---

## 3. テキストの強調 (Emphasis)

- **太字 (Bold)**: `**テキスト**` または `__テキスト__`
- *イタリック (Italic)*: `*テキスト*` または `_テキスト_`
- ***太字 & イタリック (Bold and Italic)***: `***テキスト***` または `___テキスト___`
- ~~打ち消し線 (Strikethrough)~~: `~~テキスト~~`

---

## 4. 引用 (Blockquotes)

`>` を行頭に置くことで引用を表現します。ネストも可能です。

```markdown
> これは引用です。
> 
> > これはネストされた引用です。
```

---

## 5. リスト (Lists)

### 順序なしリスト (Unordered Lists)

`*`, `+`, `-` のいずれかを行頭に置きます。

```markdown
* アイテム 1
* アイテム 2
  * サブアイテム 2.1
  * サブアイテム 2.2
```

### 順序付きリスト (Ordered Lists)

数字とピリオドを行頭に置きます。数字は自動で連番になります。

```markdown
1. 最初のアイテム
2. 2番目のアイテム
3. 3番目のアイテム
   1. サブアイテム 3.1
```

---

## 6. コード (Code)

### インラインコード (Inline Code)

バッククォート (`` ` ``) で囲みます。

```markdown
これは `インラインコード` です。
```

### コードブロック (Code Blocks)

3つのバッククォート (```` ``` ````) または3つのチルダ (`~~~`) で囲みます。シンタックスハイライトも指定できます。

````markdown
```javascript
function hello() {
  console.log("Hello, world!");
}
```
````

---

## 7. 水平線 (Horizontal Rules)

3つ以上のハイフン (`---`)、アスタリスク (`***`)、またはアンダースコア (`___`) を使います。

```markdown
---
***
___
```

---

## 8. リンク (Links)

`[リンクテキスト](URL "タイトル")` の形式で記述します。タイトルは省略可能です。

```markdown
[Google](https://www.google.com "Googleへ")
```

---

## 9. 画像 (Images)

リンクの前に `!` を付けます。

```markdown
![代替テキスト](/path/to/image.jpg "画像タイトル")
```

---

## 10. テーブル (Tables)

パイプ (`|`) とハイフン (`-`) を使ってテーブルを作成します。コロン (`:`) でカラムの揃えを指定できます。

```markdown
| 左揃え | 中央揃え | 右揃え |
| :--- | :---: | ---: |
| Cell 1 | Cell 2 | Cell 3 |
| Cell 4 | Cell 5 | Cell 6 |
```

---

## 11. タスクリスト (Task Lists)

リストのアイテムの先頭に `[ ]` または `[x]` を置きます。

```markdown
- [x] 完了したタスク
- [ ] 未完了のタスク
- [ ] これからやるタスク
```

---

## 12. エスケープ (Escaping)

Markdownの記法として解釈される文字をそのまま表示したい場合は、バックスラッシュ (`\`) をその文字の前に置きます。

```markdown
\*これはアスタリスクです\*
```

---

## Git コマンド チートシート

以下は、Gitの主要なコマンドを網羅的にまとめたものです。

---

## 1. 初期設定とリポジトリ作成

### `git config`
Gitの基本設定を行います。

```bash
# ユーザー名を設定
git config --global user.name "Your Name"

# メールアドレスを設定
git config --global user.email "your.email@example.com"

# 設定内容を確認
git config --list
```

### `git init`
カレントディレクトリに新しいGitリポジトリを作成します。

```bash
git init
```

### `git clone`
リモートリポジトリのクローン（コピー）をローカルに作成します。

```bash
git clone <repository_url>
```

---

## 2. 変更の記録

### `git status`
リポジトリの状態（変更されたファイル、ステージングエリアの状態など）を表示します。

```bash
git status
```

### `git add`
変更されたファイルをステージングエリアに追加し、次のコミットに含める準備をします。

```bash
# 特定のファイルを追加
git add <file_name>

# カレントディレクトリの全ての変更を追加
git add .
```

### `git commit`
ステージングエリアにある変更をローカルリポジトリに記録（コミット）します。

```bash
# メッセージ付きでコミット
git commit -m "Your commit message"

# ステージングとコミットを同時に行う (追跡中のファイルのみ)
git commit -am "Your commit message"
```

### `git diff`
作業ディレクトリとステージングエリア、またはコミット間の差分を表示します。

```bash
# 作業ディレクトリとステージングエリアの差分
git diff

# ステージングエリアと最新コミットの差分
git diff --staged

# 2つのコミット間の差分
git diff <commit1> <commit2>
```

---

## 3. ブランチ操作

### `git branch`
ブランチの一覧表示、作成、削除を行います。

```bash
# ローカルブランチの一覧
git branch

# リモートブランチを含む全ての一覧
git branch -a

# 新しいブランチを作成
git branch <branch_name>

# ブランチを削除
git branch -d <branch_name>
```

### `git checkout`
ブランチを切り替えます。

```bash
git checkout <branch_name>
```

### `git switch` (推奨)
ブランチを切り替えます (`checkout`より安全)。

```bash
git switch <branch_name>

# ブランチを作成してすぐに切り替える
git switch -c <new_branch_name>
```

### `git merge`
指定したブランチの変更を現在のブランチに取り込みます。

```bash
# masterブランチにいる状態で、featureブランチをマージ
git merge feature
```

### `git rebase`
現在のブランチのベースとなるコミットを、指定したブランチの最新コミットに変更します。コミット履歴が直線的になります。

```bash
# featureブランチで実行
git rebase master
```

---

## 4. リモートリポジトリとの連携

### `git remote`
リモートリポジトリの管理を行います。

```bash
# リモートリポジトリの一覧
git remote -v

# 新しいリモートリポジトリを追加
git remote add <name> <url>
```

### `git push`
ローカルリポジトリのコミットをリモートリポジトリにアップロードします。

```bash
git push <remote_name> <branch_name>

# 例: originリモートのmasterブランチにプッシュ
git push origin master
```

### `git pull`
リモートリポジトリの最新の変更を取得し、現在のブランチにマージします。(`fetch` + `merge`)

```bash
git pull <remote_name> <branch_name>
```

### `git fetch`
リモートリポジトリの最新の変更を取得しますが、マージは行いません。

```bash
git fetch <remote_name>
```

---

## 5. 履歴の確認と修正

### `git log`
コミット履歴を表示します。

```bash
# 基本的なログ
git log

# 1行で簡潔に表示
git log --oneline

# グラフ形式で表示
git log --graph --oneline --decorate --all
```

### `git reset`
コミットを取り消したり、ステージングエリアの状態を変更したりします。

```bash
# ステージングエリアからファイルを取り除く (コミットはそのまま)
git reset HEAD <file_name>

# 指定したコミットまで戻る (変更は作業ディレクトリに残る)
git reset --soft <commit_hash>

# 指定したコミットまで戻る (変更は作業ディレクトリから消える)
git reset --hard <commit_hash>
```

### `git revert`
指定したコミットの変更を打ち消す新しいコミットを作成します。履歴を書き換えないため、共有リポジトリで安全に使えます。

```bash
git revert <commit_hash>
```

### `git stash`
まだコミットしたくない変更を一時的に退避させます。

```bash
# 変更をスタッシュ
git stash

# スタッシュした変更を一覧表示
git stash list

# 最新のスタッシュを適用してスタッシュリストから削除
git stash pop

# 最新のスタッシュを適用 (リストには残る)
git stash apply
```

---

*初回発行: 2025年11月1日*
*最終更新: 2025年11月5日*