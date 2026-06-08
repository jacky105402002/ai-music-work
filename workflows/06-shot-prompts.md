# Skill 6 — 分鏡提示詞生成（shot-prompts）

## 目標
為每個分鏡鏡號生成對應的 Gemini 圖片生成提示詞。

## 輸入
- `MV分鏡.md`：完整分鏡腳本（含入點/出點時間表）
- 角色基準描述（來自 Skill 5 輸出）

## 輸出
- `MV分鏡_提示詞.md`：每鏡一個 Gemini 提示詞

---

## 📂 MV分鏡_提示詞.md 標準結構

```markdown
# 🎬 [歌曲名稱] — MV 分鏡提示詞（N 鏡）

## ⏱️ 時間對照表（Canva 剪輯用）
| 鏡號 | 入點 | 出點 | 時長 | 段落 | 場景類型（色調 emoji）|
...每鏡一列...

> 色調圖例：🟡閃回 | 🔵現在夜晚 | 🌅天台日出 | 🌙天台夜晚

## 📌 全域畫風字串
## 👤 角色快速字串
## 🎨 色調字串

## 🗂️ SESSION A — 現在場景
...（含 鏡00 前奏）...

## 🗂️ SESSION B — 閃回場景
...
```

---

## 🗂️ Session 分組策略（多角色必用）

**為什麼分 Session？** Gemini 在同 Session 內記住視覺風格，分組可大幅降低角色跑版。

| Session | 適用場景 | Gemini 操作 |
|---------|---------|------------|
| **Session A** | 現在場景、單一主角（含 鏡00） | 先生成角色參考圖 → 同 Session 繼續 |
| **Session B** | 閃回場景、雙角色同框 | 另開新 Session，先生成雙角色參考圖 |

**Gemini Session 開頭固定語：**
```
You are an MV storyboard image generator.
Maintain consistent character design throughout this session.
[貼上角色快速字串]
First, generate a character reference image.
```

---

## 提示詞結構

每個鏡號的提示詞由四層組成：

```
[場景描述] + [角色描述] + [情緒/光線] + [全域風格字串]
```

### 全域風格字串（依畫風選擇）

**美式動畫插畫風（不演了採用）**
```
semi-realistic American animation illustration style, clean line art with soft cel-shading, modern graphic novel aesthetic, 16:9
```

**寫實電影風（通用）**
```
cinematic still, film grain, soft depth of field, Taiwan indie MV aesthetic, muted warm tones, emotional and nostalgic mood, 16:9
```

### 色調字串（依場景選擇）
```
閃回：faded warm amber tones, slightly overexposed, nostalgic vintage film grain
現在・夜晚：high contrast cool tones, urban neon lighting, cinematic
天台・日出：open sky backdrop, warm golden hour dawn light, liberating and airy
天台・夜晚：dark quiet rooftop at night, low saturation, cool blue-black tones
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
- **鏡00 提示詞結尾可加封面選項備注**：若要直接用作 YT 封面，在 prompt 結尾加 `bold white Chinese text "[歌名]" in lower third, thumbnail composition`
- **片尾字卡**（最後一鏡）不需 Gemini 生成，直接在 Canva 製作
- 人物性別一定要在每個 prompt 明確寫出（避免 Gemini 亂換性別）
