# 大地測量學 (Geodesy) LLM Wiki 與圖解教學簡報系統

本專案建立了一個基於大語言模型（LLM）的**大地測量學結構化知識庫（Wiki）**與專為零基礎學習者設計的**互動式圖解教學簡報（Slides Deck）**。

整個知識體系與簡報內容皆嚴格遵循「**100% 來源無幻覺鐵則**」，所有幾何定義、物理重力公式與坐標參數均嚴密溯源自原始大地測量學專業文獻。

---

## 專案目錄結構

```text
.
├── README.md              # 專案總說明與操作手冊（本文件）
├── agent.md               # 專案唯一核心工作手冊與五節點規範準則
├── check_log.md           # 嚴格助教視角審查歷程與修正紀錄
├── slides_outline.md      # 教學投影片大綱、白話比喻與 SVG 設計底稿
├── raw/                   # 原始文獻資料庫（唯讀不可變層）
│   ├── 01.pdf.pdf         # 坐標系統、基準與轉換計算
│   ├── 02.pdf.pdf         # 地球自轉、歲差章動、極移與時間系統
│   ├── 03.md.md           # 重力、坐標系、大地基準與 GPS 定位
│   ├── 04.md.md           # 地圖投影、高斯克呂格、UTM 與臺灣 TM2/TM3
│   └── 05.md.md           # 地球重力場、球諧函數展開、克萊羅定理、司托克定理
├── wiki/                  # 繁體中文結構化知識庫
│   ├── index.md           # 總目錄、條目摘要、公式索引與雙向概念矩陣
│   ├── topic_01_地球形狀與幾何物理特徵.md
│   ├── topic_02_地球重力場與重力位理論.md
│   ├── topic_03_正常重力位與水準橢球.md
│   ├── topic_04_地球運動與空間坐標系.md
│   ├── topic_05_大地基準與橢球體.md
│   ├── topic_06_大地測量時間系統.md
│   ├── topic_07_國際參考框架與現代動態基準.md
│   ├── topic_08_臺灣大地基準與全球系統比較.md
│   ├── topic_09_基準轉換與坐標變換數學模型.md
│   ├── topic_10_地圖投影理論與高斯克呂格投影.md
│   └── topic_11_UTM投影與臺灣TM2分帶系統.md
└── slides/                # 最終呈現層
    └── index.html         # 零外部依賴、純離線可用的互動教學簡報（29 頁）
```

---

## 互動簡報功能與瀏覽方式

最終產出的 [`slides/index.html`](file:///c:/Users/user/Desktop/LLM%20wiki/slides/index.html) 為**單一獨立網頁**，將所有樣式（CSS）、互動邏輯（JavaScript）以及原生幾何示意圖（SVG）完全內嵌，**無任何外部 CDN 或網路連線依賴**，可直接離線雙擊開啟。

### 1. 本機預覽方式

- **方法一（最快）**：直接以檔案總管開啟 `slides/index.html`（或以滑鼠左鍵雙擊檔案），即可在預設瀏覽器（Edge / Chrome / Firefox / Safari）中離線預覽。
- **方法二（終端指令）**：
  - Windows PowerShell：
    ```powershell
    Start-Process "slides/index.html"
    ```
- **方法三（本機 HTTP 伺服器，選用）**：
  ```bash
  npx serve slides
  # 或使用 Python 伺服器
  python -m http.server 8000
  ```

### 2. 簡報操作快捷鍵與特色

| 按鍵 / 操作 | 功能說明 |
| :--- | :--- |
| `→` 或 `Space` 或 `PageDown` | 切換至下一頁投影片 |
| `←` 或 `PageUp` | 回到上一頁投影片 |
| `Home` / `End` | 直接跳至首頁 / 尾頁 |
| `F` 鍵 | 切換全螢幕模式（沉浸式演講模式） |
| 下拉選單 | 點擊底部導覽列選單，可即時跳轉至 29 個章節中的任一頁 |
| 手機觸控 | 支援行動裝置左右滑動（Swipe）手勢翻頁 |
| 來源溯源標籤 | 每頁底部均附帶對應的 `wiki/topic_XX` 知識庫溯源標籤 |

---

## 未來新增文獻與自動更新流程（SOP）

本專案遵循 `agent.md` 所定義的五節點工作流（Node 1 ~ Node 5）。當未來有新的大地測量文獻、講義或技術報告需要納入時，請遵循以下標準作業流程：

### 步驟 1：放置新資料至 `raw/`
- 將新文獻檔案（支援 PDF、Markdown、純文字 TXT）放入 `raw/` 目錄。
- **重要守則**：`raw/` 為唯讀不可變層，切勿刪除或修改既有的原始檔案。

### 步驟 2：向 AI Agent 發出更新指令
在對話框中向 AI 發送如下指令：
> 「我已在 `raw/` 中新增了文獻檔案，請依據 `agent.md` 的規範，執行完整的五節點工作流程（Node 1 至 Node 5），將新文獻整合進知識庫與簡報中。」

### 步驟 3：AI 自動執行節點工作流
1. **Node 1（Ingest）**：AI 盤點新舊檔案並解析知識核心。
2. **Node 2（Build Wiki）**：
   - 提取新概念，增補至既有 `wiki/topic_XX_...md` 或建立新的主題條目。
   - 同步更新 [`wiki/index.md`](file:///c:/Users/user/Desktop/LLM%20wiki/wiki/index.md) 的條目摘要、跨主題雙向關聯矩陣與數學物理公式索引。
   - 嚴格維持 100% 來源無幻覺與註腳引注。
3. **Node 3 & Node 4（Outline & Verification Loop）**：
   - 評估是否需要新增教學投影片頁面或修訂現有投影片大綱。
   - 設計新概念的內嵌原生 SVG 幾何圖解。
   - 啟動嚴格助教視角審查（至少 2 輪），嚴查溯源度、SVG 圖解正確性與新手友善度，並將審查過程完整記錄於 [`check_log.md`](file:///c:/Users/user/Desktop/LLM%20wiki/check_log.md)。
4. **Node 5（Render HTML）**：
   - 將修訂後的投影片重新編譯為獨立單檔 [`slides/index.html`](file:///c:/Users/user/Desktop/LLM%20wiki/slides/index.html)，維持完全無外部依賴的單檔離線架構。

---

## 核心設計理念與品質保證

1. **零幻覺（100% Source-Backed）**：所有名詞、數值（如 TWD67/97 偏差參數、GRS80 扁率、高斯投影比例尺等）均有 `raw/` 出處可查，杜絕 AI 臆測。
2. **零外部依賴（Self-Contained Offline First）**：所有 SVG 圖形、字型階層與 JavaScript/CSS 均完整內置，離線環境、內網投影或部署於 GitHub Pages 均可 100% 正常顯示。
3. **初學者友好（Beginner-Friendly Pedagogical Design）**：將深奧的微分幾何與位理論，轉化為「地表幾何橘子、引力與離心力的重力拔河、七參數的樂高積木轉換、圓柱切開的地圖投影」等直觀比喻，結合高對比幾何向量圖解，讓零基礎讀者也能迅速掌握大地測量學精髓。
