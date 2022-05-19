# エラー戦記

## エラーログをみる

1. [vscode]  
フォルダorファイルの上で右クリック>Explorerで開く
2. [Explorer]  
app>storage>logs>最新のファイル

---

## autoload

Laravelで名前空間を指定したのに、Class Not Foundがでた。

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
```
訳:Composer 2.3.0 で PHP <7.2.5 がサポートされなくなり、5.6.40 が動作している場合は PHP をアップグレードするか、"composer selfupdate --2.2" で Composer 2.2 LTS を使ってください。中止します。

3. [terminal]  
$ which composer  
まずはcomposerがあるか確認

4. [terminal]  
$ which composer  
まずはcomposerがあるか確認

5. [terminal]  
$ which composer  
まずはcomposerがあるか確認

6. [terminal]  
$ which composer  
まずはcomposerがあるか確認

7. [terminal]  
$ which composer  
まずはcomposerがあるか確認

8. [terminal]  
$ which composer  
まずはcomposerがあるか確認