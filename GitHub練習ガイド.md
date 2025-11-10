# GitHub練習ガイド（MCP使用版）

このガイドでは、**GitHub MCP**を使ってGitHubの操作を練習しながら学べます。
CursorのAIアシスタントに依頼するだけで、GitHubの操作が自動化できます。

## 🎯 GitHubでできること

### 1. リポジトリの管理
- コードの保存・共有
- バージョン管理
- 履歴の追跡

### 2. コラボレーション
- プルリクエスト（PR）でのコードレビュー
- イシューでの課題管理
- ディスカッションでの議論

### 3. プロジェクト管理
- プロジェクトボードでの進捗管理
- マイルストーンでの目標設定
- ラベルでの分類

### 4. 自動化
- GitHub ActionsでのCI/CD
- 自動テストの実行
- 自動デプロイ

## 📋 練習ステップ（MCP使用版）

### ステップ1: GitHubでリポジトリを作成（MCP使用）
CursorでAIに以下のように依頼：
```
GitHubでリポジトリを作成して。名前は「git-practice」、説明は「GitとGitHubの練習用リポジトリ」で。
```

**MCPで実行される操作：**
- `mcp_github_create_repository` が実行される
- リポジトリが自動的に作成される

### ステップ2: ローカルと連携

> **📘 初期化とは？**
> `git init` は、**Git管理を始めるときに一番最初にやること**です。
> - `git init` を実行すると、このフォルダ内に `.git` という隠しフォルダが作成されます
> - Git が変更履歴を記録できるようになります
> - 一度実行すれば、そのフォルダーはGit管理下になります
> - 以降のファイル変更がコミットとして追跡されます

```bash
# Gitリポジトリを初期化（まだの場合）
cd Git練習
git init  # ← 実行した結果: "Initialized empty Git repository ..."

# リモートを追加
# リモート追加とは：ローカルのGitリポジトリとGitHubのリポジトリを紐付ける作業
# origin = GitHubのリポジトリのURL（名前は「origin」が一般的）
git remote add origin https://github.com/KazukiUrano/git-practice.git
# 確認コマンド: git remote -v で設定を確認できる

# ファイルをステージング
# VS Codeなどでファイル名の左に表示される "U" は "Untracked" の略。
# → Gitがまだ追跡していない新規ファイルを意味する。
# `git add` を実行し、追跡対象にすると "A"（Added）や "M"（Modified）などに変わる。
git add .

# 最初のコミット
git commit -m "初回コミット: 練習プロジェクトの作成"

# ブランチ名をmainに変更
git branch -M main

# 最初のプッシュ
git push -u origin main
```

### ステップ3: イシューを作成（MCP使用）
CursorでAIに以下のように依頼：
```
GitHubのgit-practiceリポジトリにイシューを作成して。
タイトルは「練習用イシュー」、説明は「これはGit練習用のイシューです」で。
```

**MCPで実行される操作：**
- `mcp_github_create_issue` が実行される
- イシューが自動的に作成される

### ステップ4: ブランチで作業
```bash
# 新しいブランチを作成
git checkout -b feature/新機能

# ファイルを編集
# （エディタでファイルを編集）

# 変更をステージング
git add .

# コミット
git commit -m "新機能を追加"

# ブランチをプッシュ
git push origin feature/新機能
```

### ステップ5: プルリクエストを作成（MCP使用）
CursorでAIに以下のように依頼：
```
GitHubのgit-practiceリポジトリにプルリクエストを作成して。
feature/新機能ブランチをmainブランチにマージするPRで、
タイトルは「新機能を追加」、説明は「練習用の新機能を追加しました」で。
```

**MCPで実行される操作：**
- `mcp_github_create_pull_request` が実行される
- プルリクエストが自動的に作成される

### ステップ6: プルリクエストをマージ（MCP使用）
CursorでAIに以下のように依頼：
```
GitHubのgit-practiceリポジトリのプルリクエスト#1をマージして。
```

**MCPで実行される操作：**
- `mcp_github_merge_pull_request` が実行される
- プルリクエストが自動的にマージされる

