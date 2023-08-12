---
title: "Homebrewを使用したJavaのインストール方法" # 記事のタイトル
emoji: "☕️" # アイキャッチとして使われる絵文字（1文字だけ）
type: "tech" # tech: 技術記事 / idea: アイデア記事
topics: ["java"] # タグ。["markdown", "rust", "aws"]のように指定する
published: true # 公開設定（falseにすると下書き）
---

## 背景
CCA175合格を目指してHadoop環境を整備するため、新しく買ったmacbook airにJavaをインストールする

## 環境
- M1 Mac
- homebrew インストール済み

## インストール方法
1. Homebrewを使用してJavaをインストールする。バージョンを指定しなければ最新バージョンがインストールされる
```
$ brew install java
```

2. インストールの最後の方に以下の文章が出てくるため、sudo以下を実行する。シンボリックリンクを作成することで、参照先を指定する
```
For the system Java wrappers to find this JDK, symlink it with
  sudo ln -sfn /opt/homebrew/opt/openjdk/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk.jdk
```

3. バージョンをチェックする
```
$ java --version
openjdk 20.0.1 2023-04-18
OpenJDK Runtime Environment Homebrew (build 20.0.1)
OpenJDK 64-Bit Server VM Homebrew (build 20.0.1, mixed mode, sharing
```