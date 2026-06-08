# 🎵 AI Music MV Workflow

> 用 AI 工具製作完整音樂 MV 的標準化工作流程
> 從歌詞整理 → 分鏡規劃 → 圖片生成 → 影片剪輯 → 社群發布，一條龍完成。

---

## 🗂️ 專案結構

```
ai-music-work/
├── README.md                   # 本文件，工作流總覽
├── workflows/                  # 工作流程文件（Skill 0-8）
│   ├── 00-overview.md          # 完整流程圖 + 時間估算
│   ├── 00-song-brief.md        # Skill 0：歌曲企劃
│   ├── 01-lyrics-draft.md      # Skill 1：歌詞草稿
│   ├── 02-mureka-cycle.md      # Skill 2：Mureka 製作循環
│   ├── 03-lyrics-format.md     # Skill 3：歌詞整理
│   ├── 04-mv-storyboard.md     # Skill 4：MV 分鏡規劃
│   ├── 05-character-setup.md   # Skill 5：角色設定
│   ├── 06-shot-prompts.md      # Skill 6：分鏡提示詞生成
│   ├── 07-shot-review.md       # Skill 7：分鏡圖片審核
│   └── 08-music-publish.md     # Skill 8：發布內容生成
├── templates/                  # 可重複使用的模板
│   ├── song-intake-form.md     # 歌曲企劃表單
│   └── mureka-feedback-form.md # Mureka 試聽回饋表
├── prompts/                    # 通用提示詞庫
│   ├── gemini-style-guide.md   # Gemini 全域風格字串
│   └── character-reference.md  # 角色描述參考格式
└── examples/                   # 實際案例（每首歌一個資料夾）
    └── 倒數的加班/
        ├── MV分鏡.md
        └── MV分鏡_提示詞.md
```

---

## 🔄 工作流程總覽

```
INPUT：一個歌曲概念 / 主題
        ↓
  [Skill 0] 歌曲企劃      → Intake 表單
        ↓
  [Skill 1] 歌詞草稿      → 歌詞草稿.txt
        ↓
  [Skill 2] Mureka循環    → 選定 MP3 + 最終歌詞（Mureka提示詞.txt）
        ↓
  [Skill 3] 歌詞整理      → YT.txt（含時間戳）
        ↓
  [Skill 4] MV分鏡規劃    → MV分鏡.md（含鏡00前奏 + 入點/出點時間表）
        ↓
  [Skill 5] 角色設定      → 角色描述字串（確認畫風後定稿）
        ↓
  [Skill 6] 分鏡提示詞    → MV分鏡_提示詞.md（Session A/B 分組）
        ↓
  ── 手動：Gemini 圖片生成（先角色參考圖，再逐鏡）──
        ↓
  [Skill 7] 分鏡圖片審核  → 審核報告 + 修正提示詞
        ↓
  ── 手動：Canva 剪輯（片尾字卡直接在 Canva 製作）──
        ↓
  [Skill 8] 發布內容生成  → YT說明 / 標記 / IG文案 / Line分享文字

OUTPUT：完整 MV + 社群發布素材
```

---

## 🛠️ 使用工具

| 工具 | 用途 |
|------|------|
| **Claude** | 歌詞整理、分鏡規劃、提示詞生成、審核、發布文案 |
| **Gemini** | 分鏡圖片生成（Image Generation） |
| **Canva** | 影片剪輯、字幕、封面製作 |
| **YouTube** | 影片發布平台 |
| **Instagram** | 社群短片發布 |

---

## 🛠️ 使用工具

| 工具 | 用途 |
|------|------|
| **Claude** | 全流程文字規劃（歌詞/分鏡/提示詞/文案） |
| **Gemini** | 分鏡圖片生成（Image Generation） |
| **Mureka.ai** | AI 音樂生成 |
| **Canva** | 影片剪輯、字幕、封面製作、片尾字卡 |
| **YouTube** | 影片發布 |
| **Instagram / Line** | 社群宣傳 |

---

## 📁 案例紀錄

| 歌曲 | 狀態 | 備註 |
|------|------|------|
| [倒數的加班](./examples/倒數的加班/) | ✅ 完成 | 首次建立流程的參考案例 |
| 不演了 | ✅ 完成 | 第二首，流程最完整，已驗證所有 Skill 0-8 |

---

## 📌 版本紀錄

| 版本 | 日期 | 更新內容 |
|------|------|---------|
| v1.0 | 2026-05-31 | 初版建立，基於「倒數的加班」製作流程整理 |
| v1.1 | 2026-06-08 | 基於「不演了」製作經驗，補充 Skill 0-2、Gemini Session策略、鏡00規則、Line分享文 |

---

## 💡 優化方向（待研究）

- [ ] Canva 剪輯節奏模板建立
- [ ] 多語言版本發布文案（英文市場）
- [ ] 封面 A/B 測試追蹤
