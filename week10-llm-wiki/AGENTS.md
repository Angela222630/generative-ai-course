# AGENTS.md - 專案規範與工作流程指南

本專案為大學「生成式 AI」課程第十週作業：「從零開始的 Unity 2D 遊戲開發」之 LLM Wiki 與 HTML 教學簡報生成系統。

---

## 一、 專案目標與教學定位

1. **專案目標**：
   - 建立高透明度、精確溯源的本地端 LLM Wiki（知識庫）。
   - 以該 Wiki 為**唯一知識來源**，透過結構化 Graph / Loop 工作流製作可獨立於瀏覽器瀏覽的單檔 HTML 教學簡報。
   - 保留真實的執行紀錄、自動檢驗歷程與修正紀錄，嚴禁事後虛構。
2. **目標讀者**：完全沒有 Unity 經驗的大學初學者。
3. **教學深度與風格**：
   - 聚焦於認識 Unity 2D 遊戲的基本製作流程與心智模型（Scene、GameObject、Component、Sprite、Tilemap、腳本概念、基本物理與除錯）。
   - **不深入**複雜的 C# 語法細節、進階物理數學計算或複雜的碰撞觸發事件。
   - 語言採用**繁體中文**，保留 Unity 英文專有名詞（如 GameObject, Sprite Renderer, Rigidbody 2D）。

---

## 二、 官方核定主要資料來源（Unity 6.0 / 6000.0）

本專案嚴格收斂並鎖定以下 6 篇官方文件作為主要資料來源，未經人工許可不得擅自擴充：

| 主題編號 | Wiki 分類主題 | 官方文件標題 | 官方原始網址 |
| :---: | :--- | :--- | :--- |
| **主題 1** | Unity 基本概念 | Game objects | `https://docs.unity.com/en-us/engine/6000.0/manual/working-with-gameobjects/game-objects` |
| **主題 2** | 2D 圖像與角色 | Sprite Renderer component reference | `https://docs.unity.com/en-us/engine/6000.0/manual/unity2d/sprite/sprite-renderer-reference` |
| **主題 3** | 場景與地圖 | Tilemaps | `https://docs.unity.com/en-us/engine/6000.0/manual/unity2d/tilemaps/tilemaps` |
| **主題 4** | C# 腳本 | Creating scripts | `https://docs.unity.com/en-us/engine/6000.0/manual/scripting/get-started/creating-scripts` |
| **主題 5** | 2D 物理 | Rigidbody 2D | `https://docs.unity.com/en-us/engine/6000.0/manual/unity2d/2d-physics/rigidbody-2d` |
| **主題 6** | 測試與除錯 | The Toolbar | `https://docs.unity.com/en-us/engine/6000.0/manual/unity-editor/editor-navigating-managing/toolbar` |

---

## 三、 目錄與檔案結構規範

```text
unity-2d-llm-wiki/
├── AGENTS.md                  # 專案規範、流程、檢查條件與原則說明
├── raw/                       # 存放由官方網址擷取之原始文字檔（依篇命名）
│   ├── 01_game_objects.md
│   ├── 02_sprite_renderer.md
│   ├── 03_tilemaps.md
│   ├── 04_creating_scripts.md
│   ├── 05_rigidbody_2d.md
│   └── 06_the_toolbar.md
├── wiki/                      # 提煉整理後之結構化知識庫（繁體中文、含精準溯源）
│   ├── INDEX.md               # Wiki 總索引與分類導覽
│   ├── 01_basics.md           # Unity 基本概念
│   ├── 02_sprites.md          # 2D 圖像與角色
│   ├── 03_tilemaps.md         # 場景與地圖
│   ├── 04_scripts.md          # C# 腳本與生命週期
│   ├── 05_physics.md          # 2D 物理與剛體
│   └── 06_playmode.md         # 測試與除錯
├── docs/                      # 規劃文件、大綱與反思報告
│   ├── presentation_outline.md# 簡報大綱、頁面規劃與題目設計
│   ├── knowledge_gap_report.md# 知識缺口與簡化方案對照表
│   └── reflection.md          # 課堂心得與反思報告
├── presentation/              # HTML 簡報成果
│   └── index.html             # 單一獨立 HTML 檔案（內嵌 CSS 與 JS）
└── logs/                      # 執行紀錄與檢查日誌
    └── execution_log.md       # 自第一批 Ingest 起記錄每步真實結果、檢查項與修正履歷
```

---

## 四、 嚴格溯源（Strict Grounding）與知識缺口處理原則

1. **唯一知識來源約束（Strict Grounding）**：
   - 後續產出之 HTML 簡報內容、小測驗與說明，必須 100% 來自 `wiki/` 知識庫。
   - 嚴格禁止利用模型內建知識捏造或外插未列於 Wiki 中的 Unity API 或概念。
   - 每個重要知識點均需標明：【官方來源】、【原始網址】、【段落章節】、【適用版本：Unity 6.0】。
