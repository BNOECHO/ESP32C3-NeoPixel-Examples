# ESP32C3 x WS2812 NeoPixel 範例包

一個完整的 Arduino 範例集合，展示如何在 ESP32-C3 上使用 WS2812 可尋址 RGB LED (NeoPixel)。包含從基礎點亮到互動遊戲的四個實用範例。

## 📋 概述

**ESP32C3 NeoPixel 範例包**提供了 4 個現成可用的範例，適合學習和課堂教學：

- 🔴 **Individual Light Up**: 基礎像素控制
- 🌈 **Rainbow**: 彩虹色動畫效果
- 🎨 **Color Blending**: 顏色漸層過渡
- 🎮 **Ball Game**: 按鈕控制的互動遊戲

非常適合作為 Arduino 開發、NeoPixel LED 控制和互動裝置開發的入門教材。

## ⚙️ 硬體需求

- **微控制器**: ESP32-C3 或相容的 Arduino 開發板
- **LED 驅動**: WS2812 可尋址 RGB LED (NeoPixel)
- **腳位連接**: 
  - LED 資料線 → GPIO 3 (預設)
  - 按鈕 (互動範例) → GPIO 4
- **電源**: USB 或外部電源供應

## 📦 安裝

### 方法 1: 使用 Arduino IDE (推薦)

1. 下載本專案為 ZIP 檔案
2. 在 Arduino IDE 中選擇 **Sketch → Include Library → Add .ZIP Library**
3. 選擇下載的 ZIP 檔案
4. Arduino IDE 會自動安裝到 libraries 資料夾

### 方法 2: 手動安裝

1. 下載或複製本專案
2. 將資料夾重新命名為 `2025-ESP32C3-NeoPixel-Examples`
3. 複製到 `Documents/Arduino/libraries/` 資料夾
4. 重啟 Arduino IDE

### 依賴項

- **Adafruit NeoPixel** - Arduino IDE 會在您上傳範例時提示安裝（若未安裝）
  - 也可手動安裝：**Sketch → Include Library → Manage Libraries** → 搜尋 "Adafruit NeoPixel"

## ⚙️ 硬體需求

- **微控制器**: ESP32-C3 或相容的 Arduino 開發板
- **LED 驅動**: WS2812 可尋址 RGB LED (NeoPixel)
- **腳位連接**:
  - LED 資料線 → GPIO 3 (預設)
  - 按鈕 (遊戲範例) → GPIO 4
- **電源**: USB 或外部電源供應

## 📚 範例說明

本套件包含 4 個現成可用的範例，位於 `examples/` 資料夾。

### 1. **BasicColor** - 基礎顏色控制

學習如何點亮單個 LED 並設定顏色。

**功能**: 依序點亮不同顏色的 LED (紅、綠、藍、白)

**檔案**: `examples/BasicColor/basic_color.ino`

**應用**:
- 初學 NeoPixel 的第一步
- 測試 LED 硬體連接
- 學習 RGB 色彩值

### 2. **SequenceLightUp** - 顏色漸層

展示平滑的色彩過渡效果。

**功能**: LED 從紅色漸層轉變為綠色，使用 `map()` 函數實現平滑過渡

**檔案**: `examples/SequenceLightUp/individual_light_up.ino`

**應用**:
- 狀態指示燈設計
- 進度條效果
- 線性插值演示

### 3. **SequenceRainbow** - 彩虹色動畫

展示彩虹色循環效果，使用 HSV 色彩空間。

**功能**: 每顆 LED 展示不同的彩虹色調，範圍橫跨整個色相環

**檔案**: `examples/SequenceRainbow/sequence_rainbow.ino`

**應用**:
- 視覺反饋指示
- 裝飾效果
- HSV 色彩空間學習

### 4. **BallGame** - 互動遊戲

使用按鈕控制的互動遊戲，展示狀態管理和計時。

**功能**:
- 球在 LED 序列中移動
- 按鈕控制球的反彈方向
- 難度逐漸增加，遊戲越來越快
- 綠色區域 (前 3 顆 LED) 是安全區，紅色區域是危險區
- 達到 30ms 速度時獲勝

**硬體需求**: 
- LED: GPIO 3
- 按鈕: GPIO 4

