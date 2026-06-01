# Skill 2 — Mureka 提示詞生成（mureka-prompt）

## 目標
將確認版歌詞 + Intake 表單的風格設定，轉換為 mureka.ai 最佳化的輸入格式。

## 輸入
- 確認版歌詞（人工修改完成）
- Intake 表單（音樂風格欄位）

## 輸出
- Mureka 風格標籤字串
- 格式化歌詞（符合 Mureka 輸入規範）
- 生成建議（幾個版本、哪些參數可以嘗試調整）

---

## Mureka.ai 輸入格式說明

### 風格標籤（Style Tags）
Mureka 透過風格標籤決定曲風、樂器、情緒，格式為逗號分隔的英文詞彙：

```
[流派], [子流派], [情緒], [樂器1], [樂器2], [人聲風格], [速度], [語言]
```

### 風格標籤對照表

#### 流派
| 中文 | Mureka 標籤 |
|------|-----------|
| 抒情流行 | `mandopop`, `ballad` |
| 台灣 Indie | `taiwanese indie`, `indie pop` |
| Indie Folk | `indie folk`, `acoustic` |
| R&B | `r&b`, `soul` |
| Lo-fi | `lo-fi`, `chill` |
| 電子流行 | `electropop`, `synth pop` |
| 民謠 | `folk`, `acoustic folk` |

#### 情緒
| 中文 | Mureka 標籤 |
|------|-----------|
| 溫柔遺憾 | `melancholic`, `bittersweet` |
| 療癒釋懷 | `healing`, `hopeful` |
| 暗戀心動 | `romantic`, `longing` |
| 孤獨沉靜 | `solitary`, `introspective` |
| 青春輕快 | `nostalgic`, `wistful` |

#### 樂器
| 中文 | Mureka 標籤 |
|------|-----------|
| 木吉他 | `acoustic guitar` |
| 電吉他 | `electric guitar` |
| 鋼琴 | `piano` |
| 弦樂 | `strings`, `violin` |
| 口琴 | `harmonica` |
| 合成器 | `synthesizer`, `synth pad` |
| 爵士鼓 | `drums` |
| 輕鼓刷 | `brush drums` |

#### 人聲風格
| 中文 | Mureka 標籤 |
|------|-----------|
| 溫柔男聲 | `male vocal`, `soft male vocal` |
| 清亮女聲 | `female vocal`, `clear female vocal` |
| 沙啞低沉 | `husky vocal`, `deep vocal` |
| 空靈飄逸 | `ethereal vocal` |

#### 速度
| 中文 | Mureka 標籤 |
|------|-----------|
| 慢板 | `slow`, `60-75 BPM` |
| 中慢板 | `mid-tempo`, `75-90 BPM` |
| 中板 | `moderate`, `90-110 BPM` |

---

## 歌詞格式化規則（Mureka 輸入）

Mureka 識別以下段落標籤（**英文**）：

```
[verse]
[pre-chorus]
[chorus]
[bridge]
[outro]
```

### 格式範例
```
[verse]
又是晚上九點半
辦公室瞬間攀上了你的陪伴
你笑著說今天也要把工作做完
我坐得冷靜
心裡卻覺得很暖

[chorus]
我好像比想像中喜歡你
卻要不到答案
翻個話題後
才知道一切太晚
```

---

## 輸出範例

### 風格標籤（「倒數的加班」案例）
```
mandopop, indie pop, melancholic, bittersweet, acoustic guitar, piano, 
soft male vocal, slow, 70-80 BPM, taiwanese, chinese lyrics
```

### 生成建議
- 建議生成 **4-6 個版本**
- 版本 A：以上標籤原版
- 版本 B：把 `piano` 換成 `strings`（弦樂版，更感人）
- 版本 C：加入 `electric guitar`（稍微有力版）
- 版本 D：加入 `lo-fi`（低調復古版）

---

## Claude 操作提示

```
根據以下資訊，幫我生成 Mureka.ai 的輸入格式：

Intake 表單音樂風格欄位：[貼上]
確認版歌詞：[貼上]

請輸出：
1. 主要風格標籤字串（英文逗號分隔）
2. 2-3 個變體風格標籤（用來生成不同版本）
3. 歌詞轉換為 Mureka 格式（英文段落標籤）
4. 生成建議（幾個版本、各版本差異）
```

---

## 選歌建議

Mureka 生成後，人工選歌時注意：

| 評估面向 | 說明 |
|---------|------|
| **旋律記憶點** | 副歌能不能讓人哼出來 |
| **情緒匹配** | 曲調與歌詞情感一致嗎 |
| **人聲質感** | 聲線是否符合角色設定 |
| **編曲層次** | 主歌簡單、副歌豐富的漸進感 |
| **整體時長** | 是否符合預期（MV 分鏡會依此調整）|

---

## 注意事項
- Mureka 中文歌詞建議加上 `chinese lyrics` 標籤
- 同一組歌詞可以嘗試 3-4 種不同風格標籤
- 選定歌曲後記錄使用的風格標籤，存入案例 README 方便日後參考
- 若對結果都不滿意，可回 Skill 1 微調歌詞再重新生成
