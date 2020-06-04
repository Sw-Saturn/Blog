---
title: "Glideを使って334秒でTODOアプリを作る話"
date: 2020-06-04T03:34:00+09:00
draft: false
author: "Kanta Demizu"
summary: "334秒でアプリ開発"
tags: ['開発','glide','flutter']
share: true
toc: true
thumbnail: "/img/thumbnail/screen.png"
slug: "334todo_glide"
---

こんにちは。でみです。

今回はGlide[^1]というRADフレームワークを使って、334秒でTODOアプリを作っていきます。

## 本題

やっていきましょう。

### 準備

Google Driveでスプレッドシートを用意しておきます。

### 作っていこう

Glide[^1]のページにアクセスして、Create appを選択。

先ほど作成したスプレッドシートを選択。

タブの項目からタブを作成します。

{{< thumbnail src="pic1.png" width="50%" title="今回のタブの設定" >}}

次に表示する項目を設定しましょう。

サイドバーからLayoutを選択し、先ほど作成したタブのプロパティを開きます。

Todoのタブは以下のように設定しました。

{{< thumbnail src="pic2.png" width="50%" title="Layout" >}}
{{< thumbnail src="pic3.png" width="50%" title="Features" >}}
{{< thumbnail src="pic4.png" width="50%" title="Add" >}}

DoneのタブはFilterを*Done is true*に設定。

これでサイドバーのSettingsから見た目をいい感じにすると完成です。

今回はユーザー固有のデータを利用していないので、やることがインターネットに大放流されます。~~許して~~

PWAが動くようになれば、右上のShareボタンから0.334秒でリリースできます。

今回作成したアプリは

{{<blog "https://hutmr.glideapp.io/">}}

上のリンクから使えます。
よかったら試してみてね。

## 終わりに

Glide[^1]を使って簡単にアプリケーションを作ることができました。

データをスプレッドシートにまとめて配信するなどの用途には良さそうですね。

おわり。

[^1]: [Glide](https://www.glideapps.com)
