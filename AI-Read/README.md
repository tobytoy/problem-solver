# AI 開發指引

本文件為 AI 在此專案中的工作指引，請遵循以下規範進行開發。

--- 

## 主要任務

你的主要任務是 **自動化解題**。你會遵循一個固定的工作流程，將原始的題目檔案轉換成結構化的 Markdown 解答，並在需要時將其轉換為其他文件格式。

--- 

## 專案結構

```
/
├── AI-Read/
│   ├── README.md         # 你的核心工作指引 (本文件)
│   └── ...
│
├── util/                 # 格式轉換工具
│   └── md_converter.py   # (範例) Python 轉換腳本
│
├── raw-problems/         # 原始題目存放區 (圖片, PDF)
├── raw-problems-md/      # 你處理後的 Markdown 題目
├── solved-problems/      # 最終產出的解題文件 (DOCX, PDF)
├── solved-problems-md/   # 你產出的 Markdown 解答
│
└── README.md             # 專案的總說明文件
```

--- 

## 工作流程 (Workflow)

當使用者指示你「處理新題目」時，請嚴格遵循以下步驟：

1.  **檢查新題目**：
    -   掃描 `raw-problems/` 目錄，找出尚未被處理的檔案。
    -   與 `raw-problems-md/` 中的檔案比對，確認哪些是新檔案。

2.  **轉換為 Markdown (OCR)**：
    -   對於每個新題目檔案（例如 `*.jpg`, `*.png`）：
        -   使用你的 OCR 能力讀取圖片中的文字。
        -   根據下方的 **【題目模板】**，建立一個新的 Markdown 檔案。
        -   將檔案儲存於 `raw-problems-md/`，檔名應與原題目對應（例如 `problem-001.jpg` -> `problem-001.md`）。
        -   **重點**：仔細校對 OCR 結果，特別是數學符號和公式，並用 LaTeX 格式表示。

3.  **解題**：
    -   讀取 `raw-problems-md/` 中的題目。
    -   根據下方的 **【解答模板】**，一步步撰寫詳細的解題過程。
    -   將包含完整解答的 Markdown 檔案儲存於 `solved-problems-md/`。檔名應與題目 ID 對應。

4.  **格式轉換 (可選)**：
    -   如果使用者要求，你需要使用 `util/` 目錄中的工具。
    -   例如，使用者可能說：「將 `MATH-TRI-001` 的解答轉成 Word 文件」。
    -   你需要執行類似以下的指令：
        ```bash
        python util/md_converter.py solved-problems-md/MATH-TRI-001.md solved-problems/MATH-TRI-001.docx
        ```
    -   在執行前，請先確認 `util/` 中是否存在對應的工具。

--- 

## 【題目模板】

```markdown
---
type: question
id: MATH-TRI-001          # 題目唯一識別碼（很重要，方便對應解答）
status: todo              # todo / reviewing / published
subject: 數學
topic: 三角函數           # 主題（比 subject 更細）
difficulty: 中            # 簡單 / 中 / 難
grade: 高一
source:
  type: image
  path: raw-problems/problem-001.jpg
tags: [三角函數, 餘弦定理]
created_at: 2025-01-01
---
# 題目描述
> [!abstract] 題目截圖預留位
> ![Question Image](path/to/image.jpg)

## 題目敘述（文字版）
（在此輸入 OCR 辨識後、或修正過的完整題目內容）
- 數學式請使用 LaTeX，例如：$f(x)=ax^2+bx+c$
- 若題目較長，可分條列說明已知條件
```

---

## 【解答模板】

```markdown
---
type: solution
question_id: MATH-TRI-001  # 對應題目
status: completed
subject: 數學
topic: 三角函數
difficulty: 中
grade: 高一
tags: [三角函數, 餘弦定理]
---

# 題目重述
> （複製題目的文字敘述，讓學生不必來回切換）
---

## 解題目標
本題的目標是：
- 利用 **餘弦定理** 求出未知邊長 $c$
---

## 核心概念整理
- **使用定理**：餘弦定理
$$c^2 = a^2 + b^2 - 2ab \cos C$$
- **適用時機**：已知兩邊及其夾角
⚠️ **常見錯誤**
- 誤用正弦定理（因為題目沒有對邊對角）
---
## 解題流程
### Step 1｜整理已知條件
根據題意可得：
- $a = 5$
- $b = 7$
- $\angle C = 60^\circ$
---

### Step 2｜選擇合適公式
因為已知「兩邊一夾角」，故使用 **餘弦定理**
---

### Step 3｜代入計算
$$ 
\begin{aligned}
c^2 &= 5^2 + 7^2 - 2(5)(7)\cos 60^\circ \\
&= 25 + 49 - 35 \\
&= 39
\end{aligned}
$$

---

### Step 4｜求解結果
$$c = \sqrt{39}$$
---

## 最終答案
✅ **$c = \sqrt{39}$**
---

## 延伸思考（加分）
- 若要求三角形面積，可使用：
$$S=\frac{1}{2}ab\sin C$$
- 若角度改為鈍角，結果會有什麼變化？
```

```