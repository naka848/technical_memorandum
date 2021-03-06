# 業務知識

## サンプル

- 無料サンプル
- サンプルメール便（商品と別に代理店さんなどに送るもの）
  
---

## ステータス

- Synergy
  - 注文完了…手動で変更必要（Amaryllis）
  - 受付完了…自動受付対象はすぐこれになる
---
## marge-staging
- Amaryllis、テスト環境の名前を設定するやつ
- 秋田さんがつくったので、困ったら秋田さんにきく


---
## データ保存場所
- AWS(クラウド)
- 社内サーバ（オンプレ）
  - QNAP、他

### 社内サーバ
- Share
  - 本社、新宿店共有サーバ

---
## 合同会社キューブ・エス
- 中村さん
- 独立後おひとりでやられている

---

## IPアドレスの重複

- 問題
  - IridesseのIPアドレス（192.168.2.85）がどこかにとられてインターネットに接続が出来なくなった
- 原因
  - 現場の監視カメラのIPアドレスが切り替わり、結果重複
- 調査
  - システム課：社内のPCのIPアドレスを一機ずつ確認
  - 速水さん：アクティブディレクトリから社内のIPアドレスの一覧が確認できる。端末名先頭24ビットからメーカー名が予想できるので、アトムならアトムだとわかる
  - 総務（矢倉さん）、ロジ（岩田さん）：アトム（監視カメラ）を管理する端末から確認
- 対応
- IPアドレスが重複していた端末のIPアドレスを変更
  - IridesseのPCからイーサネットを確認
    - プロパティ＞インターネット＞プロパティ
      - IPアドレス再入力（スクショとって変更前の状態をメモ）
    - 再起動
    - プロパティ＞インターネット＞プロパティ＞終了時に設定を検証する
      - 入力した内容と設定があっているか確認をしてくれる

- 所感
  - 現場PCいっぱいある！！
  - 閉じているノートパソコンや、タブレット端末もあるので注意する

- 自分のIPアドレスの確認方法
- コマンドプロンプトにて
```
C:\Users\kpu0570>ipconfig
```
結果:ここをみる！
```
Ethernet adapter イーサネット:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::5bd:2097:7116:56d9%39
   IPv4 Address. . . . . . . . . . . : 192.168.2.250
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.2.1
```
---

## 課題

- SEO改善：ラクスルのように、価格表示を分かりやすく改定したい
  - コンサル会社：エスピー（ラクスル推し）
  - ページ数いっきに増える
  - アクセスは4-5倍になるかも（サーバー耐えられるか？）   
- スマホ・タブレットからも注文できるようにしたい
- 不備率は今でも出せるが、注文確認時などに出したり、リアルタイムで出せないか
  - 顧客ごとグループバイでグルーピングして集計
- 見本画像の表示(年間100万ほどかかりそう)
  - いわたさんと相談して、画質をおとして実現できないか？
- 面付の自動化
  - こぎんさんはやる気、費用対効果は高そう、でも１０００万くらいかかりそう
  - ベンダーの選定も必要
- 電子帳簿保存法・適格請求書対応
- キューサーバー、メール送信・ファイル送信でしか使っていない
  - AWSで置き換え可能
- 営業さんから欲しいデータ要望頻繁に来る
  - 営業側でも確認できるようにデータの整理・保管方法の見直し
- サイトの更新できる？
  - あたらしいやつに全部置き換え(ビッグバン)
  - パーツごと置き換え
- ヘビーユーザーの人とAPI連携するには？
  - 今でも対応はできる
  - 外部に公開するとセキュリティホールになりかねるので、やるなら手間をかけてしっかりやらねば


---
## 謎メモ

- レッドマインでキーワード検索「SSL」

---

## メール

- marketing-adminメールアドレス、私は知らなくても大丈夫