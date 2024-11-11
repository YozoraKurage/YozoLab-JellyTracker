# JellyTracker_V0.5.0

JT_V0.5.0は動作確認済みです！

この基板では、ESP32-C3-WROOM-02-N4とLSM6DSVのモジュールを利用して作るトラッカーです。

白猫屋さんのこのLSM6DSVモジュールでの動作を確認済みです。\
https://booth.pm/ja/items/5606882

![alt text](pic/JT_V0.5.0_001.png)

# JellyTracker_V0.5.0 FW

JT_V0.5.0で書き込み可能なカスタム済みFW一覧です。

> [!NOTE]
> FWデータは[JellyTracker-FW](https://github.com/YozoraKurage/JellyTracker-FW)リポジトリに移動しました！

| Branch Name | Repository |  |
| ---- | ---- | ---- |
| sfusion-tuned-mbe_V0.5.0 | https://github.com/YozoraKurage/JellyTracker-FW/tree/sfusion-tuned-mbe_V0.5.0 | 安定版 |
| dynamic-sfusion_V0.5.0 | https://github.com/YozoraKurage/JellyTracker-FW/tree/dynamic-sfusion_V0.5.0 | 実験的 |

## How to Flash FW
JT-V0.5.0であれば、[YozoraLaboratory ESPTool](https://jt-webflash.yozolab.net/)からWeb上でのFW書き込みが可能です。\
カスタマイズしたい場合はそれぞれFWをダウンロードしてお使いください。

## Topics

JT-V0.5.0のFWはすべて、Ni-MH1本での運用に対応するために
- 電源投入時にDeepSleepへ入る処理(RFキャリブレーションのスキップ)
- WiFiの出力強度の変更(2dbm)
- CPUクロック数の変更(80MHz)

が行われています。\
これらは主に省電力化、電源投入時の突入電流対策です。

また、sfusion-tuned-mbeではCPUクロックが80MHzで耐えられなかったため、180Mhzへと変更されています。

## 各FWについて

### sfusion-tuned-mbe_V0.5.0では
FWを書き込んだ初回にのみ6面キャリブレーションが必要です。\
詳しくは[公式ドキュメント](https://docs.slimevr.dev/server/imu-calibration.html#bmi160-with-firmware-v033-and-above-bmi270-lsm6dso-and-lsm6dsv-or-other-sfusion-imus)を御覧ください。\
(このFWは起動時にDeepSleepへと突入するため、シリアルコンソールが一時的に外され、6面キャリブレーションが少しやりにくくなっています！ごめんなさい;;)

### dynamic-sfusion_V0.5.0では
これは6面キャリブレーションが必要ないFWです。\
現在実験中！\
~~例として、[PandaTrackers](https://github.com/purraricat/SlimeVR-CheeseCake-PandaTrackers/blob/main/docs/LSM6DSV-tips.md)ではMBEは非推奨と書かれています。(2024/11/10時点)~~\
彼はSlimeVR Discordコミュニティから正当な理由によってBANされているようでした...