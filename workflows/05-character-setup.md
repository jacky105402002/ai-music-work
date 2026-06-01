# Skill 3 — 角色設定（character-setup）

## 目標
建立角色一致性基準描述，供所有分鏡提示詞使用，確保 Gemini 生成圖片時角色外型不跑版。

## 輸入
- 角色文字描述（個性、職業、外型）
- 角色參考圖片（可選，若有則優先依照圖片描述）

## 輸出
- 角色基準描述區塊（嵌入 MV分鏡_提示詞.md 最上方）
  - 角色參考圖提示詞
  - 場景快速字串（每鏡複製貼上用）

---

## 角色描述拆解框架

### 必填欄位
| 欄位 | 範例 |
|------|------|
| 族裔 | East Asian |
| 年齡 | approximately 26-28 years old |
| 體型 | slim build / petite cute figure |
| 髮型 | medium-length slightly tousled dark hair |
| 眼鏡 | square metal-framed glasses（若有） |
| 服裝 | blue-grey plaid flannel shirt, dark jeans |
| 鞋子 | grey Vans canvas shoes |
| 表情氣質 | quiet introverted expression, observant eyes |
| 配件 | simple wristwatch / small stud earrings |

### 可選欄位
| 欄位 | 說明 |
|------|------|
| 臉部特徵 | slightly unshaven / dimples when smiling |
| 姿態特徵 | slightly slouched posture |
| 能量描述 | cheerful and outgoing energy |

---

## 使用參考圖片時的分析流程

1. **請 Claude 讀取圖片**，輸出外型觀察清單
2. 核對清單是否符合角色設定
3. 轉換為 Gemini 可用的英文描述
4. 生成角色參考圖提示詞與場景快速字串

### 圖片分析提示詞
```
請分析這張圖片中的人物外型，輸出以下欄位：
- 髮型與髮色
- 眼鏡樣式（若有）
- 服裝（上衣/下著/外套/鞋子）
- 配件
- 整體氣質/表情
然後幫我轉換成 Gemini 圖片生成用的英文描述字串。
```

---

## Gemini 角色一致性技巧

### Session 內一致性（推薦）
1. 在新 Session 開頭，先輸入「角色參考圖提示詞」生成一張角色圖
2. 之後在**同一個 Session** 內繼續生成分鏡圖
3. Gemini 會記住該 Session 的視覺風格

### 跨 Session 一致性
- 把生成最好的角色圖下載，下次作為 **參考圖片** 上傳給 Gemini
- 加上 `maintain character consistency with the reference image` 到提示詞

### ⚠️ 常見問題
| 問題 | 解決方式 |
|------|---------|
| 眼鏡樣式跑掉 | 在提示詞明確寫 `square metal-framed glasses`（不要只寫 glasses） |
| 髮型改變 | 加上 `same hairstyle as reference` |
| 服裝顏色偏差 | 加上具體色號描述，如 `navy blue` 而不是 `dark blue` |
| 男女角色互換 | 每個提示詞都明確寫性別與職業 |

---

## Claude 操作提示

```
請根據以下角色設定，生成角色基準描述區塊：

角色 A（暗戀方）：
- 性別：男
- 職業：工程師
- 個性：[描述]
- 外型：[描述或上傳參考圖]

角色 B（被暗戀方）：
- 性別：女
- 職業：行銷
- 個性：[描述]
- 外型：[描述或上傳參考圖]

輸出格式：
1. 角色參考圖提示詞（完整 Gemini prompt）
2. 場景快速字串（簡短版，供每鏡複製）
```
