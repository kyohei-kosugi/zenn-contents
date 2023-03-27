---
title: "localでpysparkの簡易環境構築" # 記事のタイトル
emoji: "🐍" # アイキャッチとして使われる絵文字（1文字だけ）
type: "tech" # tech: 技術記事 / idea: アイデア記事
topics: ["python", "Spark"] # タグ。["markdown", "rust", "aws"]のように指定する
published: true # 公開設定（falseにすると下書き）
---
## はじめに
社内でSpark関連の基礎知識をまとめたblogを書くに当たって、RDDを実際に作成しながら試したかったのでlocalでpysparkの環境構築。
ただ、調べていると色んなやり方があって少しごちゃごちゃしていたので、もっとも簡単な方法を自分の整理のために残しておきます。（今後環境が変わった時とかにすぐ使えるように）

## 環境
今回は以下の環境でpysparkをダウンロードします。
事前にpythonとjavaのインストールが必要です。（javaが必要な理由はApache Sparkが動くのに必要なため。）
pipがインストールされてない場合はpythonのインストール後に行なってください。pipのインストールがうまくいかない方は下記の記事を参考にしてみてください。
[pythonコマンドが使えない 〜zsh: command not found: pythonの解消〜](https://zenn.dev/otohbk_ky/articles/b9b7d26255db78)
```
$ python3 -V
Python 3.10.4

$ java -version
openjdk version "18.0.2.1" 2022-08-18
OpenJDK Runtime Environment Temurin-18.0.2.1+1 (build 18.0.2.1+1)
OpenJDK 64-Bit Server VM Temurin-18.0.2.1+1 (build 18.0.2.1+1, mixed mode, sharing)
```

## pysparkのインストール
Dockerを使用したり、Apache Sparkをダウンロードしたり方法はいくつかありますが、今回は簡易的にpipを使用します。
```
$ pip install pyspark
Collecting pyspark
  Downloading pyspark-3.3.2.tar.gz (281.4 MB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 281.4/281.4 MB 4.4 MB/s eta 0:00:00
  Preparing metadata (setup.py) ... done
Collecting py4j==0.10.9.5
  Downloading py4j-0.10.9.5-py2.py3-none-any.whl (199 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 199.7/199.7 kB 3.9 MB/s eta 0:00:00
Building wheels for collected packages: pyspark
  Building wheel for pyspark (setup.py) ... done
  Created wheel for pyspark: filename=pyspark-3.3.2-py2.py3-none-any.whl size=281824024 sha256=d4e3cf53d9e4fcd8a555986c393d545f5c01b0d85409cb76e8900a370da2869a
  Stored in directory: /Users/k_kosugi/Library/Caches/pip/wheels/89/d6/52/1178e354ba2207673484f0ccd7b2ded0ab6671ae5c1fc5b49a
Successfully built pyspark
Installing collected packages: py4j, pyspark
Successfully installed py4j-0.10.9.5 pyspark-3.3.2
WARNING: There was an error checking the latest version of pip.
```
pysparkを実行します。
```
$ pyspark
Python 3.10.4 (v3.10.4:9d38120e33, Mar 23 2022, 17:29:05) [Clang 13.0.0 (clang-1300.0.29.30)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
Setting default log level to "WARN".
To adjust logging level use sc.setLogLevel(newLevel). For SparkR, use setLogLevel(newLevel).
23/03/27 17:39:10 WARN NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
Welcome to
      ____              __
     / __/__  ___ _____/ /__
    _\ \/ _ \/ _ `/ __/  '_/
   /__ / .__/\_,_/_/ /_/\_\   version 3.3.2
      /_/

Using Python version 3.10.4 (v3.10.4:9d38120e33, Mar 23 2022 17:29:05)
Spark context Web UI available at http://192.168.11.3:4040
Spark context available as 'sc' (master = local[*], app id = local-1679906351759).
SparkSession available as 'spark'.
>>>
```
これでpysparkを使用できるようになりました。