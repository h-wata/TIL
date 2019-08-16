# xdg-openで開くブラウザの設定

## xdg-open 
[参考](https://wiki.archlinux.jp/index.php/Xdg-open)
確認方法
```
$ xdg-mime query default text/html
$ xdg-mime query default x-scheme-handler/http
$ xdg-mime query default x-scheme-handler/https
```
設定方法
```
$ xdg-mime default google-chrome.desktop text/html
$ xdg-mime default google-chrome.desktop x-scheme-handler/http
$ xdg-mime default google-chrome.desktop x-scheme-handler/https
```

- このとき、開いたページが空白のままで遷移しなかった場合
    - /usr/share/applications/google-chrome.desktop内のExecのオプションで%Uをつける
    - もしもここを変えても変わらない場合は、~/.local/share/applications/google-chrome.desktopを見て、同様の編集を行う
    - [参考](https://askubuntu.com/questions/540939/xdg-open-only-opens-a-new-tab-in-a-new-chromium-window-despite-passing-it-a-url)
