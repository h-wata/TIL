# pluginの紹介

## vim-fugitive.vimコマンド紹介
- ```:Gwite``` -> git add
- ```:Gstatus``` -> git status
- ```:Gcommit``` -> git commit
- [参考](https://doruby.jp/users/kurita/entries/fugitive-vim%E3%81%A7vim%E4%B8%8A%E3%81%A7git%E6%93%8D%E4%BD%9C%E3%82%92%E3%81%97%E3%82%88%E3%81%86%EF%BC%81)

## previmOpenでハマった時
- 現象
  - previmOpenで開こうとするとVScodeが開いてしまった
  - `$ xdg-mime default browser.desktop text/heml`でブラウザーで開くように修正したら治った
  - previmopenするときはIndex.htmlを開く
  - [参考](https://wiki.archlinux.jp/index.php/Xdg-open#.E3.83.87.E3.83.95.E3.82.A9.E3.83.AB.E3.83.88.E3.81.AE.E3.83.96.E3.83.A9.E3.82.A6.E3.82.B6.E3.82.92.E8.A8.AD.E5.AE.9A)
