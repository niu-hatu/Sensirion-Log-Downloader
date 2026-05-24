# SHT4x Temperature & Humidity Logger — Operator Guide

> Downloads logged temperature and humidity data from Sensirion SHT43 DemoBoards
> via Bluetooth and saves them as CSV files.

---

## Requirements

- Windows 10/11 with Bluetooth LE support
- Bluetooth turned ON in Windows Settings
- SHT43 DemoBoard(s) with batteries inserted

---

## First-Time Setup

When launching for the first time on a new PC, Windows may block the app:

1. **Windows SmartScreen warning** — "Windows protected your PC"
   - Click **"More info"**
   - Click **"Run anyway"**
   - This only happens once; Windows remembers your choice.

2. **Windows Firewall prompt** (if shown)
   - Click **"Allow access"** — the app uses Bluetooth, not network, but Windows may still ask.

3. **"Unblock" the file** (if the app won't start at all)
   - Right-click `SHT4x_Logger.exe` → Properties
   - At the bottom, check **"Unblock"** → click OK

4. **Bluetooth pairing consent**
   - On first connection to each board, Windows shows a Bluetooth pairing notification.
   - A 6-digit PIN appears on screen AND on the board's LCD.
   - **Press the button on the board** to confirm pairing.

After the first successful run, none of the above steps are needed again.

---

## Quick Start

1. Insert batteries into all boards.
2. Press the button on each board to wake it up (boards sleep after ~30 seconds).
3. Double-click `SHT4x_Logger.exe`
4. The **Live Data** panel shows real-time temperature and humidity from nearby boards (no connection required).
5. Select a specific board from the dropdown, or leave as **All** to download from all boards.
6. Click **Start / 開始** to download stored data.
7. CSV files are saved in the output folder shown in the app.

---

## Setting the Logging Interval

1. Select an interval from the dropdown (10s, 30s, 1m, 5m, 10m, 1h).
2. Optionally select a specific board from the board selector.
3. Click **Start / 開始** — the app downloads data first, then writes the new interval.
4. A confirmation message appears in the log: `✓ Interval set to 30s`

> ⚠️ Setting a new interval erases all stored data on the board. The app always downloads data first to avoid data loss.

---

## Live Data

The app passively monitors BLE advertisements from nearby boards and displays:
- Board ID (e.g., D206)
- Temperature (°C)
- Humidity (%RH)
- Timestamp of last reading

No connection is needed — live data is broadcast automatically. Multiple boards are shown simultaneously.

---

## Board Notes

Each board in the live data panel has an editable text field for adding a note (e.g., location, purpose).
Notes are saved automatically to `board_notes.txt` in the app folder and restored on next launch.

---

## Tips

- Press board buttons **right before** clicking Start. Boards sleep after ~30 seconds.
- If a board shows "NO DATA", press its button and click Start again.
- The app handles multiple boards automatically. Each board is identified by a 4-character chip ID (e.g., D206, CF06).
- Use the board selector to target a specific board for download or interval changes.
- CSV files are named: `sht43_<ChipID>_<date>_<time>.csv`

---

## CSV Format

```
Date,Time,Temperature_C,Humidity_pct
2026-03-24,16:10:29,23.45,42.31
2026-03-24,16:11:29,23.48,42.15
```

---

## Troubleshooting

| Message | Solution |
|---------|----------|
| "No boards found" | Press the button on each board, then retry. Check Bluetooth is ON. |
| "Board unreachable" | Board is asleep. Press its button and retry. |
| "Pairing failed" | Remove battery, wait 10s, reinsert, press button, retry. |
| "No Bluetooth adapter" | PC has no Bluetooth hardware or driver is missing. |

---

## Log File

Debug information is saved to `sht4x_logger.log` (same folder as the exe).
Include this file when reporting issues.

---
---

# SHT4x 温湿度ロガー — 操作ガイド

> Sensirion SHT43 DemoBoard から Bluetooth 経由で温湿度ログデータを
> ダウンロードし、CSVファイルとして保存します。

---

## 必要条件

- Windows 10/11（Bluetooth LE対応）
- WindowsでBluetoothをONにしてください
- 電池を入れたSHT43 DemoBoard

---

## 初回セットアップ

新しいPCで初めて起動する場合、Windowsがアプリをブロックすることがあります：

1. **Windows SmartScreen 警告** —「WindowsによってPCが保護されました」
   - **「詳細情報」** をクリック
   - **「実行」** をクリック
   - この警告は初回のみ表示されます。

2. **Windowsファイアウォール** （表示された場合）
   - **「アクセスを許可」** をクリック

3. **ファイルのブロック解除**（アプリが起動しない場合）
   - `SHT4x_Logger.exe` を右クリック → プロパティ
   - 下部の **「ブロックの解除」** にチェック → OK

4. **Bluetoothペアリング確認**
   - 各ボードへの初回接続時、6桁のPINコードが画面とLCDに表示されます。
   - **ボードのボタンを押して** ペアリングを確認してください。

初回の設定完了後、以降はこれらの手順は不要です。

---

## クイックスタート

1. 全てのボードに電池を入れてください。
2. 各ボードのボタンを押して起動（約30秒後にスリープ）。
3. `SHT4x_Logger.exe` をダブルクリック
4. **ライブデータ**パネルに近くのボードの温湿度がリアルタイム表示されます（接続不要）。
5. ドロップダウンから特定のボードを選択、または**All**で全ボードをダウンロード。
6. **「Start / 開始」** をクリックしてデータをダウンロード。
7. CSVファイルはアプリに表示された出力フォルダに保存されます。

---

## ロギング間隔の設定

1. ドロップダウンから間隔を選択（10秒、30秒、1分、5分、10分、1時間）。
2. 必要に応じて特定のボードを選択。
3. **「Start / 開始」** をクリック — データを先にダウンロードしてから新しい間隔を書き込みます。
4. ログに確認メッセージが表示されます：`✓ Interval set to 30s`

> ⚠️ 新しい間隔を設定するとボード上の全データが削除されます。アプリはデータ損失を防ぐため、必ず先にダウンロードします。

---

## ライブデータ

アプリは近くのボードのBLEアドバタイズを受動的に監視し、以下を表示します：
- ボードID（例：D206）
- 温度（°C）
- 湿度（%RH）
- 最終受信時刻

接続不要 — ライブデータは自動的にブロードキャストされます。複数ボードを同時に表示可能。

---

## ボードメモ

ライブデータの各ボードには編集可能なメモ欄があります（例：設置場所、用途）。
メモはアプリフォルダの `board_notes.txt` に自動保存され、次回起動時に復元されます。

---

## ヒント

- 「Start」をクリックする **直前に** ボードのボタンを押してください。
- 「NO DATA」と表示された場合、そのボードのボタンを押して再度Startをクリック。
- 複数ボードを自動処理します。各ボードは4文字のチップID（例：D206, CF06）で識別。
- ボードセレクタで特定のボードを選択して、ダウンロードや間隔変更を行えます。
- CSVファイル名：`sht43_<チップID>_<日付>_<時刻>.csv`

---

## CSVフォーマット

```
Date,Time,Temperature_C,Humidity_pct
2026-03-24,16:10:29,23.45,42.31
2026-03-24,16:11:29,23.48,42.15
```

---

## トラブルシューティング

| メッセージ | 対処法 |
|------------|--------|
| "No boards found" | 各ボードのボタンを押して再試行。BluetoothがONか確認。 |
| "Board unreachable" | ボードがスリープ中。ボタンを押して再試行。 |
| "Pairing failed" | 電池を抜いて10秒待ち、再挿入してボタンを押す。 |
| "No Bluetooth adapter" | PCにBluetooth機能がないかドライバ未インストール。 |

---

## ログファイル

デバッグ情報は `sht4x_logger.log`（exeと同じフォルダ）に保存されます。
問題報告時にこのファイルを添付してください。

---

*v2.6 | 2026-05-23 | Sensirion SHT43 DemoBoard*

---
---

# Firmware Reference (Developer Notes)

## Source & Documentation

| Resource | URL |
|----------|-----|
| Firmware source | https://github.com/Sensirion/sht43-demoboard-ble-firmware |
| Arduino BLE Gadget (protocol ref) | https://github.com/Sensirion/arduino-ble-gadget |
| Doxygen docs | https://sensirion.github.io/sht43-demoboard-ble-firmware/ |
| BLE services spec | https://github.com/Sensirion/ble-services (ble-services.yml) |
| Official app | Sensirion MyAmbiance (iOS / Android) |

## Hardware

- MCU: STM32WB55RG (dual-core: M4 app + M0+ BLE stack)
- Sensor: SHT43 (I2C, CRC-8 on data)
- Storage: External QSPI flash (log-structured item store)
- Battery: CR2032 coin cell

## BLE GATT Services

### Data Logger Service `00008000-b38d-4985-720e-0f993a68ee41`

| Char | UUID (short) | Access | Data | Notes |
|------|---|---|---|---|
| Logging interval | 0x8001 | R/W | uint32 ms (LE) | Min 10s, granularity 10s. **Changing value erases stored samples.** |
| Available samples | 0x8002 | R | uint16 | Sample count |
| Requested samples | 0x8003 | R/W | uint16 | Set before subscribe to 0x8004 |
| Data transfer | 0x8004 | Notify | uint8[20] | Subscribe triggers download |

### Device Settings Service `00008100-b38d-4985-720e-0f993a68ee41`

| Char | UUID (short) | Access | Data | Notes |
|------|---|---|---|---|
| Version | 0x81FF | R | uint8 | Settings schema version |
| Alt device name | 0x8120 | R/W | string[32] | Rename the board |
| Debug log (UART) | 0x81FE | R/W | bool | Enable UART trace (drains battery) |
| Advertise data | 0x8130 | R/W | bool | Enable sensor data in adverts |

### Reboot Service `e6686821-f5b0-417f-aa27-89d1a1ae5425`

| Char | UUID | Access | Data | Notes |
|------|---|---|---|---|
| Reboot request | 0000fe11-8e22-... | Write-no-resp | uint8[3] | See below |

**Reboot request bytes:**
- `byte[0]`: Boot mode — `0` = normal app, `1` = OTA bootloader
- `byte[1]`: First flash sector to erase (7 for app firmware)
- `byte[2]`: Number of sectors to erase (0–57; settings start at page 65)

Normal reboot: `{0x00, 0x00, 0x00}`
Enter OTA mode: `{0x01, 0x07, <sectors>}`
