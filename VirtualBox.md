## VirtualBoxをダウンロード

- 公式サイト
    - https://www.virtualbox.org/wiki/Downloads
    - Windows hosts

## CentOSのISOファイルをダウンロード

- 公式サイト
    - https://www.centos.org/download/
    1. CentOS Linux>x86_64
    2. 近そうな地域のURLをクリック
    3. 「CentOS-7」「DVD」「iso」と書いてあるファイルをダウンロード
    
## VirtualBoxにCentOSをインストール

- https://qiita.com/tamago3keran/items/260899458959d3214dcf

- 設定
  - ネットワーク > アダプター１
  - 割り当て：ブリッジアダプター
  - 名前：ASIX～

- アカウント
  - rootパスワード：King7542!
  - ユーザー名：kpu0570
  - パスワード：King7542!

### CentOS設定
- 一般
  - タイプ：Linux（CentOSが動くOSを指定する。WindowsではなくLinuxにする）
  - バージョン：Red Hat(64bit)
- システム
  - メインメモリー：2048MB（1024MBじゃなきゃ動かないという説もあるが、そんなことはないらしい。速水さん談）
- ディスプレイ
  - ビデオメモリー：27MB（27MB以上にしろ！と言われたので変更。もともとは16MB）
- ストレージ
  - IDE
    - CentOS-7-x86_64-DVD-2009.iso
      - 最新版で問題なかった
  - SATA：CentOS7.vdi
    - 何度もインストールを繰り返した結果容量パンパンに。→消去してOK
    - 本体の場所：C:\Users\kpu0570\VirtualBox VMs\CentOS7
    - 中身は立ち上げないと見れない

## ネットワーク設定

- Host Only Adapter
  - 内部のネットワークと通信
  - 内部ネットワークに加え，ホストマシンとの通信も可能なネットワーク．
  - ホストOS上に作られる仮想のネットワークアダプター
  - この仮想アダプターは、対応する仮想スイッチに接続されます
  - そして作成した仮想マシン側でも同じ仮想スイッチに接続するように設定することで、ホストOSとゲストOSが直接通信できるようになります
- NAT
  - 外部のネットワークと通信


- 現状確認
- VirtualBox>CentOS7>ネットワーク

- 参考：https://blog.proglus.jp/3315/

- VirtualBox Host-Only Ethernet Adapter #2 追加
  - IPv4アドレス：192.168.4.1
  - IPv4ネットマスク：255.255.255.0

- enp0s8
  - IPv4アドレス：192.168.4.2
  - これはホストオンリーアダプタ？

### SSH接続
- CentOS起動
- シェルスクリプトからアクセス
```
ssh kpu0570@192.168.4.2
```

### Linuxマシンのシャットダウン

- シェルスクリプトでLinuxマシンと接続してる状態
```
shutdown -h now
```
- シェルスクリプトでローカルにいる状態
```
exit
```