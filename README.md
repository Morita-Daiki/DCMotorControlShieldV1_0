<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [DCモータ制御シールドV1.0](#dc%E3%83%A2%E3%83%BC%E3%82%BF%E5%88%B6%E5%BE%A1%E3%82%B7%E3%83%BC%E3%83%AB%E3%83%89v10)
  - [概要](#%E6%A6%82%E8%A6%81)
    - [ハードウェアの特徴](#%E3%83%8F%E3%83%BC%E3%83%89%E3%82%A6%E3%82%A7%E3%82%A2%E3%81%AE%E7%89%B9%E5%BE%B4)
    - [ソフトウェアの特徴](#%E3%82%BD%E3%83%95%E3%83%88%E3%82%A6%E3%82%A7%E3%82%A2%E3%81%AE%E7%89%B9%E5%BE%B4)
  - [販売](#%E8%B2%A9%E5%A3%B2)
  - [概要図](#%E6%A6%82%E8%A6%81%E5%9B%B3)
  - [内容物](#%E5%86%85%E5%AE%B9%E7%89%A9)
  - [別途ご用意いただく物](#%E5%88%A5%E9%80%94%E3%81%94%E7%94%A8%E6%84%8F%E3%81%84%E3%81%9F%E3%81%A0%E3%81%8F%E7%89%A9)
  - [組立手順](#%E7%B5%84%E7%AB%8B%E6%89%8B%E9%A0%86)
      - [1. 内容物の確認](#1-%E5%86%85%E5%AE%B9%E7%89%A9%E3%81%AE%E7%A2%BA%E8%AA%8D)
      - [2. モーターマウントの取り付け](#2-%E3%83%A2%E3%83%BC%E3%82%BF%E3%83%BC%E3%83%9E%E3%82%A6%E3%83%B3%E3%83%88%E3%81%AE%E5%8F%96%E3%82%8A%E4%BB%98%E3%81%91)
      - [3. エンコーダ用磁石の取り付け](#3-%E3%82%A8%E3%83%B3%E3%82%B3%E3%83%BC%E3%83%80%E7%94%A8%E7%A3%81%E7%9F%B3%E3%81%AE%E5%8F%96%E3%82%8A%E4%BB%98%E3%81%91)
      - [4. プーリーの取り付け](#4-%E3%83%97%E3%83%BC%E3%83%AA%E3%83%BC%E3%81%AE%E5%8F%96%E3%82%8A%E4%BB%98%E3%81%91)
      - [5. モータの取り付け](#5-%E3%83%A2%E3%83%BC%E3%82%BF%E3%81%AE%E5%8F%96%E3%82%8A%E4%BB%98%E3%81%91)
      - [6. シールドのスタック](#6-%E3%82%B7%E3%83%BC%E3%83%AB%E3%83%89%E3%81%AE%E3%82%B9%E3%82%BF%E3%83%83%E3%82%AF)
  - [サンプルプログラム](#%E3%82%B5%E3%83%B3%E3%83%97%E3%83%AB%E3%83%97%E3%83%AD%E3%82%B0%E3%83%A9%E3%83%A0)
      - [SW4STM32](#sw4stm32)
      - [mbed](#mbed)
      - [デモ動画](#%E3%83%87%E3%83%A2%E5%8B%95%E7%94%BB)
  - [サンプルプログラムの利用方法](#%E3%82%B5%E3%83%B3%E3%83%97%E3%83%AB%E3%83%97%E3%83%AD%E3%82%B0%E3%83%A9%E3%83%A0%E3%81%AE%E5%88%A9%E7%94%A8%E6%96%B9%E6%B3%95)
    - [出力結果例](#%E5%87%BA%E5%8A%9B%E7%B5%90%E6%9E%9C%E4%BE%8B)
  - [制御性能の改善](#%E5%88%B6%E5%BE%A1%E6%80%A7%E8%83%BD%E3%81%AE%E6%94%B9%E5%96%84)
  - [FAQ](#faq)
      - [Q. 電源投入時、"EncErr" LEDが点灯する](#q-%E9%9B%BB%E6%BA%90%E6%8A%95%E5%85%A5%E6%99%82encerr-led%E3%81%8C%E7%82%B9%E7%81%AF%E3%81%99%E3%82%8B)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# DCモータ制御シールドV1.0
<img src="/images/Product_photo.jpg" width="300px">

## 概要
DCモータ制御シールドV1.0は、ブラシ付きDCモータFA-130RAの位置/速度/トルク制御が可能なNucleo-64用シールドです。  
「モータ制御のプログラムの中身はどうなっているのか」や、「どのゲインを調整することで制御性能が改善されるのか」といった制御の学習にご利用いただけます。  
電子部品は全て実装済みではんだ付けが不要であるため、組立に大きな労力を割く必要がなくモータ制御の学習に集中できます。また、サンプルプログラムは[mbed](https://developer.mbed.org/users/y2kb/code/DCMotorControlShieldV1_0/)および System workbench for STM32(SW4STM32) の2種類の環境で提供しており、お好みの環境で学習することができます。

### ハードウェアの特徴
- 12-bit(4096)/回転の高分解能な磁気式エンコーダAS5600を搭載
- ユーザーが使用可能な半固定抵抗を4個用意しており、プログラムを書き換えることで指令値やゲインを動的に変動させるといったことが可能
- モータの電源はNucleoに接続したUSB端子からの供給もしくはシールド上のUSB端子からの供給のどちらかを選ぶことが可能

### ソフトウェアの特徴
- サンプルプログラムの制御系は位置/速度制御を行う加速度メジャーループ(制御周期200us)と電流マイナーループ(制御周期50us)のカスケード制御方式を採っており、いずれの制御器も全てソフトウェアで構成しているため、制御器の全てのゲインにアクセス可能
- 指令値や応答値、ゲインなどのパラメータはNucleo上のST-Linkを通じてPCに送ることができ、ターミナル([Tera Term](https://osdn.net/projects/ttssh2/))やシリアルプロッタ(例：[Arduino IDE](https://www.arduino.cc/en/Main/Software)、[CPLT](http://www.datatecno.co.jp/cplt/cplt-download.htm))を使用することでリアルタイムにパラメータを表示可能
- 制御系が不安定になりモータが暴走した際は自動的にモータと制御演算を停止する発散防止機能を搭載

## 販売  
[スイッチサイエンス委託販売ページ](https://www.switch-science.com/catalog/3459/)
※大量注文や在庫に関する問い合わせは[こちら](mailto:info.y2kb@gmail.com)までご連絡ください。  

## 概要図
<img src="/images/Overview.jpg" width="600px">

## 内容物
<img src="/images/Package_contents.jpg" width="600px">  

**<span style="color: red; ">※ なべ小ネジ・平ワッシャは予め一体になっている「座金組み込みねじ」の場合があります。</span>**  

## 別途ご用意いただく物
- **Nucleo-64ボード**  
  動作確認済：[NUCLEO-F411RE](http://www.st.com/en/evaluation-tools/nucleo-f411re.html)  
  (購入先：[スイッチサイエンス](https://www.switch-science.com/catalog/2098/) 等)  

- **マブチ DCモーター FA-130RA**  
  **<span style="color: red; ">※ 「モーターベース・二段式プーリー付」 のものをご用意ください。</span>**  
  (購入先：[ヨドバシカメラ](http://www.yodobashi.com/product/100000001001281039/)、[千石電商](http://www.sengoku.co.jp/mod/sgk_cart/detail.php?code=EEHD-0A3G) 等)  

## 組立手順  
#### 1. 内容物の確認  
内容物が全て入っているか確認します。特にネオジム磁石は見落としがちなので注意してください。
組立に必要な全物品は以下の図になります。  
<img src="/images/Requirements.jpg" width="350px">

#### 2. モーターマウントの取り付け  
マブチ DCモーター FA-130RAに入っているモータマウントを基板裏側から、ナット - 基板 - モータマウント - 平ワッシャ - 小ネジ の順になるように固定してください。このとき、モータマウントの向きに注意し、モータマウントの外形が基板のシルクに沿うようにしてください。  
<img src="/images/Assemble_MotorMount.jpg" width="350px">

#### 3. エンコーダ用磁石の取り付け  
マブチ DCモーター FA-130RAに入っている2段プーリーに両面テープや瞬間接着剤を用いて磁石を取り付けます。このとき磁石はしっかりと固定してください。固定が不十分な状態ですと制御発散時等に磁石が外れる可能性があります。また、プーリーと磁石の中心のズレが1mm以内(可能であれば0.25mm以内)に収まるようにしてください。ズレが大きいと位置情報の読み取りエラーや取得する位置情報の精度悪化に繋がります。  
<img src="/images/Assemble_Pulley_Magnet.jpg" width="200px">

#### 4. プーリーの取り付け  
モータの出力軸にプーリーを取り付けます。このとき、モータの外装部とプーリーが接触しない程度にプーリーを挿しこんでください。  
<img src="/images/Assemble_Motor_Pulley.jpg" width="350px">

#### 5. モータの取り付け  
モータをモータマウントに取り付け、モータの配線をターミナルに取り付けます。
配線がショートしないよう被覆が剥かれた部分をニッパ等で適切な長さに切った後、ターミナルに配線を挿しこんで固定します。
このとき、ターミナルに取り付ける配線の色に注意してください。  
<img src="/images/Assemble_Motor.jpg" width="300px">


#### 6. シールドのスタック  
Nucleo上のArduinoコネクタにシールドをスタックすると組立完了です。  
<img src="/images/Stack_Nucleo.jpg" width="400px">

## サンプルプログラム

### 説明書  
https://y2kblog.github.io/DCMotorControlShieldV1_0/

#### SW4STM32  
  本ページの"Software"フォルダ内にあります

#### mbed  
  [DCMotorControlShieldV1_0](https://developer.mbed.org/users/y2kb/code/DCMotorControlShieldV1_0/)

※HALライブラリ、FreeRTOS、CMSIS-OS等のライブラリ以外の
プログラムはMITライセンスです。

コンパイル済みのバイナリを"Software\Nucleo-F411RE\Nucleo-F411RE_Sample.bin"に用意しています。NucleoをPCに接続し、USBデバイスとして認識されているNucleoにこのバイナリファイルをドラッグ＆ドロップすることでサンプルプログラムを書き込むことができ、簡単に動作確認が行えます。

#### デモ動画

※動画をクリックするとYoutubeに飛びます。  
[![サンプルプログラムの動作デモ](images/demo.gif)](http://www.youtube.com/watch?v=jYBmyjHmTwM)


サンプルプログラムでは制御ON時に位置指令値と位置応答値を出力しています。
この値をリアルタイムで確認するため、上の動画では
[CPLT](http://www.datatecno.co.jp/cplt/cplt-download.htm)
というCOMポートから受信したデータをグラフ化するWindows用のフリーソフトを用いて表示しています。
このデモで用いたCPLTの設定ファイルは"Software"ディレクトリの"CPLT_Config.CFG"です。
なお、COMポート番号はボード毎に異なるため、デバイスマネージャなどでNucleoのCOMポート番号を確認し各自再設定する必要があります。

## サンプルプログラムの利用方法

大半のユーザーはモータ制御の設定とパラメータ出力に関わる"Src/control.c"内の以下の変数・関数の参照や変更で十分だと思われるのでこれらの説明を以下の表にまとめます。

変数/関数名  |  説明
--|--
`float Param1, Param2, Param3, Param4;` |  シールド上の4つの可変抵抗の値がそれぞれ格納されています。値の範囲は0.0～1.0であり、時計回りに回すと値が増加します。
`static void MajorControlLoop(void)` |  加速度メジャーループ(制御周期：200[us])<br>ユーザーはこの関数内で位置/速度/トルク制御といったモードや指令値・ゲインを変更できます。<br>また、電流制御の使用可否やゲインも設定できます。
`static void MinorControlLoop(void)`  |  電流マイナーループ(制御周期：50[us])
`static void PositionControl(float PosCmd, float VelCmd, float P_Gain, float I_Gain, float D_Gain)`  |  位置制御モードに設定する関数<br>引数は順に、位置指令値、速度指令値(位置指令値の微分値)、Pゲイン、Iゲイン、Dゲイン
`static void VelocityControl(float VelCmd, float P_Gain, float I_Gain)`  |  速度制御モードに設定する関数<br>引数は順に、速度指令値、Pゲイン、Iゲイン
`static void TorqueControl(float Command)`  |  トルク制御モードに設定する関数<br>引数はトルク指令値
`static void configCurrentControl(bool isEnabled, float P_Gain, float I_Gain)`  |  電流マイナーループの設定<br>引数は順に、電流マイナーループの使用可否、Pゲイン、Iゲイン
`void SerialCommunicationTask(void const *argument)`  |  低優先度のUARTによるシリアル通信タスク<br>この関数内の`printf`関数を書き換えることでNucleo上のST-Linkを介してPCに各種パラメータ(例：指令値、応答値、ゲイン)を送信できる

その他の詳細は[サンプルプログラムの説明書](https://y2kblog.github.io/DCMotorControlShieldV1_0/)を参照してください。

### 出力結果例
サンプルプログラムは位置指令モード、位置指令値は矩形波と正弦波を周期的に繰り返すようなプログラムになっており、シリアルプロッタを用いて以下に示すようにステップ応答と1[Hz]の周波数応答を得ることができます。  
<img src="/images/Result_Default.png" width="500px">

## 制御性能の改善

制御性能を高めるためには、モータが目標値に素早く応答する目標値応答特性と、制御系のモデル化誤差やパラメータ変動、負荷トルクといった外乱による影響を抑圧して応答する外乱抑圧応答特性を同時に向上する必要があります。  
さて、サンプルプログラムでは位置制御器にはPID制御器、速度制御器にはPI制御器、電流制御器にはPI制御器を搭載しています。こうした古典的な制御器は
指令値と応答値の偏差のみからモータ出力参照値を生成する1自由度制御であり、1つのパラメータ(偏差)を用いて目標値応答特性と外乱抑圧応答特性の向上という2つの目標を達成しようとしているため、上記の目標値応答特性と外乱抑圧応答特性はトレードオフの関係になっており、様々なゲインチューニング法を用いて良好なゲインを設定することで制御性能をある程度までは高められますが、それでも頭打ちになってしまいます。  
この問題に対し、未知の外乱やパラメータ変動による不安定化が起こりにくいロバスト制御と呼ばれる制御手法があります。代表的なロバスト制御手法にはH∞制御(H Infinity control)がありますが、ここでは容易に実装でき、かつ強力に外乱を抑圧できる「外乱オブザーバ (Disturbance observer : DOB)」を用いて制御を行ってみます。  
外乱オブザーバとはモータ出力参照値(系への入力)とモータの応答値(系の出力)から外乱を推定する観測器であり、推定した外乱をフィードバックすることで外乱による影響を抑圧することができます。外乱オブザーバを付加することで、位置/速度制御器の目標値応答特性とは独立して外乱抑圧応答特性を高めることができます。すなわち、2自由度制御系を構成でき、未知外乱に強いロバストな加速度制御系を実現できます。  
以下に外乱オブザーバを実装した場合の応答値を示します。なお、位置制御器のP、Dゲインはサンプルプログラムと同等にし、Iゲインは0 (外乱オブザーバにI制御要素が含まれるため)、外乱オブザーバのカットオフ周波数は500[rad/sec]としました。  
<img src="/images/Result_withDOB.png" width="500px">  
先の項のサンプルプログラムの出力結果と比較して、応答値がしっかりと目標値に追従していることがわかります。

参考：[外乱オブザーバによるロバスト・モーションコントロール](https://www.jstage.jst.go.jp/article/jrsj1983/11/4/11_4_486/_article/-char/ja/)

## FAQ

#### Q. 電源投入時、"EncErr" LEDが点灯する  
A. エンコーダの磁石読取りエラーです。NucleoをPCに接続しターミナル等を用いるとエラーメッセージが表示されます。エラーは三種類あります。  
- `Magnet was not detected` : 磁石が検出されていません。プーリーに磁石が付いているか確認してください。
- `Magnet too weak` : 磁力が弱すぎるというエラーです。プーリーのはめ込み量を調整し、磁石をエンコーダICに近づけてください。
- `Magnet too strong` : 磁力が強すぎるというエラーです。プーリーのはめ込み量を調整し、磁石をエンコーダICから遠ざけてください。
