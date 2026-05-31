# 🎵 AI Music MV Workflow

> 用 AI 工具製作完整音樂 MV 的標準化工作流程
> 從歌詞整理 → 分鏡規劃 → 圖片生成 → 影片剪輯 → 社群發布，一條龍完成。

---

## 🗂️ 專案結構

```
ai-music-work/
├── README.md                   # 本文件，工作流總覽
├── workflows/                  # 六個工作流程文件
│   ├── 00-overview.md          # 完整流程圖
│   ├── 01-lyrics-format.md     # Skill 1：歌詞整理
│   ├── 02-mv-storyboard.md     # Skill 2：MV 分鏡規劃
│   ├── 03-character-setup.md   # Skill 3：角色設定
│   ├── 04-shot-prompts.md      # Skill 4：分鏡提示詞生成
│   ├── 05-shot-review.md       # Skill 5：分鏡圖片審核
│   └── 06-music-publish.md     # Skill 6：發布內容生成
├── templates/                  # 可重複使用的模板
│   ├── lyrics-template.txt     # 歌詞 YT 格式模板
│   ├── storyboard-template.md  # MV 分鏡模板
│   ├── character-template.md   # 角色設定模板
│   └── prompts-template.md     # 分鏡提示詞模板
├── prompts/                    # 通用提示詞庫
│   ├── gemini-style-guide.md   # Gemini 全域風格字串
│   └── character-reference.md  # 角色描述參考格式
└── examples/                   # 實際案例（每首歌一個資料夾）
    └── 倒數的加班/
        ├── YT.txt
        ├── MV分鏡.md
        └── MV分鏡_提示詞.md
```

---

## 🔄 工作流程總覽

```
INPUT：歌曲原始歌詞 + MP3
        ↓
  [Skill 1] 歌詞整理      → YT格式歌詞.txt
        ↓
  [Skill 2] MV分鏡規劃    → MV分鏡.md
        ↓
  [Skill 3] 角色設定      → 角色基準描述 + 參考圖提示詞
        ↓
  [Skill 4] 分鏡提示詞    → MV分鏡_提示詞.md
        ↓
  ── 手動：Gemini 圖片生成 ──
        ↓
  [Skill 5] 分鏡審核      → 審核報告 + 修正提示詞
        ↓
  ── 手動：Canva 剪輯 ──
        ↓
  [Skill 6] 發布內容生成  → YT說明 / 標記 / 封面提示詞 / IG貼文

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

## 📁 案例紀錄

| 歌曲 | 狀態 | 備註 |
|------|------|------|
| [倒數的加班](./examples/倒數的加班/) | ✅ 完成 | 首次建立流程的參考案例 |

---

## 📌 版本紀錄

| 版本 | 日期 | 更新內容 |
|------|------|---------|
| v1.0 | 2026-05-31 | 初版建立，基於「倒數的加班」製作流程整理 |

---

## 💡 優化方向（待研究）

- [ ] Skill 5 審核流程自動化（批次讀取圖片比對分鏡）
- [ ] 角色一致性跨 Session 維持方式研究
- [ ] Canva 剪輯節奏模板建立
- [ ] 多語言版本發布文案（英文市場）
- [ ] 封面 A/B 測試流程
