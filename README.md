# AI 協同解題專案 (AI Problem-Solving Repository)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

歡迎來到 AI 協同解題專案！這是一個展示如何利用 AI (搭配 [Gemini CLI](https://github.com/google/gemini-cli)) 建立一個標準化、自動化的解題工作流程的範例專案。

## 核心理念

本專案的核心是將「解題」這個過程拆解成一系列標準化、可由 AI 自動執行的步驟。開發者 (或內容管理者) 負責提供原始題目、審核結果，而 AI 負責處理中間所有繁瑣的轉換、排版與解題工作。

---

## 快速開始 (Quick Start)

1.  **環境設定**：
    請確保您已安裝 [Node.js](https://nodejs.org/) (v18+) 與 [Gemini CLI](https://github.com/google/gemini-cli)。
    ```bash
    npm install -g @google/gemini-cli
    ```
    首次使用請執行 `gemini` 並依照指示登入 Google 帳號。

2.  **啟動 AI**：
    進入專案目錄，執行 `gemini` 指令。
    ```bash
    cd /path/to/gemini-autocoder
    gemini
    ```

3.  **下達指令**：
    告訴 AI 你想做什麼，例如：「幫我處理 `raw-problems` 裡的新題目」。

---

## 工作流程 (Workflow)

本專案的解題流程如下：

1.  **提供題目**：將原始題目檔案 (如圖片、PDF)放入 `raw-problems/` 資料夾。
2.  **AI 進行 OCR 與格式化**：AI 讀取新題目，使用光學字元辨識 (OCR) 技術將其轉換為 Markdown 格式，並存入 `raw-problems-md/`。這個過程包含修正 OCR 錯誤、將數學式轉換為 LaTeX 等。
3.  **AI 解題**：AI 根據 Markdown 格式的題目，撰寫詳細的解題步驟，並將結果存於 `solved-problems-md/`。解題步驟會遵循 `AI-Read/README.md` 中定義的標準模板。
4.  **格式轉換**：AI 使用 `util/` 中的 Python 腳本，將已解題的 Markdown 文件轉換為使用者需要的其他格式 (如 DOCX, PDF)，並存放在 `solved-problems/`。
5.  **人工審核**：最後，由人類專家審核 `solved-problems-md/` 或 `solved-problems/` 中的最終結果，確保品質。

---

## 專案結構

```
/
├── AI-Read/
│   ├── README.md         # AI 的核心工作指引 (包含解題模板)
│   ├── Specs/            # (可選用) 複雜任務的規格文件
│   └── Tests/            # (可選用) 對應的測試計畫
│
├── util/                 # 格式轉換工具 (例如: md to docx)
│   └── md_converter.py   # (範例) Python 轉換腳本
│
├── raw-problems/         # 原始題目存放區 (圖片, PDF)
├── raw-problems-md/      # AI 處理後的 Markdown 題目
├── solved-problems/      # 最終產出的解題文件 (DOCX, PDF)
├── solved-problems-md/   # AI 產出的 Markdown 解答
│
├── .gitignore
├── LICENSE
└── README.md             # 專案說明文件 (給人類看的)
```

-   `AI-Read/`：AI 的大腦，定義其所有行為準則。
-   `util/`：放置各種輔助工具腳本。
-   `*problems*/` 系列目錄：構成了整個解題流程的資料管道 (Data Pipeline)。

---

現在，就開始您的 AI 自動化解題之旅吧！