### ステップ7: ファイルをGitHub上で作成・更新（MCP使用）
CursorでAIに以下のように依頼：
```
GitHubのgit-practiceリポジトリに「練習用ファイル.txt」を作成して。
内容は「これはMCPで作成したファイルです」で。
```

**MCPで実行される操作：**
- `mcp_github_create_or_update_file` が実行される
- ファイルが自動的に作成・更新される

## 🔄 よくあるワークフロー（MCP使用版）

### 機能追加の流れ
1. **イシューを作成（MCP）**
   - AIに「イシューを作成して」と依頼
   - `mcp_github_create_issue` が実行される

2. **ブランチを作成（ローカル）**
   ```bash
   git checkout -b feature/機能名
   ```

3. **コードを書く（ローカル）**
   - エディタでファイルを編集

4. **コミット・プッシュ（ローカル）**
   ```bash
   git add .
   git commit -m "機能を追加"
   git push origin feature/機能名
   ```

5. **プルリクエストを作成（MCP）**
   - AIに「プルリクエストを作成して」と依頼
   - `mcp_github_create_pull_request` が実行される

6. **レビューを受ける（GitHub上）**
   - GitHubのWeb UIでレビューコメントを確認

7. **マージ（MCP）**
   - AIに「プルリクエストをマージして」と依頼
   - `mcp_github_merge_pull_request` が実行される

### バグ修正の流れ
1. **イシューを作成（MCP）**
   - AIに「バグ報告のイシューを作成して」と依頼
   - `mcp_github_create_issue` が実行される

2. **ブランチを作成（ローカル）**
   ```bash
   git checkout -b fix/バグ名
   ```

3. **修正を実装（ローカル）**
   - エディタでバグを修正

4. **コミット・プッシュ（ローカル）**
   ```bash
   git add .
   git commit -m "バグを修正"
   git push origin fix/バグ名
   ```

5. **プルリクエストを作成（MCP）**
   - AIに「プルリクエストを作成して」と依頼
   - `mcp_github_create_pull_request` が実行される

6. **テストを確認（GitHub上）**
   - GitHub Actionsの結果を確認（設定している場合）

7. **マージ（MCP）**
   - AIに「プルリクエストをマージして」と依頼
   - `mcp_github_merge_pull_request` が実行される

## 💡 MCPでできる便利な操作

### リポジトリ操作
- **リポジトリの作成**: `mcp_github_create_repository`
- **ファイルの作成・更新**: `mcp_github_create_or_update_file`
- **ファイルの取得**: `mcp_github_get_file_contents`

### イシュー管理
- **イシューの作成**: `mcp_github_create_issue`
- **イシューの更新**: `mcp_github_update_issue`
- **イシューの一覧取得**: `mcp_github_list_issues`
- **イシューへのコメント追加**: `mcp_github_add_issue_comment`

### プルリクエスト管理
- **プルリクエストの作成**: `mcp_github_create_pull_request`
- **プルリクエストのマージ**: `mcp_github_merge_pull_request`
- **プルリクエストのレビュー**: `mcp_github_create_pull_request_review`
- **プルリクエストの一覧取得**: `mcp_github_list_pull_requests`

### その他の便利な機能
- **README.md**: プロジェクトの説明を書く（MCPで作成・更新可能）
- **.gitignore**: コミットしたくないファイルを指定
- **ラベル**: イシューやPRにラベルを付ける（MCPで設定可能）
- **マイルストーン**: 複数のイシューをグループ化

## 🎯 MCPを使うメリット

1. **コマンド不要**: ターミナルでGitコマンドを覚える必要がない
2. **自動化**: AIに依頼するだけで操作が完了
3. **エラー防止**: 手動操作でのミスを減らせる
4. **効率化**: 複数の操作を一度に依頼できる

## 🎓 次のステップ

1. **コラボレーション**
   - 他の人と一緒に作業
   - コードレビューを実践

2. **GitHub Actions**
   - 自動テストの設定
   - CI/CDパイプラインの構築

3. **GitHub Pages**
   - 静的サイトのホスティング
   - ドキュメントの公開

4. **リリース管理**
   - タグの作成
   - リリースノートの作成

