GitHubを中心にしたアジャイル開発

# はじめに的な
Redmine, Jira, 手書きの付箋, etc...

## [readme.md] ドキュメントを管理する
そのリポジトリに関するドキュメントはGitHubで管理してGitHubで閲覧したい

### どうして？
+ 共有ファイルサーバにExcelってスタイルはOSの制約があったりするからイヤだ
+ ソースとドキュメントは一元管理されるべきだと思うから
+ ドキュメントもPullRequest等でレビューするべきだよ
+ ドキュメントもバージョン管理したいよ

### 使い方
1. ルートのディレクトリに`README.md`を設置する

会社のチームではコーディング規約とか設計方針、自動化ツールの説明等をそれぞれ`doc/xxx.md`として管理して、`README.md`はそれらへのリンク集にしているよ

## [github wiki] Wikiを管理する
管理ドキュメントが増えてきたらドキュメントをWikiにしよう

### 特徴
+ GitHub上でお手軽に作成出来る
+ ブラウザで作ったWikiは`git clone`してローカルで加筆修正することも出来る
+ ページの一覧が勝手に表示される
+ サイドバーとフッターも書くことが出来る

![github-wiki-sample.png](https://qiita-image-store.s3.amazonaws.com/0/113398/f0d75f7e-99c0-16dc-9b28-14552bb6ef42.png "github-wiki-sample.png")

### 使い方
1. Wikiのタブを選択し、`Create the first page`ボタンを押す
+ Markdownを書いてsubmitする

サイドバーとフッターはそれぞれ`_Sidebar.md`, `_Footer.md`と言うMarkdownを書けば勝手に表示してくれる

## [protected branches] ブランチを事故から守る
masterやdevelopはプロテクトしよう

### どうして？
+ force pushが出来なくなるので事故でデグレったりを防げる
+ ブランチを削除出来なくなる

### 手順
1. GitHubのSettingsタブにあるBranchesを選択
+ Protected branchesを任意の数だけ設定する

## [issue link, pull request link] IssueやPullRequestを紐付ける
関連するIssueやPullRequestは紐づけておこう

### どうして？
+ Issueが作られる → 対応するPullRequestが作られるというパターンが大半だと思うから
 + 大抵方針決めや問題の共有はIssueで行われるため
+ 紐づいたもののステータスや作成者もわかるので、漏れが起きにくい
+ 自動で相互リンクになるため、派生Issue等があっても後でさかのぼりやすい

PullRequestを作る時にIssueを紐づけるとリンクになる
![issue-link-sample.png](https://qiita-image-store.s3.amazonaws.com/0/113398/ecdafc53-68cb-ca8e-3784-f25f318a0f5f.png "issue-link-sample.png")

自動で相互リンクになり、このIssueに関連するPullRequestがOpenしていることがわかる
![pr-link-sample.png](https://qiita-image-store.s3.amazonaws.com/0/113398/2306ee0c-93fe-930d-6725-d7b72c520f57.png "pr-link-sample.png")

### やり方
1. `#1`の様に、`#`に続けて番号を書くだけ

番号はIssueやPullRequestのページ等で確認出来る

## [gist] 簡易コード片やMarkdownを公開する
gistを使うとお手軽にコードの公開が出来る

### どう役に立つ？
+ デモに使うちょっとした資料とか、ちょっとしたまとめ記事とかを置いたりできる
 + Markdownで書くことが出来る
+ ちょっとしたコードレビューをしてもらう
 + コメント等の機能はGitHubに準ずる
+ 言語やFWのサンプルを検索したりもできる

検索してみた例 どれも1ファイル程度の小規模なサンプルだ
![gist-search-sample.png](https://qiita-image-store.s3.amazonaws.com/0/113398/25fc0377-00ec-15f8-271b-47c497bc3194.png "gist-search-sample.png")

### 使い方
1. GitHubのアカウントがあるなら今すぐ使える
![gist-enter.png](https://qiita-image-store.s3.amazonaws.com/0/113398/646deb2b-355d-86e0-6be8-cb2925bf1ae5.png "gist-enter.png")

## [gh-pages] 静的なファイルを公開する
ブランチを作るだけでGit管理しているものを公開する

### どう役に立つ？
+ PullRequestマージ前の開発中の画面をスマホやIEで評価出来る
+ 画像やHTMLモック等の評価もできる
+ 評価サーバへのデプロイや再起動が不要！
+ gistと違うのは、Git管理しているものをそのまま公開出来る点

### 使い方
1. `gh-pages`というブランチ名でpushする
+ `https://ユーザー名.github.io/リポジトリ名/ファイルパス`にアクセスする

### 注意
+ PHPとかは当然動かないのでその場合は別の方法を考える必要がある
 + 開発環境にVagrantを使っていれば、Vagrant Shareが一番手っ取り早いと思う
+ privateリポジトリでもgh-pagesはアクセス制限がかからないらしい

## [fixes commit] PullRequestのマージ時にIssueを自動的にクローズする
Issueはわざわざ自分でCloseしないでマージ時に勝手にCloseさせよう

### 方法
1. コミット時に`fixes #1`や`cloesd #1`とメッセージに含める
+ PullRequestのマージ時に対象Issueが自動でCloseする

PullRequestをCloseした直後だが、自動でCloseされている
![closed-issue.png](https://qiita-image-store.s3.amazonaws.com/0/113398/a4061ae9-f3b6-8394-5d93-adc807d54fc9.png "closed-issue.png")

### どう役に立つ？
+ IssueのCloseし忘れは割と頻繁にあるが、これはとても楽
+ 先述のIssueをPullRequestに紐付ける機能も包含する
+ また後述するZenHubにおいても効果を発揮する

## [git template for issue] Issue作成時の説明欄にテンプレートを設定する
テンプレートを使って明瞭で完了させやすいIssueを書こう

### 使い方
1. `ISSUE_TEMPLATE.md`、もしくは`.github/ISSUE_TEMPLATE.md`というMarkdownを用意する
+ Issueを作成する

たとえば以下の様なファイルを用意した場合

```Markdown:.github/ISSUE_TEMPLATE.md
## 目的

## TaskList
+ [ ] 

## Doneの定義

## 参考

## 留意事項
+ 

## 検討事項
+ 
```

Issue作成ボタンを押した時には既に上記のMarkdownが記述されている（下画像はプレビュー中）
![issue-template.png](https://qiita-image-store.s3.amazonaws.com/0/113398/20c80970-b1cd-fd6b-65d2-91ed3176b41b.png "issue-template.png")

### 良い点
+ 絶対に外せない項目は「目的」と「Doneの定義」
 + 要は「なぜそのIssueが存在し」て「何を達成したら問題が解決する」のかを必ず明示させる
+ 具体的に行うことを列挙するためのTaskListも大切
+ Doneの定義が明確になることで、Issueが適切な粒度になる
+ テンプレート自身もGitで管理出来る

Issueってつい「submit時のJSを直す」とか「参照ロジックを直す」みたいなことだけ書いて作っちゃうけど、
対応するのが自分じゃあ無かったり時間が経ってたりすると「なんだっけ？」ってなりがちだと思う

それを防ぐためにも、例えばこんな感じに書く事を強く推奨するよ
![issue-template-sample.png](https://qiita-image-store.s3.amazonaws.com/0/113398/49cc114d-a4e5-383b-3413-d430ab0ab517.png "issue-template-sample.png")

### 残念な点
+ タイトルは対象外
+ 複数のテンプレートを使い分けることはできない
+ 必ずテンプレートが挿入される

## [git template for pull request] PullRequest作成時の説明欄にテンプレートを設定する
PullRequestもテンプレートを用いて適切なレビューを受けよう

### 使い方
1. `PULL_REQUEST_TEMPLATE.md`、もしくは`.github/PULL_REQUEST_TEMPLATE.md`というMarkdownを用意する
+ PullRequestを作成する

たとえば以下の様なファイルを用意した場合

```Markdown
## 目的

## 関連するIssue等
+ 

## レビューポイント
+ 

## 留意事項
+ 

## 残課題
+ 
```

PullRequest作成ボタンを押した時には既に上記のMarkdownが記述されている（下画像はプレビュー中）
![pr-template.png](https://qiita-image-store.s3.amazonaws.com/0/113398/09e351ac-765d-ae65-0b0e-70774b16dea6.png "pr-template.png")

### 良い点
+ Issueのテンプレートと同じように、絶対に外せない点は「目的」
 + 目的があると自然とレビュー内容や関連課題に意識が行くので、適切なレビューを受けやすい
+ 仕事の内容によっては例えば「動作確認済みブラウザ」なんて項目があっても良いと思う
+ 関連Issueは先述の`#1 〜〜`の形式で書くと先述の通り相互連携されるので書くと良い
+ 対応IssueのDoneの定義がPullRequestマージの場合は、`fixes #1`とCommitしてしまうと連動してCloseする
+ Commitを重ねる間に別問題に気付いた様な場合、残課題に書いている
 + 別対応となる場合は、新たにIssueを作り`#2 〜〜`の様に書くと、後に参照しやすい

### 残念な点
+ こちらも同様に、タイトルは対象外で、複数のテンプレートを使い分けることは出来ない

### Issue/PullRequestのテンプレートを使って
+ 存在は知っていたけど、ここまで良いとは思わなかった
+ 「目的」「Doneの定義」「レビューポイント」があるだけで、明瞭なIssueを作成でき、適切にレビューを受けて、安心してDoneさせることが出来ると実感した
+ 作成時に勝手に出てくるけど邪魔なのであえて消した、という様な困ったことは意外となかった

## [web hooks] GitHub上で特定のイベントがあった時にスクリプトを実行する
特定のイベントを見逃さない様にしよう

### どんな風に使う？
+ Hubotと連携してPullRequestが出来たりIssueがマージされた時にチャットシステムに通知しているよ
+ スクリプト次第ではreleaseブランチがマージされたタイミングでリリース通知を出す、とか出来ると思う

設定画面
![webhooks-p1.png](https://qiita-image-store.s3.amazonaws.com/0/113398/4a01fcca-15d0-121a-0733-02980b78ada4.png "webhooks-p1.png")

結構細かくイベントが用意されている
![webhooks-p2.png](https://qiita-image-store.s3.amazonaws.com/0/113398/dcdaf888-4faf-c202-e062-e11e917cc770.png "webhooks-p2.png")

## [milestone] Issueの対応期限を明示する
適切な対応期限を設定して積み残さない様にしよう

ここからMilestoneの作成・編集が出来るぞ
![milestones-01.png](https://qiita-image-store.s3.amazonaws.com/0/113398/37530baa-cc1c-93af-70ef-8f0723b66456.png "milestones-01.png")

開始日と終了日とタイトル、任意で説明を記述する
![milestones-02.png](https://qiita-image-store.s3.amazonaws.com/0/113398/febc53f7-5050-a7aa-de73-e9f04d50cb12.png "milestones-02.png")

作って置いたMilestoneはLabelやAssigneesと同じようにIssueやPullRequestに設定できる
![milestones-03.png](https://qiita-image-store.s3.amazonaws.com/0/113398/911852e1-5486-825c-3de2-ba2c9a678dad.png "milestones-03.png")

Milestoneの一覧画面では、関連するものの数や、進捗を見ることが出来る
![milestones-04.png](https://qiita-image-store.s3.amazonaws.com/0/113398/96701227-3915-39a8-430a-4f758dd025d0.png "milestones-04.png")

Label等と同様にIssue一覧画面ではMilestoneでのフィルタリングも出来るので、Issue等の優先度を理解しやすくなるぞ

## [search box] リポジトリ内の何かを検索する
検索機能を使いこなして素早く目的の何かを見つけよう

### 実は色々細かい検索が出来る
下のはたまに使う程度だけど、知ってると地味に便利

記法 | 意味     | 例                                     
:--  | :--      | :--                                    
-    | 否定     | -label:bug, -milestone:step03-sprint05
no   | 持たない | no:label, no:milestone                

## [jenkins github pull request builder] PullRequestがマージされる際にJenkinsでビルドする
PullRequestがマージされる際にコンフリクトやテスト失敗があってはならない

会社で写真撮る

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

Jiraでポーリングしたり、自動でClose出来なかったり
全部Gitで良いじゃん
