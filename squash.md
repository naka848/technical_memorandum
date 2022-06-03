## 作業ごとsquash

まずgit _testで練習

参考：https://zenn.dev/ryouhei_furugen/articles/44bc9a179764eb  
参考：https://qiita.com/takke/items/3400b55becfd72769214
  　　　

- いずれにせよ、最新のcommitまで表示されてしまうよう

- ただ、編集するかしないかは別で決められるので、編集したいcommitだけだしたい！とこだわることはなさそう

- fixupってでてきたけど、これはなに？

  | コマンド  | 説明                                                         |
  | :-------- | :----------------------------------------------------------- |
  | p, pick   | commit を残す。こちらで指定された commit は受け身なイメージ。 |
  | s, squash | 直前の pick となっている commit に統合する。commit message も統合する。 |
  | f, fixup  | 直前の pick となっている commit に統合する。commit message は統合 “しない” 。 |

  いずれも「直前」か…

## 連番、特定のcommitをまとめる

rebaseの編集画面を出す

```
 git rebase -i HEAD~10
```

まとめたいものだけ「ｓ」にする

強制PUSH

```
git push -f origin master
```

ローカルのブランチを削除して、再度MASTERを最新状態にし、もう一度ブランチを作成

（ログの整合性をとるため）



## 離れたcommitをまとめる

参考：https://kitigai.hatenablog.com/entry/2019/05/22/003841  
参考：https://www.engilaboo.com/summarize-multiple-commits/

→これでできそうかな、と思ったのだが、ファイルの中の文字列の順番が変わってしまうしcommitできなかった

手順通り進めても、変更するファイルが多すぎてできないと言われてしまう



