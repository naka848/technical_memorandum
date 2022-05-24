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