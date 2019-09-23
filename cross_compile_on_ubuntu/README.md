# Cross Compile Environment

## 概要

Windowsのバイナリをビルドする環境をUbuntu上に構築する。

## 使用コマンド

### docker build

```cmd
docker build -t takuver4/cross_compile:rev01 --no-cache .
```

### docker run

```cmd
docker run -it -v c:\home\sample_code:/work/src -e DISPLAY=10.0.75.1:0.0 --rm takuver4/cross_compile:rev01 bash
```
