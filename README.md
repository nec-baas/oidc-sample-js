oidc-sample-js: OpenID Connect 認証サンプル（ブラウザ/JavaScript）
========================================================
ブラウザでOpenID Connect 認証を行うためのサンプルです。

BaaS サーバ 事前準備
----------------------
先に BaaS サーバ上に OpenID Connect を設定したテナントを作成しておく必要があります。  
手順は以下の通りです。

1. BaaSコンソールでテナントを新規作成する。認証方式に 通常認証+OIDC認証 を指定すること。
2. OpenID Connect 設定画面の"OPリスト"から使用するOP種別の設定を行う。
3. OpenID Connect 設定画面の"許可するリダイレクトURI(オプション)"にコンテンツサーバ上のlanding.htmlおよびlanding_manual_login.htmlを登録する。  
    (例)  
    * http://[contentserver]/landing.html
    * http://[contentserver]/landing_manual_login.html

コンテンツサーバ 事前準備
---------------------------
js/config.sample.js を js/config.js にコピーし、
BaaSのテナントID、アプリID、アプリキー、APIベースURLなどを設定してください。

### 設定対象
* tenant
* appId
* appKey
* baseUri

SDKをデバッグモードで動作させたい場合は以下の設定をtrueとしてください。

###  設定対象
* debugMode  
  trueの場合、デバッグモード動作となりデバッグログが出力されます。

連携する OpenID Connectプロバイダを指定する場合は以下を設定してください。

###  設定対象
* OpType  
  設定可能な値は以下の通りです。  
    * google: Google
    * other: OpenAM
    * adfs: ADFS (Windows Server 2016)  
* Scope (オプション)

利用手順
--------
コンテンツサーバ上のindex.html（本サンプル） をブラウザで開き、以下のメニューを選択してください。

* Start authentication  
OpenID Connect 認証が成功すると自動的にログインを行います。

* Start authentication(Manual Login)  
OpenID Connect 認証に成功するとloginメニューが表示されます。  
loginメニューを選択するとログインを行います。

ログインが成功すると、画面上にユーザ情報が表示されます。

注意事項
--------
IE11でアクセスする場合、IE11の互換表示設定では接続できないため、設定を無効にするか  
他のブラウザを使用してください。

