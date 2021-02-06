---
id: flatfile_cms
title: Flat-File CMS
sidebar_label: Flat-File CMS
---

1 ページ 1 ファイルで実現する CMS(Contens Management System).

## メリット

- シンプルでスピーディ(DB 不要)
- インストールが簡単(ファイルを放り込むだけ)
- Markdown で書ける
- バックアップや移行が容易

## 課題

利用するためには、Markdown ファイルを作成してアップロードするツールが必要です。

Pico や Grav のような高機能な Flat-File CMS の場合は、編集用プラグインが用意されています。

一方、求められる Markdown の形式は、より厳密になる傾向がある印象。

## けっきょく、自分で作ってみた

![logo](https://www.catch.jp/wiki3/content/tools/honedrops.png)

- [HoneDrops](https://www.catch.jp/honedrops/index.ja)

短い PHP ファイルと、Javascript による Markdown パーサーで構成されています。

Singularity CMS と MDwiki にインスパイアされて作りました。

- データベース不要
- サーバー負荷が軽い > Markdown のレンダリングはクライアントで実行
- インストールが簡単 > ファイルを放り込むだけ
- Google 検索に対応
- 特定のテンプレートエンジンに依存しない
- カスタマイズが柔軟（Bootstrap と marked.js を利用）

## 主な Flat-File CMS

- [データベースを使わない Flat-File CMS という選択肢](https://hostingstock.net/article/notes/flat-file-cms/)
- [GitHub で人気の高い CMS ランキング (2016 年 6 月版) - Qiita](https://qiita.com/bezeklik/items/45fa04b83792743b7cbf)
- [A List of the Best Flat File CMS](https://www.cmscritic.com/flat-file-cms/)

### MDwiki

Javascript で 100%クライアントサイドで動く。手軽に使うなら、これがお勧め。

ただし、サーバーに設置しても、Google 検索には引っかからない。

- [MDwiki - Markdown based wiki](https://dynalon.github.io/mdwiki/#!index.md)
- [MDwiki：Markdown ベースの超シンプル CMS](mdwiki)

### Singularity

40 行ほどの php ファイルと.htaccess ファイルで構成されたシンプルな Flat-File CMS。
Markdown のパースには、Strapdown.js を利用している。

ナビゲーションとカスタマイズが不要なら、シンプルでいい。ネット検索にもひっかかるし。

- [Singularity](https://github.com/csu/singularity-cms)
- [Strapdown.js - Instant and elegant Markdown documents](https://strapdownjs.com/)
- [Singularity CMS を使ってみた](tools/singularity)

### dropplets

ブログに特化したシンプルな CMS。以前と配布サイトが変わっているので、古い記事だとリンク切れしているかも。

- [dropplets](https://github.com/johnroper100/dropplets)
- [Dropplets -紹介＆使い方など- | Kinchan's Blog](https://lmn-blog.com/dropplets01/)

### Pico

割とシンプルながら高機能。プラグインやテーマも揃っている。

- [Pico - A stupidly simple, blazing fast, flat file CMS.](https://picocms.org/)
- [【Pico】データベースを使わない、Markdown で記述する軽量 CMS を使ってみた。 ｜ Developers.IO](https://dev.classmethod.jp/tool/cms-pico/)

### Grav

けっこう高機能。ちょっと本格的に使うなら、このあたり。

インストールするには、「Grav Core + ADMIN Plugin」をダウンロードして、解凍したら、それを Web サーバーに放り込むだけ。あとは初回起動時に、管理用 ID の登録画面が開く。

- [Grav - A Modern Flat-File CMS](https://getgrav.org/)
- [Grav Documentation](https://learn.getgrav.org/)

- [フラットファイル CMS を比較して Grav にしました](https://unrea.usamimi.info/blog/migrate-to-grav)
- [Grav ってどんな CMS？2015 年度版 | 俺にはまだ二次元がある。](https://unrea.usamimi.info/blog/what-is-grav-cms-2015)
- [PHP 製 CMS Grav のインストール - Qiita](https://qiita.com/bezeklik/items/7593579462cb0557fd3d)

### その他

- [Monstra - The Fast, Extensible, and Easy Flat File Open Source Content Management System](https://monstra.org/)
- [CMSimple - Open Source CMS with no database](https://www.cmsimple.org/en/)

- [Ruby CMS - Nesta](https://nestacms.com/)
- [markdown-wiki
  ](https://github.com/Carpetsmoker/markdown-wiki)

- [Markdown・Textile・Wiki 記法をサポートした JavaScript 製ドキュメントフレームワーク「Invisible.js」を公開しました(オープンソース) - Chrome Life](https://www.chrome-life.com/javascript/554/)
