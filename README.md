# 合拍 PawMatch 🐾

> 一個把「審核你」換成「認識你」的貓咪認養平台 MVP——依據四場台灣貓咪中途之家的深度訪談設計，並附完整的易用性測試報告。

## 🌐 線上瀏覽

| 內容 | 連結 |
|---|---|
| **專案導覽首頁** | https://pokemonida99.github.io/pawmatch-handoff/ |
| **認養網站 Demo**（可完整走完配對流程） | https://pokemonida99.github.io/pawmatch-handoff/cat-adoption-site/index.offline.html |
| **易用性測試報告**（互動版） | https://pokemonida99.github.io/pawmatch-handoff/reports/usability-report.html |

## 這個專案在解什麼問題

台灣的貓咪中途之家普遍卡在同一個矛盾：**審核越嚴，退養越少，但願意走進審核的人也越少**。四位受訪中途幾乎逐字說出同樣的話——「問卷一出去，人就不見了」、「越來越多人不喜歡到中途認養，覺得要被檢查很多」。

瓶頸不在曝光，而在兩個閥門：**「人願不願意走進審核」決定有多少人開始，「配對品質好不好」決定貓會不會被退回來。**

## 研究與設計流程

```
① 訪談        4 場中途之家深度訪談 → 逐字稿（research/）
② 分析        領養者行為與心理 8 條洞察（證據 → 機制 → 設計意涵）
③ 設計        網站 MVP：凡「轉換率」與「被審查感」衝突，一律先消除被審查感
④ 驗證        3 位壓力測試 persona 模擬走查 → 十大功能對「領養率」貢獻度評分
⑤ 落地        報告導出的 P0/P1/P2 五項改進全部實作，Chromium 實測通過
```

**核心設計主張**：用生活樣態配對取代審核問卷、用個性敘事取代條件比對、用去人化的曬貓回報取代監控式追蹤；同時守住中途在乎的底線——中途保有最終判斷權、無責退回明路、健康護照與透明帳本。

**易用性測試的一句話結論**：評分最高的功能全部踩在「鬆開前端審查感」與「守住後端不退養」兩個閥門上；三個流失卡點都集中在「送出意向」那一刻——怕被打槍、怕留底、怕重蹈覆轍——已用三句文案接住。

## Repo 結構

```
├── index.html                    ← 專案導覽首頁（GitHub Pages 入口）
├── HANDOFF.md                    ← 交接文件：進度、待辦、設計硬規則
├── cat-adoption-site/            ← 網站本體
│   ├── index.html                ← 可讀原始碼版（React + Tailwind CDN，要改程式改這份）
│   ├── index.offline.html        ← 離線建置版（零相依、雙擊即開，展示用這份）
│   ├── PROMPTS.md                ← 原始 Prompt A / B1–B5 / C 全文
│   ├── README.md                 ← 設計計畫、色票、驗收紀錄
│   └── USABILITY-REPORT.md       ← 易用性測試報告（文字版）
├── reports/
│   └── usability-report.html     ← 易用性測試報告（互動版）
└── research/
    └── interview_*.txt           ← 4 場中途訪談逐字稿（分析原料）
```

## 本機執行

不需安裝任何東西：

```bash
git clone https://github.com/pokemonida99/pawmatch-handoff.git
# 直接雙擊 cat-adoption-site/index.offline.html 即可

# 或起本機伺服器
python3 -m http.server 8000
# 瀏覽 http://localhost:8000
```

要接續開發請先讀 [`HANDOFF.md`](HANDOFF.md)（含**設計硬規則**：全站禁用「審核／資格／追蹤／檢查」等詞、主 CTA 顏色全站唯一、配對永遠不出現「無符合結果」等，違反會破壞整個產品邏輯）。

## 資料聲明

本站為研究示意：貓咪、中途、成長相簿與透明帳本皆為假資料；persona 為訪談洞察的具象化，非真實個資。

---

🤖 Generated with [Claude Code](https://claude.com/claude-code)
