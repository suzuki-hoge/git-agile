GitHubを中心としたアジャイル開発

# はじめに的な
Redmine, Jira, 手書きの付箋, etc...

# GitHub
## 単語
リポジトリ
組織
チームメンバー
メンバー
TaskList

## [readme.md] ドキュメントを管理する
共有ディレクトリにExcelでとか辞めよう
管理者がはっきりするし
Macだし

## [default branch] デフォルトブランチを設定する
clone時
他メリットは？

## [protected branches] ブランチを事故から守る
push -f
他メリットは？ブラウザで消せない？

## [branch] ブランチを消す
branchesから
PullRequestマージ時

## [mention] メンバーを紐付ける
確認方法

## [issue link, pull request link] IssueやPullRequestを紐付ける
確認方法

## [gh-pages] 静的なファイルを公開する
デプロイ？共有ディレクトリ？
画像やHTMLモックくらいならgh-pagesで
注意

## [gist] 簡易コード片やMarkdownを公開する
リポジトリに閉じないけど組織には閉じるくらい？
簡易デモの資料や残さなくて良いアジェンダ書いたり
Markdownが表示できる簡易的な場としてよく使う

## [fixes commit] PullRequestのマージ時にIssueを自動的にクローズする
スクショ

## [git template (issue)] Issue作成時の説明欄にテンプレートを設定する
1 of 3

## [git template (pull request)] PullRequest作成時の説明欄にテンプレートを設定する
[fixes commit]

## [web hooks] GitHub上で特定のイベントがあった時にスクリプトを実行する
チャットワークに通知
ブランチとかわかる？リリース通知とか出来るかも？

## [git hooks] Gitコマンドで特定の操作をした時にスクリプトを実行する
フォーマッタとか
テストとか
バージョン埋めるとか

## [milestone] Issueの対応期限を明示する
%

## [search box] リポジトリ内の何かを検索する
-
no: 
[GitHub Issueの検索でできること](http://qiita.com/shunjikonishi/items/c5024e70b0878817725f)

## [jenkins] PullRequestがマージされる際にコンフリクトやテスト失敗があってはならない
具体方法知らないなぁ...

# ZenHub
## 単語

## [estimate] 見積もりをする

## [board] かんばんを運用する
PullRequestはどうするか
レビュー待ち？

## [burn down chart] 進捗を明確にして把握する
スクショ
何の期間の何を計算するのか

## [epic] ストーリをまとめる
機能を示す
複数スプリント
Milestoneはどうするか

## [pipe line] 中長期的な対応時期を管理する
sprint backlog
step1 backlog
product backlog

# 満足していないこと的な
## 割り込みタスク
突発ってストーリーにTaskList

## TaskList
複数人はあまり想定していない？

## 予定管理
打ち合わせのストーリの予定日を見たい
Issue開かないとわからない

# おわりに的な
議論が散らない
markdown
link, list, header, syntax-highlight
原稿をGit管理してみた
