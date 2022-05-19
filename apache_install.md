# Apache

## 1.インストール
「apt」と「apt-get」があるが、「apt」の方がモダンなコマンドなのでこちらを使うといい

```
sudo apt update
sudo apt install apache2
```

---

## 2.ファイアウォールの調整
ufwアプリケーションプロファイルを一覧表示

```
sudo ufw app list
```

実行結果
```
Output
Available applications:
  Apache
  Apache Full
  Apache Secure
  OpenSSH
```

- Apache: このプロファイルは、ポート80（通常の暗号化されていないWebトラフィック）のみを開きます。
- Apache Full: このプロファイルは、ポート80（通常の暗号化されていないWebトラフィック）とポート443（TLS/SSL暗号化トラフィック）の両方を開きます。
- Apache Secure: このプロファイルは、ポート443 （TLS/SSL暗号化トラフィック）のみを開きます。

設定したトラフィックを許可しながら、最も制限の厳しいプロファイルを有効にすることをお勧めします。現時点ではまだ、サーバーにSSLを設定していないため、ポート80のトラフィックのみを許可すればよいでしょう。

```
sudo ufw allow 'Apache'
```

変更の確認

```
sudo ufw status
```

### ＜つまづいたところ＞

「状態: 非アクティブ」になる場合は、ufwを有効化する
```
ufw enable
```

---

## Webサーバーの確認

```
sudo systemctl status apache2
```

理想の結果

```
Output
● apache2.service - The Apache HTTP Server
     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
     Active: active (running) since Thu 2020-04-23 22:36:30 UTC; 20h ago
       Docs: https://httpd.apache.org/docs/2.4/
   Main PID: 29435 (apache2)
      Tasks: 55 (limit: 1137)
     Memory: 8.0M
     CGroup: /system.slice/apache2.service
             ├─29435 /usr/sbin/apache2 -k start
             ├─29437 /usr/sbin/apache2 -k start
             └─29438 /usr/sbin/apache2 -k start
```


### ＜つまづいたところ＞
- systemd が PID1 で動作していない

```
$ systemctl
System has not been booted with systemd as init system (PID 1). Can't operate.
Failed to connect to bus: Host is down
```

参考サイト

https://snowsystem.net/other/windows/wsl2-ubuntu-systemctl/#

- genieインストールが必要

```
monaka@DESKTOP-5QEHRDB:~/genie$ genie -s
genie: コマンドが見つかりません
```

最初mac向けの記事を読んでいて、makeコマンドがない！！とあたふた笑

参考サイト

https://qiita.com/sakai00kou/items/0b401faf6dd72ad63d87

---

## 3.Webサーバーの確認
systemd initシステムでサービスが稼働中であることを確認

```
sudo systemctl status apache2

```

結果：OKな場合の例

```
Output
● apache2.service - The Apache HTTP Server
     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
     Active: active (running) since Thu 2020-04-23 22:36:30 UTC; 20h ago
       Docs: https://httpd.apache.org/docs/2.4/
   Main PID: 29435 (apache2)
      Tasks: 55 (limit: 1137)
     Memory: 8.0M
     CGroup: /system.slice/apache2.service
             ├─29435 /usr/sbin/apache2 -k start
             ├─29437 /usr/sbin/apache2 -k start
             └─29438 /usr/sbin/apache2 -k start
```

サーバーのIPアドレスを取得
```
hostname -I
```

インターネット上の別の場所から見たパブリックIPアドレスの確認方法
```
curl -4 icanhazip.com
```

ブラウザにアクセス
```
http:// さっき確認したサーバーのIPアドレスを入力
```



---

続き：

参考サイト

https://www.digitalocean.com/community/tutorials/how-to-install-the-apache-web-server-on-ubuntu-20-04-ja


---

ついでにLaravelのインストールについて

Apacheの設定、権限変更まではしたんだけど、nanoエディタでlaravel.confの設定をいじるのはやってない

参考サイト

https://ubunlog.com/ja/laravel-framework-php-ubuntu/#Instalar_Laravel