# Right Keyboard - ZMK Firmware

Xiao nRF52840を使用したカスタムキーボードのZMKファームウェアです。

## 仕様

- **マイコン**: Seeed Studio Xiao BLE (nRF52840)
- **キー数**: 24キー (6列×3行 + 3キー)
- **機能**: 
  - Bluetooth LE接続
  - USB接続
  - OLEDディスプレイ対応
  - バッテリー監視
  - スリープモード

## キー配列

```
Row 0: [Q] [W] [E] [R] [T] [Y]
Row 1: [A] [S] [D] [F] [G] [H]
Row 2: [Z] [X] [C] [V] [B] [N]
Row 3:     [GUI] [LWR] [SPC]
```

## ピン配置

### 列（Column）ピン
- col0: D6 (TX)
- col1: D7 (RX)
- col2: D8 (SCL)
- col3: D9 (SDA)
- col4: D10 (MISO)
- col5: D5

### 行（Row）ピン
- row0: D0
- row1: D1
- row2: D2
- row3: D3

### I2C (OLED)
- SCL: D8
- SDA: D9

## ビルド方法

### GitHub Actions（推奨）

1. このリポジトリをGitHubにプッシュ
2. GitHub Actionsが自動的にファームウェアをビルド
3. Actionsタブからファームウェア（.uf2ファイル）をダウンロード

### ローカルビルド

```bash
# ZMK開発環境のセットアップ
west init -l config/
west update
west zephyr-export

# ビルド
west build -b xiao_ble -- -DSHIELD=right

# ファームウェアのフラッシュ
# 1. Xiao nRF52840をブートローダーモードにする（RSTを2回押す）
# 2. build/zephyr/zmk.uf2をXIAOドライブにコピー
```

## レイヤー構成

### Layer 0 (デフォルト)
基本的な文字入力レイヤー

### Layer 1 (Lower)
数字、矢印キー、Bluetooth設定

### Layer 2 (Raise)
記号、特殊文字

## カスタマイズ

キーマップを変更する場合は `config/right.keymap` を編集してください。

## ライセンス

MIT License
