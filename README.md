# AI 協同開發模板 (Autocoder Template)

歡迎使用 AI 協同開發模板！這是一個專為搭配 [Gemini CLI](https://github.com/google/gemini-cli) 使用而設計的專案範本，旨在建立一個由 AI 輔助開發的標準化工作流程。

## 核心理念

開發者透過與 Gemini CLI 對話來下達指令，AI 會遵循專案內的規範 (`AI-Read/` 中的文件) 來進行程式碼的撰寫、修改與測試，實現高效率的人機協同開發。

---

## 環境設定 (Environment Setup)

在開始之前，您需要先安裝以下工具：

**1. Node.js**

請確保您的開發環境中已安裝 [Node.js](https://nodejs.org/) (建議版本為 18 或更高)。

**2. Gemini CLI**

Gemini CLI 是與 AI 互動的命令列介面。您可以透過 npm (Node.js 套件管理器) 進行全域安裝。

打開您的終端機，並執行以下指令：

```bash
npm install -g @google/gemini-cli
```

安裝完成後，執行 `gemini` 來進行首次設定，包含登入您的 Google 帳號。

---

## 專案結構

本專案模板包含以下幾個主要目錄：

-   `AI-Read/`：存放所有給 AI 參考的說明與規格文件。
    -   `README.md`：AI 的主要工作指引，定義了它的工作流程與規範。
    -   `Specs/$version-number.md`：功能規格文件。當有大型修改或新功能時，AI 會在此建立文件。
    -   `Tests/$version-number.md`：對應規格的測試計畫文件。
-   `backend/`：後端應用程式目錄，預設使用 **Python**。
-   `frontend/`：前端應用程式目錄，預預設使用 **React**。

---

## 開發流程 (Development Workflow)

使用此模板的建議開發流程如下：

1.  **啟動 AI**：在專案根目錄下，執行 `gemini` 指令來啟動 AI 代理。
2.  **需求溝通**：直接在對話中告訴 AI 您的開發需求，例如：「幫我建立一個登入用的 API」。
3.  **規格確認**：
    -   對於**小型修改**，AI 會在確認後直接動手。
    -   對於**大型修改**或**新功能**，AI 會遵循 `AI-Read/README.md` 的規範，先建立規格與測試文件，待您確認後再開始開發。
4.  **AI 開發**：AI 會根據需求與規格進行編碼。
5.  **審核與迭代**：AI 完成後，您可以審核其提交的程式碼，並透過對話進行後續的修改或測試。

## 快速開始 (Quick Start)

1.  安裝 Gemini CLI:
    ```bash
    npm install -g @google/gemini-cli
    ```
2.  進入專案目錄:
    ```bash
    cd /path/to/autocoder-template
    ```
3.  啟動 AI:
    ```bash
    gemini
    ```

現在，您可以開始透過對話，請 AI 協助您開發了！