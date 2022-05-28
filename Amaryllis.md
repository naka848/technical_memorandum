## アカウント
- 本番環境・テスト環境共通

---

## setting.json

- 置き場所
  - Mac
    - /Users/kpu0562/Library/Application Support/Amaryllis/setting.json
  - Windows
    - 

- 本番環境向け設定をテスト環境向け設定に変更する

  - 本番環境向け設定
    - s3>bucket
```sh
"aws": {
		"s3": {
			"bucket": "kingprinters-data",
		},
},
```

    - synergy>baseURL
   

```sh
"synergy": {
		"baseURL": "https://synergy.kingprinters.com/",
},
```


  - テスト環境向け設定
    - s3>bucket
```sh
"aws": {
		"s3": {
			"bucket": "dev-kingprinters-data",
		},
},
```
    - synergy>baseURL
```sh
"synergy": {
		"baseURL": "https://synergy-planning.kingprinters.com/",
},
```

---

## 環境を起動するながれ

- 本番環境にする→本番環境用の設定をみにいく（アプリに組み込まれていて、全員に配布されている）
- ローカル環境にする→setting.jsonをみにいく
  - だからsetting.jsonの設定の変更によって、テスト環境にはいれるようになる！

---

## Manualの読みかた

- ローカルに別途DBを作成している方もいる
- その場合、設定がかわってくるので、ローカルのDBに接続しているのか共通のDBに接続しているのか注意してみることが必要

---

## 環境の切替方

- 以下コマンド入力
(Windows)
```sh
kpu0570@kp-2014:~/workspace/Amaryllis$ bash scripts/switchenv.sh

変更したい環境を選択してください。
1) prod
2) dev
3) synergy-docker
4) exit
```
(Mac)
```sh
kpu0570@kp-2014:~/workspace/Amaryllis$ npm run switchenv
```

1) prod　…　本番環境
2) dev　…　テスト環境

- テスト環境をひらく場合

```sh
#? 2
変更する環境: dev
Synergy のステージング環境を設定します。\nmanage-staging の -n オプションで指定した文字列を入力してください。
```
閲覧だけの場合は「planning」を入力
```sh
staging-name: planning
Synergy のステージング環境のサブドメインを "synergy-planning" で設定します。
環境を変更しました。
```
※内容を変更したり、synergyとやりとりする場合は、AWSのEC2インスタンスを立ち上げ、その名前で入るようにする！