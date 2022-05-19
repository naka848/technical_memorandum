
# つまづきメモ

## Cartのsourceの編集ができない

エラーメッセージ

```
'AutoRecept.php' を保存できませんでした。ファイル 'vscode-remote://wsl+ubuntu/home/kpu0570/king/cart/Source/app/Services/Order/AutoRecept.php' を書き込むことができません (NoPermissions (FileSystemError): Error: EACCES: permission denied, open '/home/kpu0570/king/cart/Source/app/Services/Order/AutoRecept.php')
```

権限を確認(Windows側)

```sh
kpu0570@kp-2014:~/king/cart$ ls -lah
drwxr-xr-x 20      82      82 4.0K Apr 19 11:28 Source
```

権限の変更(Windows側)

```sh
kpu0570@kp-2014:~/king/kp$ sudo chmod -R 775 Source
kpu0570@kp-2014:~/king/kp$ sudo chown -R kpu0570:kpu0570 Source
kpu0570@kp-2014:~/king/kp/Source/app$ sudo chown -R www-data:www-data storage
```

---

## テスト環境について

- 本番環境
- テスト環境
    - ローカル
    - AWS EC2内の仮想サーバ（他の方にみていただくとき）

---

## サンプル

- 無料サンプル
- サンプルメール便（商品と別に代理店さんなどに送るもの）

---

## コードの辿り方

- 検証で触りたい部分のコードを読む
- 分からない変数や単語は定義されている箇所を読む（全文検索）












