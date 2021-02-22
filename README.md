# webapl-2

シンプルなPHP Webアプリケーション

## ローカルでビルドして実行する


~~~
docker build -t webapl2:1.0 .
docker run -it -p 8080:8080 --rm --name test webapl2:1.0
~~~

~~~
docker tag webapl2:1 harbor.labo.local/tkr/webapl2:1
docker push harbor.labo.local/tkr/webapl2:1
~~~


## Jenkinsパイプラインで、ビルドからデプロイまで実行

### GitLabリポジトリを5分間隔でポーリングして変更があった場合にビルドを実行する

1. 「新規ジョブ作成」をクリック
1.  ジョブの名前（日本語でもOK)をインプット
1.  ビルドトリガのタブをクリック、SCMをポーリング  "H/5 * * * *" をインプット
1.  パイプライン
1. Pipeline script from SCMを選択
1. SCM: Git を選択
1. リポジトリURL: https://gitlab.labo.local/tkr/webapl-2.git
1. 認証情報: https://gitlab.labo.local/　のユーザーID/パスワードを追加して選択
1. ビルドするブランチ "*/master" -> "*/main"へ変更
1. Script Path:  Jenkinsfile
1. 「保存」をクリック


### GitLabへpushされた時に、ビルドを実行する設定

1.「新規ジョブ作成」をクリック
1. ジョブの名前（日本語でもOK)をインプット
1. 全体のタブ
    1. GitLab Connection にコネクション名をセット（事前登録必要）
    1. GitLab Repository Name にリポジトリ名をセット
1. ビルドトリガのタブをクリック
    1. Build when a change is pushed to GitLab. GitLab webhook にチェック
    1. Enabled GitLab triggersのPush Eventsにチェック
    1. Rebuild open Merge Requests で On push to source brance を選択
    1. 高度な設定をクリック
        1. Secret token をクリック
        1. Generate クリックして、トークンを生成
1. パイプラインのタブをクリック
    1. Pipeline script from SCMを選択
    1. SCM: Git を選択
        1. リポジトリURL: https://gitlab.labo.local/tkr/webapl-2.git
        1. 認証情報: https://gitlab.labo.local/　のユーザーID/パスワードを追加して選択
        1. ビルドするブランチ "*/master" -> "*/main"へ変更
    1. Script Path:  Jenkinsfile
1. 「保存」をクリック






 　　
  



