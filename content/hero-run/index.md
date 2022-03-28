+++
title = "主人公の逃走"
date = 2022-03-28
+++

戦闘時の「にげる」コマンドについて。

本作ではりゅうおうを含む全ての敵から逃げられる。  
ただし、イベント戦で逃げてもイベントは飛ばせない。

## 逃走成功率

逃走成功率は以下の要素に依存する:

* 主人公の素早さ (A とおく)
* 敵の守備力 (B とおく)
* 敵のモンスターID

`(0..=255 の乱数) * A - K * B` が非負なら成功、負なら失敗となる。K はモンスターIDにより異なる:

* モンスターID `0..=19` の場合、`K = (0..=63 の乱数)`
* モンスターID `20..=29` の場合、`K = (0..=95 の乱数)` (実際は 2 つの乱数および乱数更新時のキャリーフラグの和)
* モンスターID `30..=34` の場合、`K = (0..=127 の乱数)`
* モンスターID `35..=39` の場合、`K = (0..=255 の乱数)`

### モンスター別の逃走成功率表

全モンスターについて[乱数](@/rng/index.md)値を全探索し、主人公の素早さの値ごとの逃走成功率を算出した:

* [スライム](@/hero-run-table-00/index.md) (ID=0, 守備力=3)
* [スライムベス](@/hero-run-table-01/index.md) (ID=1, 守備力=3)
* [ドラキー](@/hero-run-table-02/index.md) (ID=2, 守備力=6)
* [ゴースト](@/hero-run-table-03/index.md) (ID=3, 守備力=8)
* [まほうつかい](@/hero-run-table-04/index.md) (ID=4, 守備力=12)
* [メイジドラキー](@/hero-run-table-05/index.md) (ID=5, 守備力=14)
* [おおさそり](@/hero-run-table-06/index.md) (ID=6, 守備力=16)
* [メーダ](@/hero-run-table-07/index.md) (ID=7, 守備力=18)
* [メトロゴースト](@/hero-run-table-08/index.md) (ID=8, 守備力=20)
* [ドロル](@/hero-run-table-09/index.md) (ID=9, 守備力=24)
* [ドラキーマ](@/hero-run-table-10/index.md) (ID=10, 守備力=26)
* [がいこつ](@/hero-run-table-11/index.md) (ID=11, 守備力=22)
* [まどうし](@/hero-run-table-12/index.md) (ID=12, 守備力=22)
* [てつのさそり](@/hero-run-table-13/index.md) (ID=13, 守備力=42)
* [リカント](@/hero-run-table-14/index.md) (ID=14, 守備力=30)
* [しりょう](@/hero-run-table-15/index.md) (ID=15, 守備力=34)
* [メタルスライム](@/hero-run-table-16/index.md) (ID=16, 守備力=255)
* [ヘルゴースト](@/hero-run-table-17/index.md) (ID=17, 守備力=38)
* [リカントマムル](@/hero-run-table-18/index.md) (ID=18, 守備力=36)
* [メーダロード](@/hero-run-table-19/index.md) (ID=19, 守備力=40)
* [ドロルメイジ](@/hero-run-table-20/index.md) (ID=20, 守備力=50)
* [キメラ](@/hero-run-table-21/index.md) (ID=21, 守備力=48)
* [しのさそり](@/hero-run-table-22/index.md) (ID=22, 守備力=90)
* [しりょうのきし](@/hero-run-table-23/index.md) (ID=23, 守備力=56)
* [ゴーレム](@/hero-run-table-24/index.md) (ID=24, 守備力=60)
* [ゴールドマン](@/hero-run-table-25/index.md) (ID=25, 守備力=40)
* [よろいのきし](@/hero-run-table-26/index.md) (ID=26, 守備力=78)
* [メイジキメラ](@/hero-run-table-27/index.md) (ID=27, 守備力=68)
* [かげのきし](@/hero-run-table-28/index.md) (ID=28, 守備力=64)
* [キラーリカント](@/hero-run-table-29/index.md) (ID=29, 守備力=70)
* [ドラゴン](@/hero-run-table-30/index.md) (ID=30, 守備力=74)
* [スターキメラ](@/hero-run-table-31/index.md) (ID=31, 守備力=80)
* [だいまどう](@/hero-run-table-32/index.md) (ID=32, 守備力=70)
* [あくまのきし](@/hero-run-table-33/index.md) (ID=33, 守備力=82)
* [キースドラゴン](@/hero-run-table-34/index.md) (ID=34, 守備力=84)
* [ストーンマン](@/hero-run-table-35/index.md) (ID=35, 守備力=40)
* [しにがみのきし](@/hero-run-table-36/index.md) (ID=36, 守備力=86)
* [ダースドラゴン](@/hero-run-table-37/index.md) (ID=37, 守備力=90)
* [りゅうおう第1形態](@/hero-run-table-38/index.md) (ID=38, 守備力=75)
* [りゅうおう第2形態](@/hero-run-table-39/index.md) (ID=39, 守備力=200)


## イベント戦における逃走

イベント戦で逃げた場合、イベントが飛ばされないような措置がとられる:

* フィールド (73, 100) のゴーレム戦で逃げた場合、1 歩上に移動させられる。
* 沼地の洞窟 (4, 14) のドラゴン戦で逃げた場合、1 歩上に移動させられる。
* ドムドーラ (18, 12) のあくまのきし戦で逃げた場合、1 歩左に移動させられる。
* りゅうおう(形態不問)戦で逃げた場合、単に移動画面に戻る。りゅうおうに話しかけると再戦できる。
