---
id: mdwiki
title: MDwiki:Markdown ベースの超シンプル CMS
sidebar_label: MDwiki
---

MDwiki は、Markdown ベースのとてもシンプルなコンテンツ管理ツール。

Wiki というよりも、[Flat-File CMS](flatfile_cms)というジャンルなのかもしれない。

非常に便利だったけど、ほとんど日本語情報がなかったので整理しておきます。

- [MDwiki - Markdown based wiki done 100% on the client via javascript](https://dynalon.github.io/mdwiki/#!index.md)
- [HoneDrops:けっきょく、自分で作ってみた](https://www.catch.jp/honedrops/index.ja)

## 特徴

**mdwiki.html というひとつのファイルだけあれば利用できる**

で、Markdown 記法で書かれたテキストファイル(拡張子 .md、以下 md ファイル)を、この mdwiki.html と同じフォルダに置く。

これだけで、md ファイルが Web ページとして表示されます。

サーバーにスクリプトや DB を設置する必要もないし、いちいち md ファイルを変換する必要もありません。

- mdwiki.html のなかに、Javascript と Bootstrap ベースのテンプレートが埋め込まれている
- Gimmicks（ギミックス） という追加機能で、Google マップや Facebook など今どきのソーシャルサービスにも対応。
- クライアントサイドで html が作られるので、以前は検索エンジンに引っかからなかったが、最近は対応しているらしい。
- 作ったのは、 Timo D&#246;rr(Dynalon)さん。ライセンスは、GPLv3 + 追加条項

## サンプル

- [Welcome...](https://dynalon.github.io/mdwiki-examples/cafe/#!index.md)
- [Travel_blog](https://dynalon.github.io/mdwiki-examples/travel_blog/#!index.md)
- [Muscle Cars of the 70's](https://dynalon.github.io/mdwiki-examples/muscle_cars/#!index.md)

## はじめ方

1. ドキュメントを md ファイルとして準備。

- 文字コードは UTF-8
- 1 行目は、見出し 1 にする(#記号)
- 最初のページのファイル名は、index.md とします。

* MDwiki をダウンロード。>> https://github.com/Dynalon/mdwiki/releases
* index.md と mdwiki.html を同じフォルダにおく

- mdwiki.html を開くと、自動的に index.md が変換されて表示
- どこかに Web サーバーがあるなら、そこにおいてもいい。社内とかイントラネットで使うなら、XAMPP とか用意するのが早いかも。

## 使い方

使い方も、とてもシンプル

### ページアクセス

- 「mdwiki.html」を開く場合は、index.md が変換されて表示される
- 下記のように「mdwiki.html」の後ろに「#!」＋ md ファイル名をつけると、その md ファイルが変換されて表示される
- 例 https://example.com/mdwiki.html#!myfile.md

### ページ内のナビゲーション

- 見出し 1 が、ページタイトルになって、見出し 2 が複数あるとサイドに一覧表示される

### 書式設定

markdown でやる。画像やリンクも OK。

https://dynalon.github.io/mdwiki/#!layout.md

### ナビゲーションバー

- 下記のように、navigation.md ファイルを書いて、同じフォルダに置くと、上部の共通ヘッダーにナビゲーションバーが表示される

```
# サイトタイトル

[Home](home.md)
[About](about.md)
[Download](download.md)
```

### ページパス

| URL                             | 表示されるページ   |
| :------------------------------ | :----------------- |
| mdwiki.html                     | index.md           |
| mdwiki.html#!myfile.md          | myfile.md          |
| mdwiki.html#!myfolder/          | myfolder/index.md  |
| mdwiki.html#!myfolder/myfile.md | myfolder/myfile.md |

## 各種設定

### テーマの切り替え

公式サイトの右上にあるやつ。

Theme chooser というギミックスでできる。

https://dynalon.github.io/mdwiki/#!customizing.md#Theme_chooser

navigation.md に、こんなふうに記述すると、テーマ選択メニューが表示される。

```
[gimmick:themechooser](Choose theme)
```

navigation.md に、こんなふうに記述すると、デフォルトテーマを指定できる。

```
[gimmick:theme](flatly)
```

### ギミックス

Gimmicks（ギミックス） という追加機能で、Google マップや Facebook など今どきのソーシャルサービスにも対応。

こんなのが、ありますね。

- Alerts
- GitHub Gists
- Facebook Likebutton
- Fork me on GitHub - Ribbon
- Google Maps
- UML Diagrams via yUML.me
- Math
- Twitter
- Youtube
- Disqus

https://dynalon.github.io/mdwiki/#!gimmicks.md

### スタイルシート

mdwiki.html に埋め込まれているので、そこをいじる。

デフォルトでは、Twitter bootstrap が組み込まれていて、さらに追加の css がある。

個人的には、追加部分を mdwiki.css という外部 css ファイルに切り出して、そちらでいじっている。見出しなどのスタイルを変えるときも、そこでやる。

そのために、mdwiki.html の 194 行目あたりに以下のコードを埋め込む。

```html
link rel="stylesheet" href="style.css"
```

もしも、自分で[MDwiki をビルド](mdwikidev)できるなら、style/custom.css にスタイルを追記できる。

### ページ一覧の取得

ページ一覧を取得する方法がないので、navigation.md で上部メニューに手動で追加する。

まあ、wiki なので、ページ一覧を表示させるのは、本質的ではないということかも。

### 設定ファイルによるカスタマイズ

config.json というファイルを同じフォルダにおくと、カスタマイズできる。こんな設定がある。

- サイドナビの ON/OFF
- オリジナルの改行指定
- フッターテキストの追加
- 見出しのアンカー記号
- タイトル(ただし、Google 検索の結果には反映されない。そこを変えるには、html の title タグを修正する)

```
{
    "useSideMenu": true,
    "lineBreaks": "gfm",
    "additionalFooterText": "All content and images &copy; by John Doe",
    "anchorCharacter": "#",
    "title": "ACME Industries Wiki"
}
```

詳細は、https://dynalon.github.io/mdwiki/#!customizing.md#Configuration

### 追加の Javascript

こんな感じで、mdwiki.html の 200 行目(mdwiki.js の一番最後)に追加すると、「MyGimmick」というギミックスが追加できる。該当ページが表示された後に、1 回だけコードを実行してくれる。

```javascript
(function ($) {
  "use strict";
  var myGimmick = {
    name: "MyGimmick",
    version: $.md.version,
    once: function () {
      // write code here
    },
  };
  $.md.registerGimmick(myGimmick);
})(jQuery);
```

h1 の見出し(#記号のやつ)をタイトルに設定する

```javascript
// Add title
var titletext = $("h1:last").text();
document.title = titletext + " / catch.jp-memo"; // 表示テキスト
```

外部リンクを別タブで開く。

```javascript
// Add external link on a-tag
var domain = "www.example.jp/wiki/"; // 設置場所
$("a[href^=http]")
  .not('[href*="' + domain + '"]')
  .attr("target", "_blank");
```

あと、こんな方法もあるみたい。

- [MDwiki コンテンツエリアのカスタマイズ | 3D 技術研究所 Blog](https://3dtech.jp/blog/?p=110#more-110)

## ライセンス

- GPLv3 + 追加条項
- 追加条項は、Google マップのコードとか Twitter ボタンとかは、GPLv3 の対象外とか言っている(たぶん)
  -- https://github.com/Dynalon/mdwiki/blob/master/LICENSE.txt

## 関連情報

- [MDwiki](https://dynalon.github.io/mdwiki/#!index.md)
- [ソースコード](https://github.com/Dynalon/mdwiki/)
- [ビルド方法](mdwikidev)

### レビュー

少し増えていた

- MDwiki Markdown をコンテンツに使った CMS/Wiki システム MOONGIFT https://www.moongift.jp/2013/11/mdwiki-markdown%E3%82%92%E3%82%B3%E3%83%B3%E3%83%86%E3%83%B3%E3%83%84%E3%81%AB%E4%BD%BF%E3%81%A3%E3%81%9Fcmswiki%E3%82%B7%E3%82%B9%E3%83%86%E3%83%A0/
- MarkDown で書いたファイルを置くだけで Wiki 化できる MDWiki を導入してみた。 - Qiita https://qiita.com/nusa/items/8b07a8d75abc2044fa87
- MDWiki を導入してみてわかったこと - Qiita:https://qiita.com/nusa/items/54cc7b38517192b3caf4
- MDwiki に感動した - Qiita:https://qiita.com/tukiyo3/items/4cbfa1d2338c061df015
- MDwiki でローカルにオレオレ Wiki を作成する - 気になったことをいろいろやってみる:https://ogeji.hatenablog.com/entry/2015/06/05/121109
- MDwiki はじめました | 3D 技術研究所 Blog:https://3dtech.jp/blog/?p=101

- 【MDwiki】Html と Markdown ファイルを置くだけで作成できる！自分専用 Wiki ツールのご紹介: シーサー渋谷ではたらく技術担当のブログ（SSG ブログ）:https://techdev.seesaa.net/article/436995731.html
- [dropbox][wiki]MDWiki についての情報をまとめる | ブログ | そうだ車輪と名づけよう 5th:https://www.atyks.org/blog/detail/2015-10-22-1
- MDwiki に関する Tips - hphm’s diary:https://hphm.hateblo.jp/entry/2015/03/23/124819
- MDWiki の導入方法 - MIN:https://min.hatenablog.jp/entry/2016/02/06/155242
- MDwiki を Owncloud と連携させて Web で編集できるようにした - ひよこになりたい:https://zipsan.hatenablog.jp/entry/20151014/1444816696

- MDWiki に関する 6 件の投稿 - Qiita:https://qiita.com/tags/MDWiki

## 類似ツール

- Flat-FileCMS:https://www.google.co.jp/search?q=Flat-FileCMS&ie=utf-8&oe=utf-8&gfe_rd=cr&ei=TdmaWa3hK6fK8gfU6I7YBg

- Markdown・Textile・Wiki 記法をサポートした JavaScript 製ドキュメントフレームワーク「Invisible.js」を公開しました(オープンソース) | Chrome Life:https://www.chrome-life.com/javascript/554/
- 好きなブラウザで動作する Markdown ビューア local-notes.js を公開しました https://henry.animeo.jp/blog/2013/11/29/local-notes-js/
- marked.js https://github.com/chjj/marked

あと、MDwiki という名前のツールが、他にもいくつかあって、ちょっとまぎらわしい

- erickrdch/mdwiki https://github.com/erickrdch/mdwiki
- https://www.mdwiki.net/
