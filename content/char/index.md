+++
title = "文字コード"
date = 2022-03-24
updated = 2022-03-28
+++

文字コードの範囲は `0..=0x56 | 0x58..=0x6C` で、割り当ては下表の通り。  
'※' は特殊文字。

<table>
  <tr>
    <th></th>
    <th>x0</th>
    <th>x1</th>
    <th>x2</th>
    <th>x3</th>
    <th>x4</th>
    <th>x5</th>
    <th>x6</th>
    <th>x7</th>
    <th>x8</th>
    <th>x9</th>
    <th>xA</th>
    <th>xB</th>
    <th>xC</th>
    <th>xD</th>
    <th>xE</th>
    <th>xF</th>
  </tr>
  <tr>
    <th>0x</th>
    <td>０</td>
    <td>１</td>
    <td>２</td>
    <td>３</td>
    <td>４</td>
    <td>５</td>
    <td>６</td>
    <td>７</td>
    <td>８</td>
    <td>９</td>
    <td>あ</td>
    <td>い</td>
    <td>う</td>
    <td>え</td>
    <td>お</td>
    <td>か</td>
  </tr>
  <tr>
    <th>1x</th>
    <td>き</td>
    <td>く</td>
    <td>け</td>
    <td>こ</td>
    <td>さ</td>
    <td>し</td>
    <td>す</td>
    <td>せ</td>
    <td>そ</td>
    <td>た</td>
    <td>ち</td>
    <td>つ</td>
    <td>て</td>
    <td>と</td>
    <td>な</td>
    <td>に</td>
  </tr>
  <tr>
    <th>2x</th>
    <td>ぬ</td>
    <td>ね</td>
    <td>の</td>
    <td>は</td>
    <td>ひ</td>
    <td>ふ</td>
    <td>へ</td>
    <td>ほ</td>
    <td>ま</td>
    <td>み</td>
    <td>む</td>
    <td>め</td>
    <td>も</td>
    <td>や</td>
    <td>ゆ</td>
    <td>よ</td>
  </tr>
  <tr>
    <th>3x</th>
    <td>ら</td>
    <td>り</td>
    <td>る</td>
    <td>れ</td>
    <td>ろ</td>
    <td>わ</td>
    <td>を</td>
    <td>ん</td>
    <td>っ</td>
    <td>ゃ</td>
    <td>ゅ</td>
    <td>ょ</td>
    <td>※</td>
    <td>※</td>
    <td>※</td>
    <td>メ</td>
  </tr>
  <tr>
    <th>4x</th>
    <td>ラ</td>
    <td>ロ</td>
    <td>※</td>
    <td>ル</td>
    <td>レ</td>
    <td>コ</td>
    <td>ン</td>
    <td>タ</td>
    <td>シ</td>
    <td>ホ</td>
    <td>イ</td>
    <td>マ</td>
    <td>カ</td>
    <td>ム</td>
    <td>ー</td>
    <td>。</td>
  </tr>
  <tr>
    <th>5x</th>
    <td>、</td>
    <td>※</td>
    <td>※</td>
    <td>゛</td>
    <td>゜</td>
    <td>＊</td>
    <td>※</td>
    <td></td>
    <td>：</td>
    <td>※</td>
    <td>※</td>
    <td>※</td>
    <td>※</td>
    <td>※</td>
    <td>※</td>
    <td>※</td>
  </tr>
  <tr>
    <th>6x</th>
    <td>？</td>
    <td>！</td>
    <td>「</td>
    <td>Ｈ</td>
    <td>Ｍ</td>
    <td>Ｐ</td>
    <td>Ｇ</td>
    <td>Ｅ</td>
    <td>ミ</td>
    <td>ス</td>
    <td>キ</td>
    <td>ト</td>
    <td>…</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</table>

カタカナの 'ヘ', 'リ' は存在せず、ひらがなの 'へ', 'り' で代用されている。

特殊文字は以下の通り:

* 0x3C: ウィンドウ枠 左
* 0x3D: ウィンドウ枠 上
* 0x3E: ウィンドウ枠 上 (右が 1px 欠けている)
* 0x42: 1 タイル内に濁点も含む 'ド'
* 0x51: 下付き濁点 (下の行の文字と組み合わされる)
* 0x52: 下付き半濁点 (下の行の文字と組み合わされる)
* 0x56: カーソル
* 0x59: ウィンドウ枠 左上
* 0x5A: ウィンドウ枠 右上
* 0x5B: ウィンドウ枠 右
* 0x5C: ウィンドウ枠 左下
* 0x5D: ウィンドウ枠 下
* 0x5E: ウィンドウ枠 右下
* 0x5F: 空白

冒頭で述べた範囲以外のバイトは文字ではなく、[スクリプト](@/script/index.md)により解釈される。  
特に注意が必要なものを挙げておく:

* 0x57: キー入力待ち ('▼' を表示し、A または B キーの入力を待つ)
* 0xF8: 直前の文字を濁音化する (下付き濁点と組み合わせる)
* 0xF9: 直前の文字を半濁音化する (下付き半濁点と組み合わせる)
