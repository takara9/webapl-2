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


1 「新規ジョブ作成」をクリック
2  ジョブの名前（日本語でもOK)をインプット
3  ビルドトリガをクリック、SCMをポーリング  "H/5 * * * *" をインプット
4  パイプライン
  1 Pipeline script from SCM
  2 SCM: Git
  3 リポジトリURL: https://gitlab.labo.local/tkr/webapl-2.git
  4 　　　　　認証情報: https://gitlab.labo.local/　のユーザーID/パスワード
  5 ビルドするブランチ "*/master" -> "*/main"へ変更
  6 Script Path:  Jenkinsfile
5 「保存」をクリック



 　　
  



