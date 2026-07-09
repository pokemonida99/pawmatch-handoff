# 合拍 PawMatch 專案交接文件（HANDOFF）

> 用途：在**另一台電腦**接續本專案。這份文件說明目前進度、檔案位置、如何執行、以及待辦事項。
> 打包時間：2026-07-09　·　工作分支：`claude/cat-adoption-prompt-suite-zzaho0`

---

## 0. 一分鐘看懂這個專案

「合拍 PawMatch」是一個**貓咪認養平台的單頁式網站 MVP**，依據對台灣貓咪中途之家的深度研究（Prompt 組 + 4 場訪談）設計。核心設計主張：**凡「轉換率」與「被審查感」衝突，一律先消除被審查感**——用生活樣態配對取代審核問卷、用個性敘事取代條件比對、用去人化的曬貓回報取代監控式追蹤。

已完成兩件事：
1. **網站本體**（依 Prompt A 主站 + B1–B5 模組深化 + Prompt C 易用性驗收生成）。
2. **易用性測試報告**（整理 4 場中途訪談 → 領養者行為與心理分析 → 三位 persona 模擬走查 → 功能對領養率的貢獻度評分）。

---

## 1. 目前進度（已完成 ✅）

| 項目 | 狀態 | 檔案 |
|---|---|---|
| Prompt 組原始文件保存 | ✅ | `cat-adoption-site/PROMPTS.md` |
| 網站主站（可讀原始碼版，CDN） | ✅ | `cat-adoption-site/index.html` |
| 網站離線版（零相依、雙擊即開，已 Chromium 實測） | ✅ | `cat-adoption-site/index.offline.html` |
| 設計計畫 + 驗收紀錄 | ✅ | `cat-adoption-site/README.md` |
| 4 場訪談逐字稿（已從 .docx 抽出文字） | ✅ | `research/interview_*.txt` |
| 易用性測試報告（Markdown） | ✅ | `cat-adoption-site/USABILITY-REPORT.md` |
| 易用性測試報告（互動 HTML，可雙擊預覽） | ✅ | `reports/usability-report.html` |

**網站已實作的 6 大區塊 + 模組深化：**
Hero（利己主張＋雙 CTA）／生活樣態配對測驗（一屏一題·可跳過·貓掌進度·加權向量配對·引用答案的合拍理由）／個性敘事貓咪檔案（第一人稱故事·健康護照時間軸·以貓為主詞的需求卡）／認養旅程四階段／成長相簿＋回家之後（曬貓回報·抽獎·隱私預設私密）／新手支援與透明區（匿名發問·無責退回·透明帳本）／中途後台（兩檔位提醒·系統轉介）。

**線上版（GitHub Pages，公開，2026-07-09 上線）：**
- 專案導覽首頁：https://pokemonida99.github.io/pawmatch-handoff/
- 網站 Demo：https://pokemonida99.github.io/pawmatch-handoff/cat-adoption-site/index.offline.html
- 易用性報告：https://pokemonida99.github.io/pawmatch-handoff/reports/usability-report.html

**Artifact 預覽（私人連結，內容同上）：**
- 網站：https://claude.ai/code/artifact/4d4aba28-c2ac-4b66-a407-34d65ef60111
- 易用性報告：https://claude.ai/code/artifact/0f09548f-0745-4a43-a100-42f37343f138

> 舊連結（d28a00e1…／3e709a2f…）是前一台電腦的工作階段發佈的，無法從新環境更新，內容停在 P0 實作前，可忽略。

> 註：Artifact 連結預設為私人，需在頁面分享選單開啟才可分享。這些連結是雲端渲染，與本 ZIP 內的檔案內容一致。

---

## 2. 檔案地圖（ZIP 內容）

```
pawmatch-handoff/
├── HANDOFF.md                    ← 你正在看的這份（進度＋代辦）
├── cat-adoption-site/            ← 網站本體（= git repo 內同名資料夾）
│   ├── index.html                ← 【要改程式改這份】可讀 React+Tailwind CDN 版
│   ├── index.offline.html        ← 【要展示用這份】零網路、雙擊即開
│   ├── PROMPTS.md                ← 原始 Prompt A/B1–B5/C 全文
│   ├── README.md                 ← 設計計畫、色票、驗收紀錄
│   └── USABILITY-REPORT.md       ← 易用性測試報告（文字版）
├── reports/
│   └── usability-report.html     ← 易用性報告（互動版，雙擊即開）
└── research/
    └── interview_*.txt           ← 4 場中途訪談逐字稿（分析原料）
```

---

## 3. 在另一台電腦怎麼接續

### 方式 A：從 GitHub 接續（推薦，保留 git 歷史）
本專案已是獨立 repo（2026-07-09 建立，私人）：
```bash
git clone https://github.com/pokemonida99/pawmatch-handoff.git
cd pawmatch-handoff/cat-adoption-site
```
> 舊的 CogVideo repo 分支 `claude/cat-adoption-prompt-suite-zzaho0` 是第一階段的工作紀錄，內容已全部帶到本 repo，可忽略。

### 方式 B：直接用這個 ZIP（無 git）
解壓縮後，`cat-adoption-site/` 就是完整網站，不需安裝任何東西。

