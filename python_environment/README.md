# Python Environment

## 概要

Python の開発環境を Docker上に構築する。
当初は WSL 上での構築を検討していたが、RedHat系 の WSL が無かったので断念した。

## 必要なもの

* Docker for Windows
  * Firewall の解除でハマったがググって解決したよ。

## 使用コマンド

### docker build

```cmd
docker build -t takuver4/python_dev:python36_colour13_ctl --no-cache .
```

### docker run

```cmd
docker run -it -v c:\home\sip:/work/src -e DISPLAY=10.0.75.1:0.0 --rm takuver4/python_dev:python36_colour13_ctl bash
```

## Todo

* ユーザーアカウント作成
  * rootユーザーじゃなくて一般ユーザーで動かすようにする

## Tips

### ~/.bash_profile に関する注意点

```docker run``` では **ログインシェル** が立ち上がるのではなく **対話型シェル** が立ち上がる。
そのため、~/.bash_profile は実行されない。これを解決するには ```docker run``` に
```--login``` オプションを付ける必要がある。

なお、```--login``` オプションを付けることのデメリットは不明である。
しかし標準で有効になっていないことから、何らかの弊害があるのではと推測している。

### GUIに関して

* Qiita の [Docker for WindowsでGUI(sshでX11転送しない方法)](https://qiita.com/kfjt/items/369c48686c849c0042a9)
を~~丸パクリ~~参考にして構築
* VcXsrv の起動は同ディレクトリにある config.xlaunch をダブルクリックで行ける（要ソフト本体のインストール）
* Windows側のHiDPI設定を無効化するには、vcxsrv.exe だけでなく xlaunch.exe も設定が必要


### VS Code の変更

* terminal.integrated.commandsToSkipShell in your setting and remove "workbench.action.quickOpen" from the list.
* https://qiita.com/Yuki-Inoue/items/60ec916383025160fbb8#_reference-a2d9244a6c4496f4df05

```json
{ "key": "alt+j",              "command": "workbench.action.terminal.focus",
                               "when": "editorTextFocus"},
{ "key": "alt+k",              "command": "workbench.action.focusFirstEditorGroup",
                               "when": "terminalFocus"}
```