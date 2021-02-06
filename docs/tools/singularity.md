---
id: singularity
title: Singularity CMS を使ってみた
sidebar_label: Singularity
---

40 行ほどの php ファイルと.htaccess ファイルで構成されたシンプルな Flat-File CMS。
Markdown の変換には、[Strapdown.js](http://strapdownjs.com/)を利用している。

- [Singularity-cms by csu](https://christopher.su/singularity-cms/)

サーチエンジンにも、ひっかかる。ナビゲーションバーがあるといいなー。

あと、ページデザインをカスタマイズする方法が、もう少し欲しい。

## インストール

ダウンロードしたファイルを放り込むだけ。

## ページ投稿

content ディレクトリに、Markdown ファイルをコピーする。

## ページアクセス

| URL              | 表示されるページ    |
| :--------------- | :------------------ |
| /index           | index.md            |
| /myfile          | myfile.md           |
| /myfolder/index  | /myfolder/index.md  |
| /myfolder/myfile | /myfolder/myfile.md |

## カスタマイズ

index.php で以下の項目を編集する。

- ROOT_DIR '/'
- CONTENT_DIR 'content/'
- file_format = '.txt'

## テーマ

[Bootswatch](https://bootswatch.com/)から、Strapdown.js に含まれている以下のテーマを選択できる。

- cerulean
- cyborg
- journal
- readable
- simplex
- slate
- spacelab
- spruce
- superhero
- united
