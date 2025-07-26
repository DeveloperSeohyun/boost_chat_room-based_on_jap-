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


# 运行界面
注册界面
ログイン画面
![image](https://github.com/user-attachments/assets/5718d504-819e-4868-a5ab-e11b1408c438)

服务器接受情况
サーバーのバックエンドの受け入れ
![image](https://github.com/user-attachments/assets/595d91c6-eaa8-4b81-acc8-1ba9c7856d1e)

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





