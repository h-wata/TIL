### Dockerでやりたいこと

- Buildできるかどうかの試験- 
  - melodicでのBuild試験
  - Rosdep installの試験
- 動作していた環境の保存
  - roll backが簡単
  - https://qiita.com/niisan-tokyo/items/88a53a1b4aa7ad60723e
  - docker repo
-  Updateの仕組みづくり？？
- Dockerでやるの？ 
- deｂパッケージの作成方法
  - https://eng-entrance.com/linux-package-deb-create
- https://blog.cybozu.io/entry/2016/05/16/111500

github ssh key 登録
https://qiita.com/xiaotuanzi/items/52f72ac4a09c7efb47b3

- dockerは環境構築が大事、ROSでは自分達のパッケージを落としてきてrosdep updateを行い、依存パッケージを入れたうえで、rosフォルダーを削除する。そして、docker runするときにROSフォルダをマウントすれば、Buildできる状況になる
  - https://hub.docker.com/r/wkentaro/jsk_apc/dockerfile/
