---
title: "dmz_ai作ってみた"
date: 2018-12-07T08:49:55+09:00
draft: false
author: "Kanta Demizu"
summary: "人工知能(大嘘)を作ってみました．"
share: true
---
こんなもん作ってみました．

<a class="twitter-timeline" width=60% height="400px" href="https://twitter.com/dmz_ai?ref_src=twsrc%5Etfw">Tweets by dmz_ai</a> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

### 作ろうと思った経緯

　今年の10月下旬ごろに開催された高専プロコンに参加してきました．例年，高専プロコンが終わったらTLが賑やかになるんですよね．
そしてTLのプロたちを眺めていたらこんなものが飛び込んできました．
<div class="blogCard"><div class="blogCardCont"><div class="blogCardTxt"><p class="blogCardTitle"><a href="http://kvinnoiroiro.hatenablog.com/entry/2018/11/04/221920">C#で人口無能と化した僕.botを作った - ケヴィンのなんかいろいろ</a></p><p>突然ですが僕の分身を作りました。2日で作った（コミットログ曰く）。 twitter.com こいつについて書きます。 なにこれ？ モチベーション 実装とか ツイートを取得する、ツイートする 形態素解析して文節を抽出してテーブルを作る マルコフ連鎖（のような何か）を利用して、ツイートする文章を作る。 作った文章をツイート 問題 今後 参考資料</p></div><div class="blogCardImg"><div class="blogCardImg__wrap"><a href="http://kvinnoiroiro.hatenablog.com/entry/2018/11/04/221920"><img src="https://cdn.blog.st-hatena.com/images/theme/og-image-1500.png" alt=""></a></div></div></div><div class="blogCardFooter"><a href="http://kvinnoiroiro.hatenablog.com/entry/2018/11/04/221920"><img src="//www.google.com/s2/favicons?domain=http://kvinnoiroiro.hatenablog.com/entry/2018/11/04/221920" alt="">kvinnoiroiro.hatenablog.com</a></div></div>

はいプロ．
プロです．

ということで私も作ってみました(便乗)．

## 中身
簡単にいうと，自分のTLの発言を200Post取得して，[MeCab](http://taku910.github.io/mecab/)で形態素解析する．

形態素解析した語彙を単語ごとに分割して3つ組に分けてSQLiteデータベースにぶちこむ．
マルコフ連鎖で文章生成して，Twitterに投稿する．的な流れです．

ちなみに，MeCabのPythonバインディングを使用してPythonでプログラム構成，VPSでcronを使って定期的にツイートしています．また，毎回新規学習はしないです．学習したくなったタイミングで語彙のアップデートができます．

## 総評
- なんか動いてはいるものの，ベースの文章がガバガバなのでアレ
- 自分本体の語彙力データベースを更新するべきだなー
- プロになりたい

そのうちまた機能追加していい感じにしていきたいですね．

### 追記@2019 Feb.05
適当にリプを送ると返答してくれるようになったよ！
やったね！

~~送りまくるとAPI制限引っかかると思うよ~~