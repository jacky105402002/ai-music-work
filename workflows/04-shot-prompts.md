# Skill 4 — 分鏡提示詞生成（shot-prompts）

## 目標
為每個分鏡鏡號生成對應的 Gemini 圖片生成提示詞。

## 輸入
- `MV分鏡.md`：完整分鏡腳本
- 角色基準描述（來自 Skill 3 輸出）

## 輸出
- `MV分鏡_提示詞.md`：每鏡一個 Gemini 提示詞

---

## 提示詞結構

每個鏡號的提示詞由四層組成：

```
[場景描述] + [角色描述] + [情緒/光線] + [全域風格字串]
```

### 全域風格字串（每張圖結尾都加）
```
cinematic still, film grain, soft depth of field, Taiwan indie MV aesthetic, muted warm tones, emotional and nostalgic mood, 16:9
```

### 室內色調補充
```
warm amber office lighting, 2700K tungsten glow, late night office
```

### 室外色調補充
```
cool blue night cityscape, city lights bokeh
```

---

## 提示詞撰寫原則

### 場景描述
- 說明構圖：`wide shot` / `close-up` / `medium shot` / `overhead shot`
- 說明主體位置：`standing in doorway` / `sitting at desk`
- 說明道具細節：`white ceramic mug with steam rising`
- 說明光線來源：`backlit by hallway light` / `warm desk lamp casting shadows`

### 情緒描述
- 直接描述表情：`bittersweet half-smile` / `quiet longing expression`
- 加上象徵性敘述引導 AI 理解情緒：
  - `the kind of smile that costs everything`
  - `the weight of unspoken words`
  - `symbolizing two people staying late`

### 鏡頭類型對應提示詞
| 分鏡鏡頭 | Gemini 提示詞寫法 |
|---------|----------------|
| 特寫 | `extreme close-up` / `close-up portrait` |
| 側臉特寫 | `close-up side profile` |
| 中景 | `medium shot` |
| 廣角 | `wide angle shot` |
| 俯拍 | `overhead shot` / `top-down view` |
| 主觀視角 | `POV shot from the perspective of...` |
| 逆光 | `backlit` / `rim light silhouette` |
| 跟拍背影 | `wide shot of [person] walking away` |

---

## 特殊鏡頭提示詞技巧

### 回憶閃回（拼貼）
```
Collage of four warm overexposed nostalgic memory vignettes in a single frame,
top-left shows..., top-right shows..., bottom-left shows..., bottom-right shows...,
all in warm faded overexposed film-style tones
```

### 倒影/疊影
```
the glass reflecting the ghostly transparent face of [角色描述] overlaid on top of [背景],
semi-transparent like a double exposure
```

### 靜物空鏡
```
macro close-up still life of [物件], [光線], [象徵意義], no people in frame
```

### 字幕卡（尾聲）
```
minimalist title card, pure black background, elegant thin white Chinese characters,
soft white glow around text, film grain texture, fade in from darkness
```

---

## Claude 操作提示

```
請根據以下分鏡腳本，為每個鏡號生成 Gemini 圖片提示詞：

角色快速字串：
- 男主角：[複製 Skill 3 輸出的場景快速字串]
- 女主角：[複製 Skill 3 輸出的場景快速字串]

全域風格字串：
cinematic still, film grain, soft depth of field, Taiwan indie MV aesthetic, muted warm tones, emotional and nostalgic mood, 16:9

分鏡腳本：[貼上 MV分鏡.md 內容]

要求：
- 每鏡一個完整 Gemini 提示詞（英文）
- 涉及角色的鏡號自動嵌入角色快速字串
- 室內場景加暖黃色調描述，室外加冷藍色調
- 輸出 MV分鏡_提示詞.md 儲存到 [路徑]
```

---

## 注意事項
- 每個提示詞長度建議 80-150 字
- 避免過度複雜的構圖描述（Gemini 容易混亂）
- 角色描述字串一定要出現在提示詞前半段
- 同一張圖不要描述超過兩個主要元素
