# meishikbd ビルドガイド


## 部品


| 名前 | 数 | 備考 |
| ---- | ---- | --- |
| PCB | 1枚 | |
| Pro Micro | 1個 | |
| タクトスイッチ | 1個 | |
| ピンヘッダ | 2個 | スプリングピンヘッダ(12P)でも可 |
| キースイッチ | 8個 | MX互換 |
| キーキャップ | 8個 | キースイッチと互換があるもの |
| micro USBケーブル | 1本 | |
| ゴム足 | 4個 | 必要に応じて |

## 必要な道具

| 名前 | 備考 |
| ---- | ---- |
| はんだごて |  |
| 糸ハンダ | 0.8mm程度のものを推奨 |



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

※スプリングヘッダを使用する場合  

スプリングピンヘッダには推奨する向きがあります．

側面の小さい窓がPro Micro寄りになります．
また，実装時には二本ともに小さい窓が同じ方向を向くようにしてください．

※向きを間違えたり，はんだ付けする前に強い力がかかるとピンが外れますので注意してください．また，足が折れ曲りやすいので抜き差しするときには注意して扱ってください．

裏面を上にしてPCBのスルーホールに取り付けてください．はんだ付けしなくても固定されます（Pro Microとスプリングピンヘッダのみをはんだ付け）．

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
次のコマンドで，必要なツールのインストールを行います．
```
util/qmk_install.sh
```
ファームウェアをPro Microに書き込みます．
#### ファームウェアのビルド
次のコマンドを実行します．
```
make meishikbd:default
```
#### Linux, Mac, Msys2の場合
次のコマンドを実行すると，ビルドと書き込みを同時に置こうことができます．

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
#### qmk toolbox場合
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