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





