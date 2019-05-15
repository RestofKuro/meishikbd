# meishikbd ビルドガイド


## 内容物


| 名前 | 数 | 備考 |
| ---- | ---- | --- |
| PCB | 1枚 | |
| Pro Micro | 1個 | |
| ピンヘッダ | 2個 | スプリングピンヘッダ(12P)も使用可能 |
| タクトスイッチ | 1個 | |
| キースイッチ | 8個 | Cherry MX互換 |
| キーキャップ | 8個 | キースイッチと互換があるもの |

## 別途必要な物

| 名前 | 備考 |
| ---- | ---- |
| はんだごて |  |
| 糸ハンダ | 0.8mm程度のものを推奨 |
| micro USBケーブル | 通信のできるもの |
## あると便利なもの

| 名前 | 備考 |
| ---- | ---- |
| フラックス |  |
| マスキングテープ | Pro Micro，スイッチの固定用 |
| ゴム足 | 必要に応じて |

## 組み立て方
PCBの表面
![MVIMG_20190503_200215](https://user-images.githubusercontent.com/49835946/57136455-e6e2b180-6de7-11e9-9d0a-3a107b5debde.jpg)

PCBの裏面
![IMG_20190503_200222](https://user-images.githubusercontent.com/49835946/57136486-fcf07200-6de7-11e9-994e-f9ff64347db4.jpg)
### パーツ実装

#### リセットスイッチ

タクトスイッチを上面から実装してください．

![IMG_20190503_200251](https://user-images.githubusercontent.com/49835946/57136500-07127080-6de8-11e9-9ef6-5e733482274c.jpg)


#### Pro Micro

下の写真のようにPro Microを実装してください．
ピンヘッダを使用する場合は，両方はんだ付けをしてください．

※スプリングヘッダを使用する場合は，[Helixのビルドガイド](https://github.com/MakotoKurauchi/helix/blob/master/Doc/buildguide_jp.md#pro-micro)を参考にしてください．



![IMG_20190503_200645](https://user-images.githubusercontent.com/49835946/57136511-10034200-6de8-11e9-91f5-9c09cd50a049.jpg)



#### キースイッチ

キースイッチをはんだ付けします．

![IMG_20190503_201139](https://user-images.githubusercontent.com/49835946/57136535-1abdd700-6de8-11e9-82d2-515f58066e03.jpg)

### ファームウェア
#### ビルド環境構築
以下のコマンドまたは，[ここ](https://github.com/RestofKuro/qmk_firmware/tree/meishikbd)から，ソースコードをダウンロードします．
```
git clone -b meishikbd https://github.com/RestofKuro/qmk_firmware.git
```
次のコマンドで，ディレクトリを移動し必要なツールのインストールを行います．
```
cd qmk_firmware
util/qmk_install.sh
```

#### ファームウェアのビルド
次のコマンドを実行します．
```
make meishikbd:default
```
#### Linux, Mac, Msys2の場合
次のコマンドを実行すると，ビルドと書き込みを同時に置こうことができます．

実行権限が必要な場合は，`sudo`をつけて実行してください．

```
make meishikbd:default:avrdude
```
以下のメッセージが表示されたらリセットボタンを1回または2回押すと書き込みが開始されます．
```
Detecting USB port, reset your controller now.
```
次のメッセージが表示されたら成功です．
```
avrdude.exe done.  Thank you.
```
#### QMK Toolbox場合
[ここ](https://github.com/qmk/qmk_toolbox/releases)から，`qmk_toolbox.exe`をダウンロードします．

QMK Toolboxを起動し，作成した`meishikbd_default.hex`を選択します．
リセットボタンを押し，`Caterina device connected`と表示されたらFlashボタンを押します．

![toolbox](https://user-images.githubusercontent.com/49835946/57151657-6edab280-6e0c-11e9-87e4-d1b3cdcd83de.png)

次のメッセージが表示されたら成功です．
```
avrdude.exe done.  Thank you.
```
完成です．

![IMG_20190503_201206](https://user-images.githubusercontent.com/49835946/57136553-23aea880-6de8-11e9-8399-2aab2318cee3.jpg)