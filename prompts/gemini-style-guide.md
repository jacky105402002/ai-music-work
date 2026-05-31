# Gemini 圖片生成風格指南

## 全域風格字串

每個提示詞結尾都貼上這段：

```
cinematic still, film grain, soft depth of field, Taiwan indie MV aesthetic, muted warm tones, emotional and nostalgic mood, 16:9
```

---

## 色調字串

### 室內（辦公室）
```
warm amber office lighting, 2700K tungsten glow, late night office atmosphere
```

### 室外（夜晚街道/城市）
```
cool blue night cityscape, city lights bokeh, nighttime street
```

### 回憶閃回
```
warm overexposed nostalgic tones, slightly washed-out film style, faded warm colors
```

### 黃昏/傍晚
```
golden hour, warm orange diffused light, long soft shadows
```

---

## 鏡頭提示詞對照表

| 分鏡標記 | Gemini 寫法 |
|---------|-----------|
| 特寫 | `close-up portrait` |
| 極特寫 | `extreme close-up` |
| 側臉特寫 | `close-up side profile` |
| 中景 | `medium shot` |
| 廣角 | `wide angle shot` |
| 俯拍廣角 | `overhead wide angle shot` |
| 仰拍 | `low angle shot looking up` |
| 主觀視角 | `POV shot from the perspective of [誰]` |
| 跟拍 | `tracking shot following [誰]` |
| 逆光 | `backlit, soft rim light silhouette` |
| 疊影 | `double exposure, semi-transparent overlay` |

---

## 情緒描述字串庫

### 悲傷/遺憾
- `bittersweet half-smile`
- `wistful and quietly longing expression`
- `quiet resignation`
- `the weight of unspoken words`
- `a face that holds both sadness and acceptance`

### 緊張/期待
- `quiet anxiety and silent prayer`
- `barely suppressed excitement`
- `a slight tremor of nervousness`

### 溫暖/幸福
- `natural warm spontaneous smile with dimples`
- `a warm genuine smile that reaches the eyes`
- `lively sparkling eyes full of energy`

### 釋懷/成長
- `quiet acceptance and gentle resilience`
- `the kind of smile that took a lot of courage to find`
- `moving forward with quiet resolve`

### 暗戀/羞澀
- `a helplessly suppressed smile`
- `subtle involuntary smile he's trying to suppress`
- `flustered shy look`

---

## 常用道具描述

| 道具 | 英文描述 |
|------|---------|
| 咖啡杯（有蒸氣）| `white ceramic coffee mug with visible steam rising` |
| 咖啡杯（已冷）| `untouched coffee mug, no steam, cold` |
| 吉他 | `acoustic guitar leaning against wall` |
| 便條紙（劃掉）| `yellow sticky note with words crossed out in ink` |
| 鍵盤 | `mechanical keyboard, hands resting motionless` |
| 時鐘（9:30）| `small analog desk clock showing 9:30` |
| 筆電螢幕（空白）| `laptop screen showing blank white document with blinking cursor` |

---

## 生成技巧

### 提高一致性
1. 在 Session 開頭先生成角色參考圖
2. 同一 Session 內繼續生成分鏡圖
3. 下次用最好的角色圖作為參考圖上傳

### 提高品質
- 提示詞長度 80-150 字最佳
- 先說場景，再說人物，最後說情緒
- 用具體名詞而非抽象描述

### 常見問題排除
| 問題 | 解法 |
|------|------|
| 手指畸形 | 加 `hands not in frame` 或 `focus on face only` |
| 文字亂碼 | 避免要求圖中有可讀文字 |
| 角色性別錯 | 提示詞最前面明確寫 `young East Asian male/female` |
| 背景太雜 | 加 `clean blurred background` / `shallow depth of field` |
