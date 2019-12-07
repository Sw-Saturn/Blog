---
title: "Rapidoを使って334秒でTODOアプリを作る"
date: 2019-12-07T21:27:14+09:00
draft: false
author: "Kanta Demizu"
summary: "334秒でアプリ開発"
tags: ['開発','rapido','flutter']
share: true
toc: true
thumbnail: ""
slug: "334todo"
---

**この記事は「kvin鯖 Advent Calendar 2019」の7日目の記事です。**

{{<blog "https://adventar.org/calendars/4175">}}

こんにちは。でみです。

今回は[Rapido](https://pub.dev/packages/rapido)というRADフレームワークを使って、334秒でTODOアプリを作っていきます。

## RAD(Rapid Application Development)とは?
有名なバンドではなく、ざっとこんな感じ。
>Rapid Application Developmentの略。「高速アプリケーション開発」の意味。システム開発の手法の1つ。ユーザーを含む少人数で仕様分析、設計、開発を進め、繰り返し試作品を作成して評価・改良することで完成品に近づけていく。開発期間を短縮し、高品質のシステムを構築できる。

(引用元:[RAD | IT用語辞典 | 大塚商会](https://www.otsuka-shokai.co.jp/words/rad.html))

要するに、ツールとか使いまくってさくっと作る的な感じですね(間違ってるかも)。

## 本題
開発環境は整っている前提でいきます。

### コードを書くまでの準備
Flutterの新規プロジェクトを作成します。

pubspec.yamlにrapidoの依存関係を追加。
{{< highlight dart>}}
dependencies:
  rapido: ^0.1.9
{{< /highlight >}}
JetBrainsな人は上の`Packages get`を選択して、それ以外の人は、
`flutter pub get` でパッケージを取得します。

{{< highlight html>}}
Running "flutter pub get" in todo_rad...                           15.7s
Process finished with exit code 0
{{< /highlight >}}
こんな感じだったら:ok:

### 実際に書いていこう

main.dartの上に追記。
{{< highlight dart>}}
import 'package:rapido/rapido.dart';
{{< /highlight >}}

あとはこんな感じにDocumentListと入力フィールドとDocumentListScaffoldを作成するだけ。
{{< highlight dart>}}
class _MyHomePageState extends State<MyHomePage> {
  DocumentList taskslist = DocumentList("Tarea",
      labels: {"Date": "date", "Task": "task", "Priority": "pri count"});

  @override
  Widget build(BuildContext context) {
    return DocumentListScaffold(taskslist);
}
{{< /highlight >}}
labelはデータの項目のようですね。

labelを設定する時に、dateやlatlongを指定すると、それぞれDatePicker、LocationPickerが使えるようです。便利。

さて、ここまでできたらビルドしてみましょう。

{{< figure src="/img/rapido/todo_1.png" width="40%" class="inline">}}
{{< figure src="/img/rapido/todo_2.png" width="40%" class="inline">}}

いい感じになってる。

この時点で項目の追加・編集・削除など一通り動きます。

ただ一つだけ謎なのが、一番最後に追加したデータのみ永続化できています。リスト全体ではないんですよね...

とりあえずこれで完成ということにしておきます(?)

## おまけ
誕生日だったということでこんなもの作ってみました。

{{< figure src="/img/rapido/birthdayapp.jpg" width="40%" title="プライマリーカラーに阪神は関係ありません">}}
`DocumantListScaffold()`の引数に`customItemBuilder`を設定すると、普段通りにWidgetをを設定できます。
年齢の表示とか、残り日数に応じてカードの色を変えてみました。

~~デザインできないので見た目は許して()~~

:poop:コードは以下のリンクに公開してるのでよかったら見てください。

{{<blog "https://github.com/Sw-Saturn/birthday-countdown">}}

## 終わりに
rapidoを使って簡単にアプリケーションを作ることができました。

しっかり使える形にするなら1から作った方が良さそうですが、初心者にはサクッと目に見えて動くものが作れてオススメです。

### 参考
{{<blog "https://github.com/rapido-mobile/rapido-flutter">}}
{{<blog "https://qiita.com/ssoejima/items/58c5b67214c03b040f2c">}}
