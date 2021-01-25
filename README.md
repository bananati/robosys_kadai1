# robosys_kadai1
## 概要
ロボットシステム学の演習で作成したデバイスドライバの改良を行ったコード．以下の機能を追加した．
- 1を入力した場合、LEDが点灯
- 2を入力した場合、LEDの点灯と消灯を1セットとしてLEDが10セット点滅
- 0を入力した場合、LEDが消灯
## 用意するもの
以下の環境で動作を確認しています．
- Raspberry Pi 4 Model B
- OS:Ubuntu 20.04 LTS
- ブレッドボード
- LED✕1
- 抵抗100Ω✕1
- ジャンパー線（オス-メス）2本
## 回路構成
以下のように回路を組む．
![iOS の画像](https://user-images.githubusercontent.com/77135361/105760137-ac924e00-5f94-11eb-9eaf-b1c5e7fe9170.jpg)
LEDのアノード側をGPIO25に接続し，カソード側を任意のGNDに接続．
## 環境構築
```
$ git clone https://github.com/bananati/robosys_kadai1.git
$ cd robosys_kadai1/myled
$ make
$ sudo insmod myled.ko //カーネルモジュールをインストール
$ sudo chmod 666 /dev/myled0 //ファイルのアクセス権を変更
```
## 実行方法
1を実行
```
$ echo 1 > /dev/myled0
```
2を実行
```
$ echo 2 > /dev/myled0
```
0を実行
```
$ echo 0 > /dev/myled0
```
実行後は以下のコマンドを入力
```
$ sudo rmmod myled //カーネルモジュールのアンインストール
$ make clean //カーネルモジュールを消去
```
## デモ動画
