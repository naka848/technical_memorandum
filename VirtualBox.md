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

- 不安な設定（これでいいのかな？）
  - ネットワーク > アダプター１
  - 割り当て：ブリッジアダプター
  - 名前：ASIX～

- 最終的な設定
  - メモリサイズ：1024MB
  - 光学ドライブ：CentOS-7-x86_64-DVD-1810
  - コントローラーSATA：新規ストレージの割り当て追加＞ハードディスク

- アカウント
  - rootパスワード：king0000
  - ユーザー名：admin
  - パスワード：king0000