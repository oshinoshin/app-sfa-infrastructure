# 環境構築概要

## 1.SFAシステム構成
- ※作成後追記する

## 2.ディレクトリ構造
作業用のPCのディレクトリ構造は以下の通り各リポジトリを同一階層に```git clone```してください。

```
tree -L 1
.
├── app-sfa-backend
├── app-sfa-frontend
└── app-sfa-infrastructure
```

- [app-sfa-backend](https://github.com/oshinoshin/app-sfa-backend)  
    - SFAシステムのフロントエンド開発用のリポジトリ

- [app-sfa-frontend](https://github.com/oshinoshin/app-sfa-frontend)  
    - SFAシステムのバックエンド開発用のリポジトリ

- [app-sfa-infrastructure](https://github.com/oshinoshin/app-sfa-infrastructure)  
    - SFAシステムのインフラ設定用のリポジトリ


## 3. 使用ツール (※推奨となるため、記載しているツール以外でも問題ないです)
### Macbook
- [DockerDesktop](https://www.docker.com/ja-jp/products/docker-desktop/)
- [Sourcetree](https://www.sourcetreeapp.com/)
- [DBeaver](https://dbeaver.io/download/)

## 4. 環境構築手順
1. 使用ツールをインストールする


2. gitから各リポジトリのソースをクローンする
- [app-sfa-backend](https://github.com/oshinoshin/app-sfa-backend)  
#```git clone git@github.com:oshinoshin/app-sfa-backend.git```

- [app-sfa-frontend](https://github.com/oshinoshin/app-sfa-frontend)  
#```git clone git@github.com:oshinoshin/app-sfa-frontend.git```

- [app-sfa-infrastructure](https://github.com/oshinoshin/app-sfa-infrastructure)  
#```git clone git@github.com:oshinoshin/app-sfa-infrastructure.git```


3. コンテナを立ち上げる
- (1) DockerDesktopを起動する  

- (2) ディレクトリを移動する
#```cd app-sfa-infrastructure```

- (3) コマンドでコンテナを立ち上げる
#```make up```

- (4)コンテナに接続できるか確認する
    - (4)-1 コンテナIDを調べる  
    #```docker ps -a```

    - (4)-2 コンテナに接続する  
    #```docker exec -it <(3)-1調べたコンテナID> /bin/bash```


4. 環境ごとに必要なconfigファイルのシンボリックリンクを作成する
- ※作成後追記する

5. SFAシステムの開発環境へアクセスできるか確認する  
http://localhost


## コマンド集  
### Docker  

- コンテナ立ち上げ    
#```make up```

- コンテナ削除  
#```make down```
