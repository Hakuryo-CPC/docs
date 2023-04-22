---
description: pygameと出会います。
---

# Hello Pygame

Pythonでマインスイーパーゲームを作るにあたって、今回 `pygame` というライブラリを使用することにします。

### インストール

Pythonライブラリのインストールに今回はPython付属の `pip` を使用することにします。\
再びターミナルを開いて、インストールを実行します。

```bash
pip install pygame
```

### Hello Pygame

`main.py` の頭に `pygame` のimportを追加します。

```python
import pygame
```

続けて、

```python
pygame.init()
pygame.display.set_mode((400, 400))

running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
```

を追加し、実行してみましょう。

![](<../.gitbook/assets/image (3).png>)

真っ黒いキャンバスが出現しました。\
我々はここに、マインスイーパーをどんどんと描いていくことになります!

ではさて、コードを見てみます。

```python
pygame.init()
pygame.display.set_mode((400, 400))
```

`init` で、先程インポートした `pygame` モジュールを初期化しています。\
初めに初期化することで、 `pygame` モジュールの準備をします。

`display.set_mode((400, 400))` では、さっき準備したモジュールを使用します。\
見たまんま、表示(display)関連で、 `set_mode` は表示ウィンドウ初期化をします(ウィンドウを作ります)。\
タプル型で `(横長, 縦長)` を渡して画面サイズを設定できます。\
この場合は400px x 400pxです。\
`set_mode` で作られたウィンドウは、当然ですが `main.py` が終了すれば一緒に終了します。\
つまり、ここまでだけのプログラムで実行すると、 `set_mode` でウィンドウが作られ、そのまますべての処理を終えたため `main.py` は終了します。 -> 一瞬ウィンドウが現れて、すぐ消えます。

```python
running = True
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
```

`running` が `True` なので、初めwhileは `while True` 、つまり無限ループとなります。\
無限ループをウィンドウ作成後に配置したため、 `main.py` は即終了せず、つまりウィンドウは残り続けます。

`for`ループは1ループごとに、右上の赤いバッテンを押してウィンドウを閉じていないか、を確認します。\
もしそうなら、そのタイミングのループで `running` を `False` に更新することで`while`ループは `While False` により終了します。\
ループが終了すると `main.py` も終了しますから、バッテンを押したらループを終わらせる(プログラムを終了させる)、という処理を書いたわけです。

ライブラリ全貌の把握なんてのは厳しいですが、以降都度使い方を書いてみます。
