# bashをupgradeしたらlog in loopしてしまった

## 経緯
`bashtop`というソフトを試そうとしたときにrequimentとして、｀bash (>4.4)｀ だった。
そのため、bashをUpgradeした。
[手順](https://qiita.com/takahirono7/items/5dd99bcc4202d289103b)に従って実行して、`bash 4.4`が入った。
しかしながら、`/bin/bash`が消えていた->これが悲劇の始まりだった

## 現象
- まずはターミナルを開いても、bashrcが正しく読み込まれず、`/bin/sh`が立ち上がるようになった
- `/bin/bash` not foundが表示されるようになった
- 再起動すれば直るかと再起動した -> 最悪手
- 再起動したら、loginしようとしてもGUIはもちろん、tty1~6のターミナルにも入れなくなった
- recovery modeも試したがmenuにも行かず

## 復帰方法
### 参考リンク
 https://serverfault.com/questions/451528/how-to-recover-from-a-deleted-bin-bash
 このページを参考にした。
 再起動前であれば、`ln -s /bin/sh /bin/bash`などしてお茶を濁しつつ、`sudo apt install --reinstall bash`なども出来たが、すでに再起動済み
 そのため、`archi-linux`のライブUSBを作成し、ライブで起動しリンクを貼った。
   ```
    $ mkdir /mnt/share
    $ mount /dev/nvme1p6 /mnt/share
    $ ls /mnt/share/bin/bash # not found
    $ cd /mnt/share
    $ ln -s ./bin/sh ./bin/bash
    $ reboot
   ```
 最終的には、`ln /usr/local/bin/bahs /bin/bash`を貼り実行するようにした
 ちなみにlogin loop担った理由は、`/etc/passwd`にlogin shellが`/bin/bash`に定義されているから
 ```/etc/passwd
 gisen:x:1000:1000:gisen,,,:/home/gisen:/bin/bash
 ```
 これを変更するときは、`/etc/shells`に`/usr/local/bin/bash`を追加して、
 `chsh -s /usr/local/bin/bash`を実行する必要がある

 困っているときに下記ページを見つけられなかったけど、こっちのほうが簡単そう
 https://qrunch.net/@alshezka/entries/ppMx8bdWLAkKj7UW?ref=qrunch

