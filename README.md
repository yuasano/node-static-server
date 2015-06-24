# node-static-server
node-static-serverは静的リソースをホストすることを目的とした、シンプルなWebサーバです。  
静的リソースをディレクトリに配置、コマンド1つでローカル環境にWebサーバを起動し、その動作を確認することができます。  
Heroku上で動かすこともできるため、デモ環境の構築や複数のメンバー間でのWebデザインの確認などに用いることも可能です。  

## 使い方
node-static-serverはGitとNode.jsを用いているため、利用する際はそれらがインストールされている必要があります。  

### ローカル環境での利用
#### ローカル環境へのクローン
```
$ git clone https://github.com/flect-miyake/node-static-server.git
```
Gitを用いて、ローカル環境にリポジトリをクローンします。

#### npmパッッケージのインストール
Gitによってクローンされたディレクトリに移動し、npmパッケージのインストールコマンドを実行します。  
```
$ cd node-static-server
$ npm install
```
node-static-serverはExpress4を用いています。  

#### 静的リソースの配置
`public`ディレクトリに、静的リソースを配置します。  
Webサーバ起動時は、`public`ディレクトリがルートディレクトリとなります。  

#### サーバの起動
リポジトリのルートディレクトリで次のコマンドを入力すると、Webサーバが起動します。  
```
$ npm start
```
ブラウザから`localhost:3000`にアクセスすることで、`public`ディレクトリに配置されたコンテツを確認することができます。  

### Herokuへのデプロイ
node-static-serverをHerokuにデプロイし、簡易的なWebサーバとして利用することができます。  
Herokuのアプリ作成やデプロイは、Herokuへの登録とHeroku Toolbeltのインストールが必要となります。  

#### Herokuアプリの作成
リポジトリのルートディレクトリで、`create`コマンドを用いてHerokuアプリを作成します。
```
$ heroku create {APPNAME}
```
このコマンドでHerokuにアプリケーションが作成され、Gitのリモートリポジトリに登録されます。  

#### 環境変数の設定
Herokuにデプロイする前に、以下のコマンドで環境変数の設定を行います。  
```
$ heroku config:set NODE_ENV=production
```

#### Herokuへのデプロイ
Gitを用いてHerokuへのデプロイを行います。
```
$ git push heroku master
```
デプロイが完了したのち、`heroku open`コマンドでアプリケーションを開くことができます。  

### BASIC認証の設定
Herokuに公開した際に、アクセスできる人を制限するためにBASIC認証を設定することができます。  

#### 環境変数でユーザ名とパスワードの設定
Herokuの環境変数としてユーザ名とパスワードを設定することで、BASIC認証が有効となります。  
```
$ heroku config:set BASIC_AUTH_USERNAME={USERNAME}
$ heroku config:set BASIC_AUTH_PASSWORD={PASSWORD}
```
