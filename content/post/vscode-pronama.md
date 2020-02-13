---
title: "Visual Studio Codeにプロ生ちゃんを召喚した話"
date: 2020-02-13T19:47:25+09:00
draft: false
author: "Kanta Demizu"
summary: "VSCodeにプロ生ちゃんを召喚します"
tags: ['開発','editor','vscode']
share: true
toc: true
thumbnail: "/img/pronama/editor.png"
slug: vscode-pronama-chan
---

## はじめに

開発のモチベーションを上げるために、[プロ生ちゃん](https://kei.pronama.jp)をVS Codeに召喚させようと思います。

元ネタは、[プロ生ちゃん IDE](https://pronama.jp/2016/11/27/pronama-chan-ide-vs2017/)。

## やり方

[vscode-background](https://marketplace.visualstudio.com/items?itemName=shalldie.background)を使います。

上記の拡張機能をインストールして、*settings.json*を以下のように編集。
画像は[ここ](https://pronama.jp/images/animated.png)から拝借しています。

{{< highlight json "linenos=inline, linenostart=1" >}}
"background.useDefault": false,
    "background.customImages": [
    "https://pronama.jp/images/animated.png",
],
"background.style": {
    "content": "''",
    "pointer-events": "none",
    "position": "absolute",
    "z-index": "99999",
    "width": "100%",
    "height": "100%",
    "background-position": "100% 100%",
    "background-repeat": "no-repeat",
    "background-size": "20%",
    "opacity": 0.3
},
{{< / highlight >}}

ちなみに、*background.customImages*に好きな画像を複数設定することで、ランダム表示にすることもできます！

編集したら、VS Codeを再起動すると完了！

ファイルを開くと、プロ生ちゃんが現れていると思います。
[APNG](https://developer.mozilla.org/ja/docs/Animated_PNG_graphics)なので目がパチパチしてかわいい！

{{< figure src="/img/pronama/editor.png" width="100%" class="inline">}}

## おわりに

簡単にVS Codeのエディタ画面に画像を表示することができました。

自分で拡張機能を作ってみても楽しいかもしれませんね！