**檔案**: `examples/BallGame/ball_game.ino`

**應用**:
- 互動遊戲開發入門
- 按鈕輸入和狀態管理
- 遊戲邏輯和計時器實現

## 🚀 快速開始

### 步驟 1: 硬體連接

```text
ESP32-C3          WS2812 LED Strip
GPIO 3     ----→  DIN (資料輸入)
GND        ----→  GND
3.3V/5V    ----→  5V (取決於 LED 規格)

(遊戲範例需要)
GPIO 4     ←----  按鈕
GND        ←----  按鈕另一端
```

### 步驟 2: 上傳範例

1. 在 Arduino IDE 中打開任一範例 (例如 `examples/rainbow/rainbow.ino`)
2. 選擇 **Tools → Board → ESP32 → ESP32-C3**
3. 選擇正確的 COM 埠
4. 點擊上傳按鈕 (→)

### 步驟 3: 運行

上傳完成後，您應該會看到相應的 LED 效果!

## 🎨 自訂設定

每個範例都可以根據您的硬體和需求進行修改：

### 修改 LED 數量

```cpp
#define NUMPIXELS 25  // 改為您的 LED 數量
```

### 修改 GPIO 腳位

```cpp
#define PIN 3         // 改為您的資料線腳位
#define BTN_PIN 4     // 按鈕腳位 (遊戲範例)
```

### 調整亮度

```cpp
pixels.setBrightness(100);  // 0-255，預設最亮
```

### 修改顏色

```cpp
// RGB 色彩 (0-255)
pixels.setPixelColor(0, pixels.Color(255, 0, 0));     // 紅色
pixels.setPixelColor(0, pixels.Color(0, 255, 0));     // 綠色
pixels.setPixelColor(0, pixels.Color(0, 0, 255));     // 藍色
pixels.setPixelColor(0, pixels.Color(255, 255, 255)); // 白色
pixels.show();
```

## 📖 Adafruit NeoPixel 常用函數

本套件使用 Adafruit NeoPixel 函式庫。以下是常用的函數：

| 函數 | 說明 |
|------|------|
| `pixels.begin()` | 初始化 NeoPixel，必須在 setup() 中調用 |
| `pixels.setPixelColor(n, color)` | 設定第 n 顆 LED 的顏色 |
| `pixels.Color(r, g, b)` | 建立 RGB 顏色 (0-255) |
| `pixels.ColorHSV(hue)` | 使用 HSV 色彩空間建立顏色 |
| `pixels.show()` | 顯示所有 LED 顏色變更 (必須調用) |
| `pixels.clear()` | 關閉所有 LED |
| `pixels.fill(color, start, count)` | 填滿指定範圍的 LED |
| `pixels.setBrightness(brightness)` | 設定整體亮度 (0-255) |
| `pixels.numPixels()` | 取得 LED 總數 |

## 💡 學習提示

- 每次修改 LED 顏色後都要調用 `pixels.show()` 才會生效
- 使用 `pixels.clear()` 和 `pixels.show()` 可以快速關閉所有 LED
- RGB 顏色值範圍是 0-255，數值越大越亮
- 大量 LED 或高亮度時使用外部電源，避免 USB 供電不穩定

## 🐛 疑難排解

| 問題 | 解決方案 |
|------|--------|
| LED 不亮 | 檢查 GPIO 腳位、USB 連接、LED 供電 |
| 顏色不對或閃爍 | 檢查 LED 型號 (NEO_GRB 或 NEO_RGB)、供電電壓 |
| 遊戲按鈕無反應 | 確認按鈕連接到 GPIO 4、檢查接線 |
| 編譯失敗 | 確認已安裝 Adafruit NeoPixel 函式庫 |

## 📚 資源

- [GitHub 倉庫](https://github.com/etc1290/ESP32C3-NeoPixel-Examples)
- [Adafruit NeoPixel 文檔](https://github.com/adafruit/Adafruit_NeoPixel)
- [ESP32-C3 資料表](https://www.espressif.com/)
- [Arduino 官方網站](https://www.arduino.cc/)

---

**版本**: 1.0.0  
**最後更新**: 2025 年 11 月
