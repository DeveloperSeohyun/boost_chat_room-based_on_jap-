# プログラム紹介
現在のネットワークバックエンドのアーキテクチャは、一般的に Reactor ネットワークモデル を基盤としたマルチスレッド型のサービス構成です。これはイベント駆動型のアーキテクチャで、スレッドプール管理技術の進化にも関わらず、カーネル空間からユーザー空間へのデータコピー待ちの時間 を完全に回避することは難しいという特性を持ちます。

本システムは Boostオープンソースライブラリ を活用し、C++言語によりProactorマルチスレッドネットワークモデル に基づいたクライアント/サーバ（C/S）構成のリアルタイムチャットシステムを構築しています。

クライアント側は Qt6 を用いて開発されており、

メッセージの通信形式としては nlohmann ライブラリ による JSONフォーマット および HTTP形式 を採用しています。

本システムは以下の基本機能を実装しています：

ユーザー登録

ユーザーログイン

セッション管理

ユーザー検索

フレンド/グループチャットの管理

フレンド追加・削除

ローカル履歴メッセージの保存と読み込み

オフライン時のメッセージ・通知の管理

さらに、macOSおよびWindowsの両方で同一のコードベースからコンパイル可能であり、クロスプラットフォーム開発をより効率的に行うことができます。


# 特徴と新しさ

本システムは最新の標準と機能に積極的に対応しており、最低限のコンパイル要件は C++17です。

使用している主な技術：

Boost.Asio および Boost.MySQL（※Boost 1.83 は2023年8月11日公開。MySQLモジュールは1.82で初登場）

nlohmann/json ライブラリ

Qt6 によるクライアント開発

CMake によるビルド管理

これらすべてはクロスプラットフォーム対応を前提として設計されており、特定のOSに依存するAPIを極力排除しています。

# ローカル開発環境
開発環境：

OS：Windows 10 Version 22H2 x64

開発フレームワーク：Qt 6.2.3

必要な外部ライブラリ：
　- Boost version 1.82.3
　- nlohmann/json version 3.10.4

コンパイラ：MinGW 8.1.0

使用C++バージョン：C++11

ビルドツール：CMake

ソースコード管理：git

# 本番デプロイ環境
デプロイ環境：

OS：Windows 10 Version 22H2 x64

CPU：AMD Ryzen 7 4800H with Radeon Graphics 2.90 GHz

メモリ：16.0 GB（使用可能：15.4 GB）

# どうやって動きますか?


## サーバーを起動する
### 手順1：プロジェクトをビルドする

１－まず、以下のコマンドでリポジトリをローカルにクローンします：

```bash
git clone https://github.com/DeveloperSeohyun/boost_chat_room-based_on_jap-.git
cd your-repo
```

画面：
<img width="877" height="163" alt="ab9b8c24abc53b34ecab214efd27da4b" src="https://github.com/user-attachments/assets/00a0a583-a720-40f7-9d51-3a28c11ec349" />

２－次に、プロジェクトディレクトリ内で以下のコマンドを実行してビルドします：
```bash
cmake .
make
```

<img width="775" height="435" alt="image" src="https://github.com/user-attachments/assets/b05f9db6-d3f2-4bce-92aa-ecfcec0f8696" />

もしビルドできなければ、是非もう一度開発環境を確認してください、特に
boost.asio、boost.mysql、nlohmann/jsonなどのライブラリ持っていますか？バージョンとか最低より高くあるんですか？
本コード倉庫の中で必要なライブラリすべて完備していないですが、自分自身で準備してください。

### 手順2：サーバーをスタートする

１－本プロジェクトはチャットシステムで、バックエンド側起動する必要があるサーバーが2つあります。
ImageServer and MychatServer
それぞれ起動するお願いします。
<img width="782" height="160" alt="image" src="https://github.com/user-attachments/assets/68d38e7e-a39e-42fa-9837-239755e469c8" />
サーバーを起動すると、デフォルトデータへのクエリが自動的に実行されます。サーバーから出力される情報に基づいて、データベースへの接続が正常かどうかを判断できます。

起動できない時には、「port bind error」というエラーを確認してください、
MychatServer default port:23610
ImageServer default port:23611
具体的な設定情報はetcフォルダ内の2つのファイルにありますので、サーバーのIPアドレスを更改するなどの必要な状況では応じて参照してください。

## クライアントを起動する
クライアントに関係するコードはこちらではなく、でも、クライアント起動するというのはサーバースタートに繋がるとおもうんですが、一応にこちらで説明しておきます。
クライアントのスタートは簡易だと思って、一言に尽きって、対応しているファルダをQT6以上バージョンで開けて、CMakeListsが完備なので、直接にRunやDebugのムードで起動することがうまくできるだと思います
``` cpp
#define BASE_JAP
```
この言語を抜いてプロジェクトは中国語バージョンに戻ります。具体的な機能は不変なのに...






# 运行界面
ログイン画面
<img width="533" height="361" alt="image" src="https://github.com/user-attachments/assets/de01fe82-ba79-49d7-b4dd-e701436ef929" />

サーバーはログイン要求を受け入れて処理する状況
<img width="740" height="236" alt="image" src="https://github.com/user-attachments/assets/93f4db70-9ab6-40c0-b3f2-5473e78aae93" />

サインした後メイン画面
<img width="976" height="651" alt="image" src="https://github.com/user-attachments/assets/c061d35f-977b-488a-9d61-2d7e2645b1fe" />


好友添加
友達を追加
![image](https://github.com/user-attachments/assets/77025e9c-ac79-4e11-8907-58a6dbd4530c)
![image](https://github.com/user-attachments/assets/c5cba34b-fa19-42f7-abc1-231268fc51b5)
对方收到系统信息：
![image](https://github.com/user-attachments/assets/9eca8275-a12a-415b-837a-6869d3356d0d)


正常通讯
双方がお互いにメッセージを送信する
![image](https://github.com/user-attachments/assets/70459117-b7df-483b-8d0d-b8ecedca9561)
消息格式打包
メッセージ形式のカプセル化
![image](https://github.com/user-attachments/assets/6e9f2286-97e9-4ba9-94be-4c537fdf3275)





