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
docker build -t takuver4/python_dev:python366 .
```

### docker run

```cmd
docker run -it -v c:\home\sip:/work/src takuver4/python_dev:python3_venv bash
```

## Tips

### ~/.bash_profile に関する注意点

```docker run``` では **ログインシェル** が立ち上がるのではなく **対話型シェル** が立ち上がる。
そのため、~/.bash_profile は実行されない。これを解決するには ```docker run``` に
```--login``` オプションを付ける必要がある。

なお、```--login``` オプションを付けることのデメリットは不明である。
しかし標準で有効になっていないことから、何らかの弊害があるのではと推測している。


### VS Code の変更

* terminal.integrated.commandsToSkipShell in your setting and remove "workbench.action.quickOpen" from the list.
* https://qiita.com/Yuki-Inoue/items/60ec916383025160fbb8#_reference-a2d9244a6c4496f4df05

```json
{ "key": "alt+j",              "command": "workbench.action.terminal.focus",
                               "when": "editorTextFocus"},
{ "key": "alt+k",              "command": "workbench.action.focusFirstEditorGroup",
                               "when": "terminalFocus"}
```