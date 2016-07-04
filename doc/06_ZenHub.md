GitHubを中心とした開発プロセス ZenHub

[GitHubを中心とした開発プロセス](http://qiita.com/suzuki-hoge/items/a6e3bdc2cc1cf4e98ea1)のZenHub編です

## はじめに
ざっくり言うとGitHubを拡張してRedmineやJiraの様に課題管理を出来る様にするchrome拡張のことだ！
紹介記事や導入記事はたくさんあるので、具体的な使い方を紹介してみようと思います

### 導入前後のキャプチャ
ZenHub.ioからChrome拡張のインストールをするだけ
![install.png](https://qiita-image-store.s3.amazonaws.com/0/113398/3cb556ee-2757-043a-ecf9-d138f85eff74.png "install.png")

するとこんなのや
![navs.png](https://qiita-image-store.s3.amazonaws.com/0/113398/8b6bcf16-6a7a-6ecd-79df-fe8d347e5244.png "navs.png")

こんな機能が何やら増えている
![sides.png](https://qiita-image-store.s3.amazonaws.com/0/113398/0f35e0a1-d106-09e6-9a50-4809df5d120e.png "sides.png")

ZenHubを導入して一通り必要なことを設定するという想定で進めます

## [story] ストーリを作ろう
ZenHubではIssueをストーリとして扱う

なにやら青いボタンが増えているが、今は気にせずIssueを作ろう
![issue-create.png](https://qiita-image-store.s3.amazonaws.com/0/113398/222c336e-2151-b737-193b-88ba70926a2b.png "issue-create.png")

ここで前に紹介したIssueのテンプレートが役に立つ！ ぜひ「目的」と「Doneの定義」を意識してIssueを作ろう！
[課題管理編: Issue作成時の説明欄にテンプレートを設定する](http://qiita.com/suzuki-hoge/items/3a568dff36fd981082ba#git-template-for-issue-issue%E4%BD%9C%E6%88%90%E6%99%82%E3%81%AE%E8%AA%AC%E6%98%8E%E6%AC%84%E3%81%AB%E3%83%86%E3%83%B3%E3%83%97%E3%83%AC%E3%83%BC%E3%83%88%E3%82%92%E8%A8%AD%E5%AE%9A%E3%81%99%E3%82%8B)

実はストーリを作るのは今までIssueを作っていたやり方と全く変わらない

## [estimate] 見積もろう
ストーリを作ったら見積もろう

プランニングポーカー、してますか？
相対見積もり自体の説明は割愛しますが、ZenHubにおけるIssueはストーリなので、当然見積もりポイントを記入することが出来ます

Issueを作るとき、もしくは作った後に、右サイドにあるEstimateでポイントを入れることが出来る
![pre-estimate.png](https://qiita-image-store.s3.amazonaws.com/0/113398/d5c6f146-3309-56a1-2ee6-b4a69da3314d.png "pre-estimate.png")

入れるとこんな感じ
![post-estimate.png](https://qiita-image-store.s3.amazonaws.com/0/113398/46e017cd-c099-46f8-ff49-fec77644f141.png "post-estimate.png")

Issue一覧にも表示される
![estimated-issues.png](https://qiita-image-store.s3.amazonaws.com/0/113398/28336bba-9b11-ca51-45b8-019021d0836e.png "estimated-issues.png")

## [board] かんばんを使おう
ストーリはかんばんに並べて管理しよう

ストーリがいくつか出来たので、Boardにアクセスしてみよう
![initial-board.png](https://qiita-image-store.s3.amazonaws.com/0/113398/f549aa43-e3c7-2766-e898-5243f462e1be.png "initial-board.png")

何やら意外にたくさんの列があるけど、自分で増減・リネームさせられるので、例えばこんな風にしてみると良いと思う
![moved-board.png](https://qiita-image-store.s3.amazonaws.com/0/113398/de33c327-baec-110f-622f-1452e2f5d754.png "moved-board.png")

ちなみにデフォルトで用意されている列の意味は[ZenHub を使って Kanban 方式をプロジェクトに取り入れる - Qiita](http://qiita.com/yoheimuta/items/ddf4b278f3db79ce2a8f)が参考になる

### ポイント
+ 見積もりポイントやかんばんでの並びはZenHub側に保存されているので、当然他の人と同じ画面を見ることが出来る
+ 列ごとの見積もりポイント合計が表示されていたり、色々なフィルタリングが用意されている
+ Closed列だけ特別なようで、元々どの列に置いてあってもIssue自体がCloseするとここに移される
 + だからfixes commitを使うと完了したストーリを自動でClose列に移動出来る！
 + [課題管理編: PullRequestのマージ時にIssueを自動的にクローズする](http://qiita.com/suzuki-hoge/items/3a568dff36fd981082ba#fixes-commit-pullrequest%E3%81%AE%E3%83%9E%E3%83%BC%E3%82%B8%E6%99%82%E3%81%ABissue%E3%82%92%E8%87%AA%E5%8B%95%E7%9A%84%E3%81%AB%E3%82%AF%E3%83%AD%E3%83%BC%E3%82%BA%E3%81%99%E3%82%8B)

## [chart] バーンダウンチャートを見よう
進捗はバーンダウンチャートで把握しよう

### バーンダウンチャートが見えるまで
一番最初はちょっとだけ手間が必要だ ちょっとだけね

Milestoneがひとつもないと作っておいてね、と言われる [課題管理編: Issueの対応期限を明示する](http://qiita.com/suzuki-hoge/items/3a568dff36fd981082ba#milestone-issue%E3%81%AE%E5%AF%BE%E5%BF%9C%E6%9C%9F%E9%99%90%E3%82%92%E6%98%8E%E7%A4%BA%E3%81%99%E3%82%8B)
![chart-no-milestones.png](https://qiita-image-store.s3.amazonaws.com/0/113398/fb98ce24-c7cb-df1a-3f6d-40d87654c2e1.png "chart-no-milestones.png")

今度はなにやら開始日が設定されてないと言われる
（GitHubのMilestoneには開始日という項目は無いので、この開始日はZenHub側に保存される）
![chart-no-startdate.png](https://qiita-image-store.s3.amazonaws.com/0/113398/accfc824-fe00-358c-d390-acd63e18320d.png "chart-no-startdate.png")

やっと表示されたみたいだけど、Total Story Pointsが0になってしまっている
この期間で対応するIssueにMilestoneを設定しよう
![chart-no-stories.png](https://qiita-image-store.s3.amazonaws.com/0/113398/73ec62de-4e04-d514-4ee3-8325a214cb7f.png "chart-no-stories.png")

設定完了！
理想線も見えているぞ！（ちゃんと土日は働かなくて良い様になっている）
![chart-line.png](https://qiita-image-store.s3.amazonaws.com/0/113398/3887e826-fa04-7114-f8de-573a33982dd9.png "chart-line.png")

1画面に収まらないけど、表示中のMilestoneに紐付くIssueが下に列挙されるぞ
![chart-stories.png](https://qiita-image-store.s3.amazonaws.com/0/113398/36626285-6a14-b843-2f87-c10d51495a9b.png "chart-stories.png")

少し日にちが経ってIssueを一部焼いた様子
ポチにカーソルを合わせると焼いたIssueがわかるぞ
![chart-stories.png](https://qiita-image-store.s3.amazonaws.com/0/113398/18f1b043-c433-5643-31e5-8a05b873de93.png "chart-stories.png")

### 何を数えているか
このバーンダウンチャートは「Milestoneに紐付くIssue」の「見積もりポイント」を数えて描かれている

だから大きいIssueは全てが完了した日に一気にバーンダウンすることになる
日々の進捗が少しでも見たい場合は、Issueの粒度をもっと小さくする必要がある

Issueを分けすぎるとIssueがばらばらに別れて散ってしまい管理が難しそうだ、と思った人は
次のEpicの項を読んでみて欲しい

## [epic] ストーリをまとめよう
Epicと言う機能を使うと、複数のストーリをグルーピングすることができる

### 使い方
Issue作成画面で先ほどは使わなかった青いボタンを押してみよう
![epic-create.png](https://qiita-image-store.s3.amazonaws.com/0/113398/012662e9-ee4f-46fc-e21d-62ea2c873d0a.png "chart-stories.png")

するとなにやらこんな画面になる
Epicに紐付くIssueを作ったり選んだりする画面だ この画面ではすぐ青いCreate Epicボタンを押してしまって良い
![epic-issue-select.png](https://qiita-image-store.s3.amazonaws.com/0/113398/5afc86e8-170c-d4ec-2036-ecd1210b1371.png "chart-stories.png")

余談だけどこの画面でIssueを作成するのは以下の理由でオススメしない

+ 漢字変換のEnterキーでそのままSubmitされてしまい入力途中のタイトルで作ってしまう
+ Issueの説明欄が書けない
 + 折角テンプレートを用意しているのだから、ちゃんとIssue作成画面で作ろう！

実はEpicの実体はLabelの貼られたIssueなのでIssue一覧画面にEpicも並ぶぞ
![epics.png](https://qiita-image-store.s3.amazonaws.com/0/113398/dbe1a0b5-72ca-4bad-af98-b83f5c8777b4.png "chart-stories.png")

IssueをEpicに紐付ける場合はIssue画面からEpicを選択する
![epic-select.png](https://qiita-image-store.s3.amazonaws.com/0/113398/96979f7b-8c01-1253-4a0f-07d5203ae649.png "chart-stories.png")

紐付けが終わったらEpicを開いてみよう
紐付くIssueとそのOpen/Closeの他、合計ストーリ数や合計見積もりポイント数がわかるぞ！
![epic.png](https://qiita-image-store.s3.amazonaws.com/0/113398/00dc2f7e-d16d-55e1-4a80-5ddce07f6799.png "chart-stories.png")

### Epicの考え方
最初はEpicの使い方がよくわからなかったけど、1月ほど使ってみて「Epicは機能を表す」ものだと考えた
Epicは機能を表し、それに紐付くIssueは作業を表す と考えるのが一番しっくりきた

Epicは後述するリリースプランニングの項でも役に立つのでこの考え方を覚えておいて欲しい

また、Epic自体の説明欄には総合仕様を書いておくと良い
![epic-desc.png](https://qiita-image-store.s3.amazonaws.com/0/113398/3fb83796-9d40-9af6-5c10-02da986e28ec.png "chart-stories.png")

## [pipeline] ストーリの対応時期を管理しよう
Pipelineを適切に設定して、対応時期を明示しよう

### Pipelineとは？
かんばんの画面にあった列のこと

この囲ってある部分のひとつひとつをPipelineと言うよ
![moved-board.png](https://qiita-image-store.s3.amazonaws.com/0/113398/de33c327-baec-110f-622f-1452e2f5d754.png "moved-board.png")

### 用意したPipeline
このPipelineについても色々考えてみたけど、今は以下の様なPipelineを用意して使っているよ

Pipeline        | 意味                           
:--             | :--                            
Product Backlog | いつかやること                 
Step1 Backlog   | Step1（初回リリース）でやること
StepX Backlog   | StepXでやること
Sprint Backlog  | 今スプリントでやること         
In Progress     | 進行中                         
Review          | レビュー待ち                   
Closed          | 完了                           

![pipelines.png](https://qiita-image-store.s3.amazonaws.com/0/113398/85e2a61f-baf8-925f-d8e4-ad09d039eb40.png "moved-board.png")

当然かんばんの列内は優先度順になっているので、何からやったら良いかはかんばんを見れば一目瞭然だ！

## リリースプランニングをしよう
Epic（機能）とIssue（作業）が出そろったら、それがいつ実現できるかを決めよう

かんばん画面のLabelフィルターでEpicだけにすると、プロダクト実現に必要な「機能」だけが列挙される
（しかし、Epicには見積もりポイントを振っていないのでかんばんに合計値が表示されない...ちょっと残念...）
![epic-only.png](https://qiita-image-store.s3.amazonaws.com/0/113398/f7034697-73d5-8c78-e4ff-430a70096fa7.png "moved-board.png")

見積もりポイントは各Issueの中を見て把握するか、EpicのEstimateを使おう
（ただしEpicのEstimateと関連するIssueのEstimateは連動しない）
![epic-estimate.png](https://qiita-image-store.s3.amazonaws.com/0/113398/2d3f9e98-d1b9-56d5-c646-b108cca5ddcc.png "moved-board.png")

Epicを機能として捉えていると、いつどんな機能をリリースするのか（したのか）一目瞭然だ！
EpicとPipelineを駆使してリリース内容をわかりやすく管理しよう

## 少し迷ったこと
ここまで説明したのは色々試して納得したことだったけど、実は「これで良いのか？」って思っていることもちょっとだけある

### MilestoneとPipelineについて
MilestoneもPipelineも期間を表すという点は同じだと思うので、それぞれをどう理解すれば良いのか迷った
（というかPipelineの本来の意図はIssueの進捗ステータスの表現、だけなのかな？ リリースタイミングまで表現させるのは制作者の意図に反しているのかも...）

今はZenHubの機能を実現させる手段としてそれぞれを考えているよ

機能                 | 手段     
:--                  | :--      
バーンダウンチャート | Milestone
かんばん             | Pipeline 

だからMilestoneは基本的には今週（=今スプリント）対応するIssueにしか設定していない

### PullRequestについて
今まではずっとIssueの話をしてきたけど、実はPullRequestもPipelineやEstimate等のZenHub機能は設定できる
それにかんばんにも並ぶしMilestoneとEstimateを設定すればバーンダウンチャートにも影響を与える

#### Estimate
PullRequestを見積もるってのは考えづらいので見積もりはしていない
スプリントプランニング後に見積もったら増えちゃってチャートも変なことになるしね

#### Milestone
先述の通りMilestoneはバーンダウンチャートを実現する機能としてとらえている
チャートにPullRequestを反映させる気は無いので設定していない

#### Pipeline
もともとPullRequestの「レビューして」とか「修正中」はラベルで表現していたので、ZenHubを使う様になった今もPullRequestにPipelineは設定していない
けど、In ProgressとReviewingを適切に設定すればPullRequestもかんばんに並べることが出来るのでアリかもしれないな、と思っている

## おまけ
### 料金
![pricing.png](https://qiita-image-store.s3.amazonaws.com/0/113398/424e3198-2f18-90de-f54b-b1d4eba6e255.png "moved-board.png")

publicリポジトリなら無料、privateリポジトリなら月5＄だ
privateリポジトリで使う場合はお試し期間があって、決済後は利用者一人ずつに権利を（5＄で）与える様な感じだ

イメージ的にはGitHubアカウントにZenHub利用権が乗っかっている様なイメージであってると思う

### ZenHubに渡す情報
多分全部
組織の下にリポジトリを複数作るって形だと思うけど、隣のチームがZenHubを使っている様だけどうちは関係ないなー、とはならない
組織単位でZenHubに情報を明け渡す必要があるので、使い出すチームは一応それを意識しておいた方が良いと思う