2. **知識缺口（Knowledge Gap）處理原則**：
   - 若 6 篇官方文件不足以支援特定功能（如鍵盤輸入 API、Collider 2D 幾何碰撞、Trigger 回調事件、SceneManager 切換）：
     - **第一優先**：**簡化教學內容**，回歸現有 6 篇文件涵蓋的核心觀念（例如：腳本講 `Start/Update` 概念而不捏造 `Input` API；物理講 `Rigidbody2D` 三種 Body Type 與重力而不捏造 `Collider2D` 屬性）。
     - **第二優先**：在 `docs/knowledge_gap_report.md` 明確條列缺少項目與受影響之簡報頁面。
     - **第三優先**：若特定功能有教學必要，必須先提出最少量的官方補充來源，**由人工核准後方可匯入**，不得自行擴充。
3. **狗狗移動 Demo 定位**：
   - 簡報中的狗狗移動展示為**純前端網頁視覺互動模擬（HTML/CSS/JS Mock）**。
   - 必須清楚標註免責聲明：*「本模擬僅供體會每一幀更新座標之概念，非 Unity 引擎實際執行程式碼」*。

---

## 五、 Graph / Loop 流程與檢查機制

專案採用狀態機（State Machine）流程推進，包含局部自我修正迴圈（Self-Correction Loop）：

### 1. 節點定義與流向

```
[Node 0: Init Specification] ──(Pass)──> [Node 1: Batch Ingestion (raw/)]
                                               │
                                               ▼
                                         [Node 2: Wiki Distillation (wiki/)]
                                               │
                                               ▼
                                         [Node 3: Batch Verification]
                                          ├─ Pass ──> (若批次未完則回 Node 1，若完成則至 Node 4)
                                          └─ Fail ──> [Node 2 修正] (Loop, max 3 次)
                                               │
                                               ▼
                                         [Node 4: Outline & Gap Report]
                                               │
                                               ▼
                                         【HITL 審查點：確認簡報大綱】
                                               │
                                               ▼
                                         [Node 5: Presentation Generation (HTML)]
                                               │
                                               ▼
                                         [Node 6: Presentation Verification]
                                          ├─ Pass ──> [Node 7: Reflection & Delivery]
                                          └─ Fail ──> [Node 5 修正] (Loop, max 3 次)
                                               │
                                               ▼
                                         【HITL 審查點：最終驗收】
```

### 2. 通過條件、失敗判定與 Loop 規則

| 檢查節點 | 檢查項（Pass Criteria） | 失敗判定（Failure Condition） | 失敗退回節點與處置 |
| :--- | :--- | :--- | :--- |
| **Node 3: Batch Verification** | 1. `raw/` 內容真實對應官方 URL。<br>2. `wiki/` 採用繁體中文並保留英文專有名詞。<br>3. 具備明確來源 URL、章節與 Unity 6.0 標註。<br>4. 無任何外插幻覺知識。 | 1. 原始資料擷取失敗或內容不完整。<br>2. Wiki 內容錯誤、引用缺失或出現未獲來源支持的知識。<br>3. 官方網址持續失效或阻擋。 | • 情況 1：退回 **Node 1** 重新擷取<br>• 情況 2：退回 **Node 2** 重新整理<br>• 情況 3：**立即停止自動流程**，呈報人工確認，嚴禁自行替換來源 |
| **Node 6: Presentation Verification** | 1. 單一 HTML 檔案無外連 CSS/JS 依賴。<br>2. 投影片換頁與小測驗互動功能正常。<br>3. 內容 100% 映射 Wiki，無超綱技術。<br>4. 附有網頁模擬免責聲明。<br>5. **驗證真實性**：測試結果必須記錄實際驗證方法。若未實際於瀏覽器或環境操作驗證，不得宣稱互動功能或離線測試通過。 | 1. 頁面無法離線正常開啟或版面錯亂。<br>2. 換頁或測驗按鈕故障。<br>3. 簡報出現 Wiki 未提及之概念。<br>4. 缺乏實際驗證紀錄即宣稱通過。 | 退回 **Node 5** 重新生成修正 |

### 3. Loop 停止與中斷條件
- 每個檢查節點的自動修正上限為 **3 輪（Retry Count ≤ 3）**。
- 若修正 3 次仍未通過檢查，必須**立即停止自動流程**，將具體錯誤、可能原因與當前狀態記錄於 `logs/execution_log.md`，並呈報人工確認處理。

---

## 六、 人工確認檢查點（Human-in-the-Loop Checkpoints）

為了確保每一步都在控制範圍內，專案嚴格禁止連續自動執行到底，必須在以下時間點暫停並等待人工確認：

1. **檢查點 0（規範確認）**：確認 `AGENTS.md` 內容。
2. **檢查點 1（第 1 批 Ingest 確認）**：完成主題 1 與主題 2 的 `raw/`、`wiki/` 及日誌後暫停。
3. **檢查點 2（第 2 批 Ingest 確認）**：完成主題 3 與主題 5 的 `raw/`、`wiki/` 及日誌後暫停。
4. **檢查點 3（第 3 批 Ingest 確認）**：完成主題 4 與主題 6 的 `raw/`、`wiki/` 及日誌後暫停。
5. **檢查點 4（簡報大綱與缺口審查）**：完成 `presentation_outline.md` 與 `knowledge_gap_report.md` 後暫停。
6. **檢查點 5（最終交付驗收）**：完成 HTML 簡報、日誌與反思報告後進行整體驗收。
