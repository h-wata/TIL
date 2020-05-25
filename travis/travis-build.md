# localでtravisを実行してみた

## dockerでの実行
docker hubも覗いてみたがどのDockerをPullしてくればいいかわからなかった
既存の記事に出てくるBranchは結局14.04しかなく、Ubuntu 16.04で実行できるものを見つけられなかった
また、DOCKER_BUILDKIT=1をしたときのUIDとGIDはrootがデフォルトと言う事がわかっていなかった。
Dockerの中でDockerをLaunchする方法がわからなかった

                                                                               

## travis-buildリポジトリを再度見てみた。

https://github.com/travis-ci/travis-build#use-as-addon-for-travis-cli
githubのREADME.mdを改めてみたいたらローカルで実行できそうだったので試した

### ハマったポイント
```
git clone https://github.com/travis-ci/travis-build
cd travis-build
mkdir -p ~/.travis
ln -s $PWD ~/.travis/travis-build
gem install bundler   # -> gem install bundler -v 1.7.3じゃないとバージョン違いで下記コマンド実行できなかった
bundle install --gemfile ~/.travis/travis-build/Gemfile
bundler binstubs travis
```

matrixは無視されるので、環境変数は自ら`export`すべき

また、git clone するとき`https`を使うので、面倒な場合は`build.sh`の中身を適宜置換する
`--branch=''`も指定されているので変えたいときは修正する
