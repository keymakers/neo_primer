# NEOで始めるブロックチェーン開発入門

このリポジトリは、Keymakers著『NEOで始めるブロックチェーン開発入門』のサポートリポジトリです。

<!-- 表紙と販売ページへのリンク欲しい -->

本書に関するご意見・ご質問は[Discord](https://discord.gg/u4sxXas)の#neo_primer_supportチャンネルまでどうぞ

## 【重要】neo-pythonコマンドについて
2019/01/16に実装されたneo-python v0.8.3 へのアップデートによって、プロンプトを起動した後のコマンドが大きく変更されました。
これに伴い、v0.8.3以後のneo-pythonでは、本書に記載のコマンドではエラーが発生するようになってしまいました。

```
Command 'xxxxx' not found
```

この問題に対して以下のページに、新しいコマンドの解説を記しましたので、ご参考ください。

[コマンド解説一覧](https://github.com/keymakers/neo_primer/blob/master/commands.md)

## リンク
* Keymakers 公式ホームページ：[keymakers.jp](keymakers.jp)
* Keymakers 公式チャット：[Discord](https://discord.gg/u4sxXas)


## サンプルコード等
本書で使用したソースコード等は、以下のリポジトリから参照しています。

### 3章 開発を進めるための準備とHelloworld

* チュートリアル用のフォルダー：[CityOfZion / python-smart-contract-workshop](https://github.com/CityOfZion/python-smart-contract-workshop)
* ウォレットファイル：[neo-privnet.wallet](https://s3.amazonaws.com/neo-experiments/neo-privnet.wallet)

### 4章 NEO上の独自トークン”NEP5”を自分で発行してみるには？
サンプルコード：[Keymakers / NEP5](https://github.com/keymakers/NEP5)

### 5章 ICOをしてみよう
テンプレート：[neonexchange / neo-ico-template](https://github.com/neonexchange/neo-ico-template.git)

### 6章 モバイル開発に最適なneon-jsとneoscan
Dockerファイル：[Keymakers / neo-scan-docker](https://github.com/keymakers/neo-scan-docker)
