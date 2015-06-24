# node-static-server
node-static-serverは静的リソースをホストすることを目的とした、シンプルなWebサーバです。  
静的リソースをディレクトリに配置、コマンド1つでローカル環境にWebサーバを起動し、その動作を確認することができます。  
Heroku上で動かすこともできるため、デモ環境の構築や複数のメンバー間でのWebデザインの確認などに用いることも可能です。  

[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy)

### Herokuへのデプロイ
Herokuボタンをクリックすると、自分のHerokuアカウントにデプロイし、動かすことができます。  

#### ローカル環境での編集
任意のディレクトリに移動し、Herokuに作成されたアプリをローカルにクローンし、編集することができます。  

```
heroku git:clone --app アプリ名
```

#### BASIC認証の設定
Herokuに公開の際に、アクセスできる人を制限するためにBASIC認証を設定することができます。  
`basic-auth-connect`を使い、プロダクション環境でユーザ名とパスワードが設定されている時に、BASIC認証が有効になるようにしています。  

Herokuの環境変数として

* BASIC_AUTH_USERNAME
* BASIC_AUTH_PASSWORD

上記の2つを設定することで、BASIC認証が有効になります。  

### ローカル環境での利用
#### ローカル環境へのクローン
```
$ git clone https://github.com/flect-miyake/node-static-server.git
```
Gitを用いて、ローカル環境にリポジトリをクローンします。

#### npmパッケージのインストール
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
