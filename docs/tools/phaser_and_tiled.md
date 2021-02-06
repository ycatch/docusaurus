---
id: phaser_and_tiled
title: Tiled で作成したタイルマップ json ファイルを phaser.js に読み込む方法
sidebar_label: phaser_and_tiled
---

Javascript ゲームエンジンの Phaser.js は、タイルマップを読み込めるのだけれど、Tilemap データの作成や読み込みに苦労したので、その手順を記述する。

結論から書くと、Tiled でエクスポートする前に、タイルセットレイヤーで「Embed Tilelayer」ボタンをクリックしておく。

## 準備

タイルマップのパーツになるタイルセット画像を用意しておく。

ここでは、32x32 ピクセルの画像を組み合わせて、「tilesets.png」というファイルにしている。

![tilesets.png](https://www.catch.jp/wiki3/content/tools/phaser_and_tiled01.png)

## Tiled

- [Tiled Map Editor | A generic tile map editor](http://www.mapeditor.org/)

クロスプラットフォームのタイルマップ作成ツール。

json ファイルを作成するには、次のように操作する。

1. Tiled を起動する
2. 新しいマップを作る
3. レイヤー名を「ground」にする(**重要**)
4. タイルセットとして、tilesets.png を読み込む
5. タイルセット名として「tileset」を指定する(**重要**)
6. タイルセットを使って、タイルマップを描く
7. タイルセットレイヤーで「Embed Tilelayer」ボタンをクリック(**重要**)
8. 「ファイル」>「名前を付けてエキスポート」。json フォーマットで保存する。
   ファイル名は「tilemap.json」。

![Tiled](https://www.catch.jp/wiki3/content/tools/phaser_and_tiled02.png)

## 読み込むファイル

phaser.js に読み込むとき、必要になるファイルと情報は下記のとおり。

- タイルマップの json ファイル：tilemap.json
- タイルセット画像ファイル：tilesets.png

- タイルマップレイヤー名：ground
- タイルセット名：tileset

## phaser.js

- [Phaser - A fast, fun and free open source HTML5 game framework](https://phaser.io/)

preload()の記述

```js
// Load tileset and tilemap
function preload() {
  game.load.tilemap(
    "map1",
    "images/test11.json",
    null,
    Phaser.Tilemap.TILED_JSON
  ); // タイルマップのjsonファイル
  game.load.image("tiles", "images/tilesets.png"); // タイルセット画像ファイル
}
```

create()の記述

```js
var map;
var layer;

// Set name of tileset and name of tilemap layer
function create() {
  map = game.add.tilemap("map1"); // 引数はpreloadでロードしたマップ名
  map.addTilesetImage("tileset", "tiles"); // 第1引数にタイルセット名
  layer = map.createLayer("ground"); // タイルマップのレイヤー名
  layer.resizeWorld();
}
```

## 関連ページ

- [Phaser 入門:HTML5/Javascript 2D ゲームエンジン - catch.jp-wiki](https://www.catch.jp/wiki/index.php?Phaser)
- [Making your first Phaser game をやってみた - catch.jp-wiki](https://www.catch.jp/wiki/index.php?phaser%2Ftutorial_01)
- [Phaser のゲームを改良してみた - catch.jp-wiki](https://www.catch.jp/wiki/index.php?phaser%2Ftutorial_02)
- [Phaser で、HTML5 のオリジナルゲームを作ってみた - catch.jp-wiki](https://www.catch.jp/wiki/index.php?phaser%2Foriginal_01) タイルマップを使用

- [Phaser - Examples - Loader - Load Tilemap Json](https://phaser.io/examples/v2/loader/load-tilemap-json)
