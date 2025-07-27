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






# クライアントを紹介する
こちらもクライアントの基本機能を紹介しています。あわせて、サーバー側のレスポンスもログとして出力し、添付いたします。

## チャット関係

ログイン機能
<img width="561" height="383" alt="image" src="https://github.com/user-attachments/assets/010eff61-7f88-48e5-8551-df0d6dbd9762" />

サーバーはログインリクエストを受け入れて処理する状況
<img width="959" height="261" alt="image" src="https://github.com/user-attachments/assets/8cd4ab7f-d7d7-4166-bd5a-6632811270af" />

サインした後メイン画面
<img width="1141" height="684" alt="image" src="https://github.com/user-attachments/assets/9e7cff4f-409f-4865-8fe4-b7ea680ac254" />

友だちとお互いにチャットする画面
<img width="1036" height="672" alt="image" src="https://github.com/user-attachments/assets/18142df3-b0d7-45bc-bad4-3bfb9f74d7a7" />

## ユーザー管理

フレンドを探して申請する場合
<img width="976" height="651" alt="image" src="https://github.com/user-attachments/assets/7098d4c2-353c-48a3-8db9-20e5978ca42d" />
<img width="976" height="651" alt="image" src="https://github.com/user-attachments/assets/16023583-b969-4788-bcf3-389f817dfcbb" />
<img width="976" height="651" alt="image" src="https://github.com/user-attachments/assets/d016cddf-f7fd-4cc1-9aa0-d1691e21a76d" />

マイフレンドページ
<img width="976" height="651" alt="image" src="https://github.com/user-attachments/assets/4e940434-fa57-4ba2-a7f7-615797d3a864" />


## サーバー側のデータベース関係すること

メッセージ形式のカプセル化
![image](https://github.com/user-attachments/assets/6e9f2286-97e9-4ba9-94be-4c537fdf3275)

データベース内の主要なテーブル情報
<img width="1121" height="249" alt="image" src="https://github.com/user-attachments/assets/062ff5d0-f3e9-46c2-bb08-659991fe1784" />

メッセージ歴史保存
<img width="1696" height="315" alt="image" src="https://github.com/user-attachments/assets/19a5bd5c-a0fb-4474-9686-6053bc2f745e" />

本システムに関して簡単な説明は以上です。
何か質問があれば是非ISSUESしてお願いいたします

