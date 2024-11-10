# JellyTracker_V0.5.0 FW

JT_V0.5.0で書き込み可能なカスタム済みFW一覧です。

| Folder Name | Origin Repository |  |
| ---- | ---- | ---- |
| JT-V0.5.0-LSM6DSV-sfusion | https://github.com/l0ud/SlimeVR-Tracker-ESP-BMI270/tree/sfusion | 安定版 |
| JT-V0.5.0-sfusion-tuned-mbe | https://github.com/kounocom/SlimeVR-Tracker-ESP/tree/sfusion-tuned-mbe | 実験的 |
| JT-V0.5.0-dynamic-sfusion | https://github.com/kounocom/SlimeVR-Tracker-ESP/tree/dynamic-sfusion | 実験的 |

> [!WARNING]
> JT-V0.5.0-dynamic-sfusionは検証が終了していないため、一時的にリポジトリから外されています。

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

また、sfusion-tuned-mbeFWではCPUクロックが80MHzで耐えられなかったため、180Mhzへと変更されています。

### JT-V0.5.0-LSM6DSV-sfusionでは
FWを書き込んだ初回にのみ6面キャリブレーションが必要です。\
詳しくは[公式ドキュメント](https://docs.slimevr.dev/server/imu-calibration.html#bmi160-with-firmware-v033-and-above-bmi270-lsm6dso-and-lsm6dsv-or-other-sfusion-imus)を御覧ください。\
(このFWは起動時にDeepSleepへと突入するため、シリアルコンソールが一時的に外され、6面キャリブレーションが少しやりにくくなっています！ごめんなさい;;)

### JT-V0.5.0-sfusion-tuned-mbeでは
この6面キャリブレーションが必要ないFWとされています。/
SlimeVRコミュニティでは評価が高いようですが、私はまだ詳しく検証できていません。\
例として、[PandaTrackers](https://github.com/purraricat/SlimeVR-CheeseCake-PandaTrackers/blob/main/docs/LSM6DSV-tips.md)ではMBEは非推奨と書かれています。(2024/11/10時点)\
ただ、SlimeVRのDiscordコミュニティではかなり高評価なので信用していいと思います。