### 執行 / 預覽網站
- **最簡單**：直接用瀏覽器雙擊 `index.offline.html`（零相依）。
- **要改程式**：改 `index.html`（React 寫在 `<script type="text/babel">` 內），存檔後瀏覽器重整即可（需網路載入 React/Tailwind CDN）。
- 或起本機伺服器：`python3 -m http.server 8000` 後開 `http://localhost:8000/index.html`。

### 重新產生離線版（若你改了 index.html）
離線版是把 `index.html` 的 JSX 用 esbuild 預編譯、Tailwind 預產 CSS、React 內嵌而成。重建步驟：
```bash
# 需 node。把 index.html 內 <script type=text/babel> 的內容存成 app.jsx
npm i react@18 react-dom@18 tailwindcss@3 esbuild
npx esbuild app.jsx --loader:.jsx=jsx --minify --outfile=app.js
npx tailwindcss -i input.css -o tw.css --minify   # content 指向 app.jsx
# 再把 react/react-dom UMD + tw.css + app.js 串成單一 HTML（參考現有 index.offline.html 結構）
```
> 大多數情況只維護 `index.html` 即可；離線版是給「無網路展示 / 交付」用的。

---

## 4. 待辦事項（TODO）

### 🔴 P0 — 高報酬、低成本 ✅ 全部完成（2026-07-09）
來自易用性報告：三個流失卡點全部發生在「送出意向」那一刻，用三句文案就能接住。

- [x] **草稿頁除罪化**：`ChatModal` 草稿上方加一句「中途看的是你願不願意學，不是你懂多少。」
      → 解「新手怕被打槍」（persona P1）。
- [x] **送出隱私說明**：`ChatModal` 草稿旁標注「這段摘要只寄給這位中途，不會公開、不進相簿。」
      → 解「隱私敏感者怕留底」（persona P3）。
- [x] **前移『試相處』**：`Quiz` 結果頁每張結果卡 CTA 下方加「先見面、可試相處，不用一次決定。」
      → 解「有退養陰影者怕重蹈覆轍」（persona P2）。

### 🟡 P1 / P2 — 次要優化 ✅ 全部完成（2026-07-09）
- [x] 無責退回入口，複製一個輕量入口到「承諾決策點」（`Journey` 旅程末「中途把關」說明卡內，錨點連到 #support）。
- [x] 成長相簿近況卡加「像牠一樣的貓，正在找家 →」連結導流到 #cats（社會證明導流到轉換）。
- [x] 中途後台標記「不合適」後顯示「系統已幫對方轉介三隻同樣合拍的貓」；認養人端送出成功畫面同步加「如果這次沒有配上，系統會再推薦你其他同樣合拍的貓」。

### 🔧 2026-07-09 附帶修復（重要）
- [x] **Babel CDN 鎖版本**：`index.html` 原引用未鎖版本的 `unpkg.com/@babel/standalone`，unpkg 已升到 Babel 8（preset-react 預設 automatic runtime，會輸出 `import` 語句），導致整站白屏。已鎖回 `@babel/standalone@7`。若日後改用其他 CDN，務必鎖 v7。
- [x] **離線版重建**：`index.offline.html` 已依新文案重建（esbuild + tailwindcss 3，腳本邏輯同 §3），並以 Chromium 實測完整流程通過。

### 🟢 產品化方向（若要從 MVP 走向真實產品）
- [ ] 把假資料（6 隻貓、12 張相簿、帳本）接後端 / CMS。
- [ ] 照片佔位圖（目前是 SVG 毛色漸層）換成真實貓照；替換點在 `CatAvatar` 元件。
- [ ] 中途實名、健康護照、帳本改為可驗證的真實資料來源。
- [ ] 真人易用性測試：招募 5–8 位真實新手認養人做 moderated test，重點量測「送出意向」那一格的放棄率（報告 Part 6 方法備註）。
- [ ] 決定是否合併到 main / 開 PR（目前皆未做）。

---

## 5. 接手時務必遵守的設計硬規則

改任何文案前先看這幾條（違反會破壞整個產品邏輯）：

1. **全站禁用詞**：審核、資格、申請條件、追蹤、檢查、監督、合格。
   替換詞：配對、認識、旅程、曬貓、近況。（改完可用 grep 掃一次確認 0 筆）
2. **主 CTA 顏色全站唯一**（暖橘 `#C05621`），一個區塊只有一個主要行動。
3. **測驗一屏一題、每題可跳過、進度用正向句式**（「還差 N 題就能看結果」）。
4. **配對永遠不出現「無符合結果」**，最差也輸出「目前最合拍」＋誠實提醒。
5. **回報預設私密**（只給中途看）、提醒用系統中性語氣、不得用人來催。
6. **信任四錨點**必須都看得見：中途實名、健康護照、透明帳本、無責退回。
7. **觸控目標 ≥ 44px**、對比 ≥ 4.5:1、`prefers-reduced-motion`、可見 focus 樣式。

完整規範見 `cat-adoption-site/PROMPTS.md`（Prompt A 的【UX 與易用性硬規則】段）與 `README.md`。

---

## 6. 一句話交接

網站骨架正確（易用性報告證實高分功能全部踩在「鬆開前端審查感 + 守住後端不退養」兩個閥門上），且報告導出的 P0／P1／P2 五項改進已於 2026-07-09 全部落地並實測通過。**剩下的待辦都在「產品化方向」**：接真實資料、換真實貓照、招募真人做 moderated test 驗證「送出意向」那一格的放棄率。
