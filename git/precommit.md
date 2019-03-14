### pre-commitのやり方について調査

- gitのhooksを使う
  - .git/hooksの中にある
  - pre-commit, post-commit等種類があり走るタイミングが異なる
  - 無視するとき`````$git commit --no-verify` をもちいる。
  - [参考](https://git-scm.com/book/ja/v1/Git-%E3%81%AE%E3%82%AB%E3%82%B9%E3%82%BF%E3%83%9E%E3%82%A4%E3%82%BA-Git-%E3%83%95%E3%83%83%E3%82%AF)
  - git hooksの使い方
  - あまり、プロジェクトごとには設定しない？
	-  ->templateを用意したほうがよいかも。
  - hooksファイルを修正したら`$git init`をする
  - [参考](https://qiita.com/noraworld/items/c562de68a627ae792c6c)
- autopep8を走らせる
  - 書く場所-> .git/hooks/pre-commit
  - [参考](https://qiita.com/konojunya/items/bcfa4561b9c51ef7412a) 
  - ただし、スクリプトの書き方が微妙なので、[これ](https://stackoverflow.com/questions/29738206/autopep8-in-a-git-pre-commit-how-to-automatically-recommit)
  - autopep8の[エラーコード](https://github.com/hhatto/autopep8/)
- .giit/フォルダはGit管理ができないので、各自でpre-commitの設定を行う必要がある
  - [参考](https://qiita.com/cathcheeno/items/cb5df2eef1e655f089b7)
  - [gitの運用について](https://labs.gree.jp/blog/2011/03/2885/)

