# 2022年システム課研修

## 単語

- FHS
  - Filesystem Hierarchy Standard
  - Hierarchy(ハイラルキー、ヒエラルキー)…階層

## ディレクトリ構造

- dev
  - device（デバイス）
- srv
  - Service

## rm

- ゴミ箱の概念がない
- 削除したら、復活ができないので消去するときはめちゃくちゃ気を付ける！

## recuresiveオプション

- -R
- recuresive「再帰的」
## tar

- 圧縮（アーカイブ）
$ tar cvf tarファイル名 アーカイブ対象ディレクトリ
  - c : コンプレス
- 解凍（展開）
$ tar xvf tarファイル名
  - x : エクストラクト

- tar.gz
  - tarファイルのジージップ圧縮

## chmod

- r 4 …読み取り
- w 2 …書き込み
- x 1 …実行

- 3桁の内訳
  - 所有者の権限　グループの権限　その他の権限

## ディスク管理

- du
  - ディスク（Disk）使用量（Usage）を表示する
- df
  - ディスク（Disk）の空き（Free）容量を表示する

## ping

- 今どれくらい遅延があるか調べるときに使う
  - 例）当社のルーターでためす
    - ping 192.168.2.1

## ifconfig
- IPアドレスのチェック
- どの仮想アダプタがあるのかのチェック

## プロセス

- Linuxのプロセス
  - Linuxで実行中のプログラムのこと
  - 自動的に起動しているものや、シェルからコマンドで実行されるものも含む
  - 一つのプログラムから複数のプロセス(プログラム)が生成されることも多くある
  - サーバ関係のプロセスの場合「デーモン」といわれ、基本的にユーザから手続きのもとに「終了してくれ」といわないかぎり稼動し続ける

## ICMP通信

- Internet Control Message Protocol 
- TCP/IPでネットワークの疎通がされているノード（サーバー、ネットワーク機器、PCなど）間で、通信状態の確認をするために使われるプロトコル

## httpd

- HTTPのデーモン(d)
- Linuxとかにおける常駐プログラム（デーモン）のひとつ
- Webサーバとしてのお仕事をしている
- Red Hat Enterprise Linux では、httpd パッケージが Apache HTTP Server を提供します

## デーモン

- UNIX系OS（MacとかLinuxとか）における常駐プログラムの呼び名

## 標準入出力

- ファイルディスクリプタ
  - 標準入力 : 0
  - 標準出力 : 1
  - 標準エラー出力 : 2
- 「>」リダイレクト 
  - シェルの結果を出力する場所を指定可能
- 「&ファイル・ディスクリプタ」
  - 出力先などを特定のファイルディスクリプタに送る

## Vim

- ビジュアルモード
  - 範囲を選択して、その範囲に対してなにか操作を行うことができる


## SSH サーバーの構築

- [CentOS]公開鍵の作成
$ssh-keygen -t	rsa

- [CentOS]権限の変更
$chmod 600	~/.ssh/id_rsa

- [CentOS]公開鍵、秘密鍵の２個が作成されたことを確認
[kpu0570@localhost ~]$ ls .ssh
id_rsa  id_rsa.pub
  
- [ローカル]SSH接続ができることを確認
ssh kpu0570@192.168.4.2

- [CentOS]SSH接続を確認できたらローカルに戻る
  exit

- [ローカル]CentOSで作成した秘密鍵を取りだす
  CentOSの.sshフォルダの中身をローカルのルートディレクトリ直下にコピー
  scp kpu0570@192.168.4.2:~/.ssh ./

　- scpコマンド
  　- リモートマシンとローカルマシン、あるいはリモートマシン同士でファイルをコピーする際に使用するLinuxのコマンド
  
- [CentOS]SSHでサーバーに入る
ssh kpu0570@192.168.4.2

- [CentOS]ホームディレクトリの.sshフォルダ配下に「authorized_keys」ファイルを作成
- cd ~/.ssh/
　touch authorized_keys

- [CentOS]公開鍵を「authorized_keys」ファイルへおろす
  - cat:ファイルを連結して標準出力に出力する」 
  - cat id_rsa.pub >> authorized_keys

- [CentOS]SSH接続をぬける
- exit

- [ローカル]秘密鍵をつかって、SSH接続を行う
 ssh -i ~/id_rsa kpu0570@192.168.4.2

  - ssh [オプション] ホスト名 [コマンド]
    - -i 秘密鍵ファイル