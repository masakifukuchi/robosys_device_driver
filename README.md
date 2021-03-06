# ロボットシステム学　課題1
先生が講義用に作ってくださったデバイスドライバを少し改変したものです。
## 概要

<img src="https://user-images.githubusercontent.com/72370342/104086607-c21d2d80-529c-11eb-9e27-e6c34a59ca52.jpg" width="300px">

交通信号機を再現しました。  
歩行者用信号が赤に変わった後、車両用信号も赤に変わります。
## 動作環境
- Ubuntu 20.04
- Raspberry Pi 4 Model B
## 使用したもの　
- LED(赤×２、青×２、黄×１)
- 抵抗(220Ω)　×５
- ブレッドボード
- ユニバーサル基板
- 接続用ケーブル

## 使用方法
### 接続
<img src="https://user-images.githubusercontent.com/72370342/104086478-bf6e0880-529b-11eb-952d-6e3b5722844c.jpg" width="200px">  

GPIO、抵抗、LED、GNDの順につなぎます。

対応するGPIOとLEDの組み合わせは以下の通りです。  

＜歩行者用＞　　青　GPIO25    
　　　　　　　　赤　GPIO24    
＜車両用＞　　　青　GPIO23    
　　　　　　　　黄　GPIO22    
　　　　　　　　赤　GPIO21    
### 実行
```
git clone https://github.com/masakifukuchi/robosys_device_driver.git  
cd robosys_device_driver
make
sudo insmod myled.ko
sudo chmod 666 /dev/myled0
```
青点灯  
```
echo 1 > /dev/myled0
```
青点滅から赤へ  
```
echo 2 > /dev/myled0
```
全消灯  
```
echo 0 > /dev/myled0
```

## 動画
[![](http://img.youtube.com/vi/YxAS4ktgqR0/0.jpg)](http://www.youtube.com/watch?v=YxAS4ktgqR0 "a")　
## ライセンス
[GNU General Public License v3.0](https://github.com/masakifukuchi/robosys_device_driver/blob/main/LICENSE)
