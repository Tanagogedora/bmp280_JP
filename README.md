# BMP280 Sensor Extension for micro:bit
# micro:bit 用 BMP280 センサー拡張機能

> ⚠️ **この拡張機能は現在ベータ版です。動作確認中の機能が含まれます。ご使用の際はご注意ください。**

This extension allows the micro:bit to communicate with a BMP280 digital pressure and temperature sensor via I2C.  
You can measure atmospheric pressure and temperature.  
Sensor values are based on the official BMP280 datasheet.

この拡張機能は、BMP280 デジタル気圧・気温センサーを micro:bit の MakeCode 上で利用するためのものです。  
気圧と気温の測定が可能です。センサー仕様は BMP280 のデータシートに基づいています。

✅ This extension is **bilingual**: all block definitions and documentation are provided in both **English and Japanese**.  
✅ この拡張機能は、すべてのブロック定義および説明が **日本語と英語の併記**により構成され、多言語に対応しています。


> 🔗 **Demo Page:**デモページを見る: [https://tanagogedora.github.io/bmp280betaVrJP/](https://tanagogedora.github.io/bmp280betaVrJP/)

---
## 📦 How to Use / 使い方

### As a MakeCode Extension / MakeCode 拡張機能としての使用方　
1. Open [https://makecode.microbit.org/](https://makecode.microbit.org/)
1. Create a new project
1. Click the gear icon (⚙) → "Extensions"
1. Paste the following URL to add the extension  
   `https://github.com/tanagogedora/bmp280betaVrJP`   

---

1. MakeCode [https://makecode.microbit.org/](https://makecode.microbit.org/)を開く
1. 「新しいプロジェクト」をクリック
1. 画面右上のギアボタン（⚙）をクリックし、「拡張機能」を選択 
1. 下記の URL を検索または貼り付けてインポート    
   `https://github.com/tanagogedora/bmp280betaVrJP` 

### 🖼 Example / 使用例 

🎯 The following sample (block/script) performs the following actions:
- Connects the BMP280 weather sensor to the micro:bit via I2C (address: `0x77`).
- Initializes the BMP280 so it can measure temperature and atmospheric pressure.
- **Pressing button A** displays the **temperature** (in Celsius, with one decimal place) on the micro:bit LED.
- **Pressing button B** displays the **air pressure** (in hPa, with one decimal place) on the micro:bit LED.

🎯 次のサンプル（ブロック／スクリプト）は、以下のような動作を行います：
- I2C接続により、気象センサー BMP280 と micro:bit が接続されます（アドレス：`0x77`）。
- BMP280 が有効化され、気温・気圧の測定が可能になります。
- **ボタンA** を押すと、micro:bit のLEDに **気温（摂氏・小数第1位）** が表示されます。
- **ボタンB** を押すと、micro:bit のLEDに **気圧（hPa・小数第1位）** が表示されます。


#### 🧱　Sample Blocks / ブロックの使用例
English
<br>
<img src="https://github.com/Tanagogedora/bmp280betaVrJP/raw/main/Blockeg.png" width="600" alt="MakeCode blocks (English UI)">
<br>

日本語
<br>
<img src="https://github.com/Tanagogedora/bmp280betaVrJP/raw/main/Blockjp.png" width="600" alt="ブロック構成例">
<br>

#### 💻 Sample Code / JavaScriptサンプル
```javascript
BMP280.Address(BMP280.BMP280_I2C_ADDRESS.ADDR_0x77)  
BMP280.PowerOn()  
input.onButtonPressed(Button.A, function () {  
    basic.showString("" + BMP280.temperature(BMP280.BMP280_T.T_C) + "C")  
})  
input.onButtonPressed(Button.B, function () {  
    basic.showString("" + BMP280.pressure(BMP280.BMP280_P.hPa) + "hPa")  
})  

```

---

### ✏️ To modify the extension source code in MakeCode /  MakeCode 上で編集 : 

1. Open [https://makecode.microbit.org/](https://makecode.microbit.org/)
1. Click "Import" → "Import URL"
1. Paste this URL
`https://github.com/tanagogedora/bmp280betaVrJP`  

--- 

1. MakeCode [https://makecode.microbit.org/](https://makecode.microbit.org/) を開く
1. 「読み込む」→「URLから読み込む…」を選択
1. 以下の URL を貼り付けてインポート :  
   `https://github.com/tanagogedora/bmp280betaVrJP`

---

## 🧪 Sensor Specification (Based on Datasheet) / 測定仕様（参考：データシートより）

| Measurement(測定対象) | Range(範囲) | Accuracy(精度) | Resolution(分解能) |
|-----------|------------------|-------------------|--------------------|
| Pressure(気圧) | 300 ～ 1100 hPa | ±1.0 ～ 1.7 hPa | ±0.16 Pa |
| Temperature(気温) | -40 ～ +85 ℃ | ±0.5 ～ 1.0 ℃ | ±0.01 ℃ |

※ 上記の値は BMP280 の公式データシートに基づく参考値です。

## 📝 Acknowledgement　/　謝辞・ベースとなった実装について

This extension is based on the BME280 TypeScript implementation originally developed by the microbit/micropython Chinese community (2018).  
However, due to differences in initialization and control flow, this version has been re-implemented specifically for the BMP280 sensor.  
We adapted and extended it for use in Japanese educational contexts, adding Japanese block support and improved decimal precision for science experiments.

Original Source: http://www.micropython.org.cn

本拡張機能は、microbit/micropython 中国コミュニティ（2018年）による BME280 TypeScript 実装をもとに開発しています。  
ただし、BME280 向け実装とは初期化方法や制御仕様が異なるため、本拡張機能は BMP280 専用として新たに移植・再構築されたものです。  
日本の教育現場での利用を想定し、ブロックの日本語対応や小数点精度での測定機能も追加しています。

元コード提供元（参考）：http://www.micropython.org.cn

## 📝 Version Info / バージョン情報

| Version/バージョン | Release Date/公開日 | Notes/備考 |
|---------|--------------|-------|
| **1.10** | 2025-04-02   | Public version. Multilingual, README improvements, bug fixes.<br>公開版。多言語併記・README改善、バグ修正 |
| **1.00** | 2025-03-26   | First release Japanese support (Beta)<br>初回リリース 日本語対応（ベータ） |  



## 📝 License / ライセンス

© 2025 Tanagotti  
Based on BME280 code by the microbit/micropython Chinese community (2018)  
Original Source: http://www.micropython.org.cn  
（元コード：microbit/micropython 中国コミュニティによる BME280 実装）

### [参考]　📄 [日本語版ライセンスはこちら（日本語ライセンスを読む（GitHub Pages））](https://tanagogedora.github.io/bmp280betaVrJP/license_jp.html)

---

## 🔍 MakeCode Rendering Metadata / メタデータ（MakeCode レンダリング用）

```html
<script src="https://makecode.com/gh-pages-embed.js"></script>
<script>
makeCodeRender("{{ site.makecode.home_url }}", "{{ site.github.owner_name }}/{{ site.github.repository_name }}");
</script>

