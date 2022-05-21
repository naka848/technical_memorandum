- [共通](#共通)
  - [深呼吸](#深呼吸)
- [Laravel](#laravel)
  - [エラーログをみる](#エラーログをみる)
  - [バージョンを確認する](#バージョンを確認する)
  - [どのバージョンがいいの？](#どのバージョンがいいの)
    - [php](#php)
    - [node](#node)
  - [autoload](#autoload)
  - [Cartのsourceの編集ができない](#cartのsourceの編集ができない)
# 共通
## 深呼吸

- 怖いのは、焦って作業してどんどん迷路に迷い込むこと
- まずは現状把握
- その上で、適切な対処法を検索
- 調べたコマンドの意味をよく調べる
- 実行に不安があれば、周囲に相談
- ここまでできて、やっと実行！

---

# Laravel

## エラーログをみる

1. [vscode]  
フォルダorファイルの上で右クリック>Explorerで開く
2. [Explorer]  
app>storage>logs>最新のファイル

---

## バージョンを確認する

- なんかおかしかったら、バージョンが違うせいかも
  - ex)nodeのバージョンをあげた結果Huskyが動かなくなった

---

## どのバージョンがいいの？

### php
- いろいろ変更することはあっても、最終的に以下のように戻しておく
  - synergy …php5.6.40
  - cart    …php7.3
- compoesrは1でOK（少なくとも速水さんの環境では問題は起きていない）

### node
- nodeとnpmは基本的には同じバージョンにする

---

## autoload

Laravelでファイルを作成したら、ファイルを自動で読み込む仕組み(オートロード機能)を利用してクラス名と名前空間をマッピングする！

1. [terminal]  
まずはcomposerがあるか確認
```
$ which composer  
/usr/local/bin/composer
```

2. [terminal]  
composerがあれば、バージョンを確認
```
$ composer --version  
Composer 2.3.0 dropped support for PHP <7.2.5 and you are running 5.6.40, please upgrade PHP or use Composer 2.2 LTS via "composer self-update --2.2". Aborting.

訳:Composer 2.3.0 で PHP <7.2.5 がサポートされなくなり、5.6.40 が動作している場合は PHP をアップグレードするか、"composer selfupdate --2.2" で Composer 2.2 LTS を使ってください。中止します。
```

4. [terminal]  
phpもバージョンを確認
```
$ php --version
PHP 5.6.40 (cli) (built: May  6 2022 09:54:11) 
```

5. [terminal]  
インストールされているphpのバージョンを確認
```
$ phpenv versions  
  system
* 5.6.40 (set by /home/kpu0570/.php-version)
```

6. [terminal]  
phpのバージョンの切り替え
（local…カレントディレクトリのみ変更）  
変更理由:5.6.40では、composer self-updateが使えないため
```
$ phpenv local system  
system
```

7. [terminal]  
変更後のphpのバージョンを確認
```
$ php --version  
PHP 7.4.3 (cli) (built: Mar  2 2022 15:36:52) ( NTS )
```

8. [terminal]  
composer本体のバージョンを下げる
```
$ sudo composer self-update --1 
Warning: You forced the install of 1.10.26 via --1, but 2.3.5 is the latest stable version. Updating to it via composer self-update --stable is recommended.
Upgrading to version 1.10.26 (1.x channel).

訳:警告 1.10.26 を --1 で強制的にインストールしましたが、2.3.5 が最新の安定版です。composer self-update --stable でアップデートすることをお勧めします。
バージョン 1.10.26 (1.x チャンネル) にアップグレードしています。
```
- composer version 1 は非推奨なので警告がでる。
- ただ、version 1 じゃないとできない作業がもろもろあるので、version 1 にしたまんまでOK（デプロイに今のところ問題はなさそう）


9. [terminal]  
◎１番やりたかったこと！！  
処理に必要なPHPファイルを自動で読み込む
```
$ composer dump-autoload  
Generating autoload files
Carbon 1 is deprecated, see how to migrate to Carbon 2.
https://carbon.nesbot.com/docs/#api-carbon-2
    You can run './vendor/bin/upgrade-carbon' to get help in updating carbon and other frameworks and libraries that depend on it.
Generated autoload files
```

10. [vscode]  
新たに作成されたファイルを確認する  
- ClassLoader.php 
  - ファイルごと変更を取り消す（Discard Changes）
- autoload_classmap.phpとautoload_static.php  
  - 'Composer\\InstalledVersions'に関する記述の部分が削除されてしまうので、変更点を含む範囲を選択して右クリック>Revert Selected Ranges(元に戻す)


11. [terminal]  
phpのバージョンを元に戻す
```
$ phpenv local 5.6.40
5.6.40
```

12.  [terminal]  
phpのバージョンを確認
```
$ php --version
PHP 5.6.40 (cli) (built: May  6 2022 09:54:11) 
```

---

## Cartのsourceの編集ができない

- 原因：storageへのアクセス権限がない
  - storageディレクトリー
    - コンパイルされたBladeテンプレート、ファイルベースのセッション、ファイルキャッシュなど、フレームワークにより生成されるファイルが保存される。storageへのアクセス権限がないと、各変更が記録できない。

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