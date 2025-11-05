---
title: nb - Public
---

# nb - Public - INDEX

## 🚧 **工事中**

公開ノートブックへようこそ！ このページは随時追記しています。

### クイックリンク
- [ホーム](index.md)
- [使い方](usage.md)
- [虎の巻](assist.md)

---

## nbコマンドでコンテンツをプッシュする方法

`nb`コマンドを使ってこのノートブックからリモートリポジトリにコンテンツをプッシュするには、以下の手順に従ってください：

1. **リモートリポジトリを設定する**: ノートブックのリモートURLを設定します。
   ```
   nb remote set https://github.com/yourusername/your-repo.git
   ```

2. **変更をプッシュする**: ローカルノートブックをリモートリポジトリと同期し、新しいまたは更新されたコンテンツをプッシュします。
   ```
   nb sync
   ```

   - このコマンドは自動的に変更をコミットし、リモートにプッシュします。
   - 複数のノートブックがある場合、ノートブックを指定してください: `nb example:sync`

Git同期とリモート管理の詳細については、[nbドキュメント](https://xwmx.github.io/nb/#-git-sync)を参照してください。

---

## ファイルの配置

```PlainText
.nb-public
├── README.md
└── docs
    └── index.md（このファイル）
    └── xxx.md（このファイルからのリンク先）
    └── yyy.md（このファイルからのリンク先）
    └── zzz.md（このファイルからのリンク先）
```

> docs/内が web となります


参考：

```mermaid
graph TD
    docs[docs/] --> index[index.md]
    docs --> dotindex[.index]
    docs --> readme[README.md]
```

---

*初回発行: 2025年11月1日*
*最終更新: 2025年11月5日*

---
