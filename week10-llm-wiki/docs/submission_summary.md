# 專案成果摘要與繳交說明（Submission Summary）

本檔案彙整大學「生成式 AI」第十週作業之專案成果、檔案結構與平台繳交說明草稿。

---

## 一、 專案基本資訊

* **專案名稱**：從零開始的 Unity 2D 遊戲開發：LLM Wiki 與互動教學簡報系統
* **專案簡介**：
  本專案為完全沒有 Unity 經驗的大學初學者所設計。系統先自 Unity 6.0 官方手冊精確 Ingest 六篇核心文件，建立具備嚴格溯源（Strict Grounding）的本地端 LLM Wiki 知識庫；接著透過 Graph / Loop 狀態機工作流程，以此 Wiki 為唯一知識來源，製作出單檔獨立、可離線瀏覽、包含雪地狗狗情境與互動小測驗的 10 頁 HTML 教學簡報。

---

## 二、 六篇核定 Unity 6.0 官方主要資料來源

本專案內容 100% 溯源自以下 6 篇 Unity 官方文件，未依賴任何外部非官方教學：

| 編號 | 分類主題 | 官方文件標題 | 官方原始 URL |
| :---: | :--- | :--- | :--- |
| **1** | Unity 基本概念 | Game objects | `https://docs.unity.com/en-us/engine/6000.0/manual/working-with-gameobjects/game-objects` |
| **2** | 2D 圖像與角色 | Sprite Renderer component reference | `https://docs.unity.com/en-us/engine/6000.0/manual/unity2d/sprite/sprite-renderer-reference` |
| **3** | 場景與地圖 | Tilemaps | `https://docs.unity.com/en-us/engine/6000.0/manual/unity2d/tilemaps/tilemaps` |
| **4** | C# 腳本基礎 | Creating scripts | `https://docs.unity.com/en-us/engine/6000.0/manual/scripting/get-started/creating-scripts` |
| **5** | 2D 物理與剛體 | Rigidbody 2D | `https://docs.unity.com/en-us/engine/6000.0/manual/unity2d/2d-physics/rigidbody-2d` |
| **6** | 測試與除錯 | The Toolbar | `https://docs.unity.com/en-us/engine/6000.0/manual/unity-editor/editor-navigating-managing/toolbar` |

---

## 三、 本地端 LLM Wiki 六大章節功能

所有提煉後的繁體中文結構化知識存放於 `wiki/` 目錄中，並以 `wiki/INDEX.md` 作為總索引：

1. **[01_basics.md](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/01_basics.md)**：GameObject 容器論、Component 功能組合模式、唯一不可刪除之 `Transform` 組件（Position, Rotation, Scale）。
2. **[02_sprites.md](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/02_sprites.md)**：Sprite Renderer 渲染組件、Flip 貼圖翻轉特性、2D 圖層排序規則（`Sorting Layer` 與 `Order in Layer` 數值越大顯示在越上層）。
3. **[03_tilemaps.md](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/03_tilemaps.md)**：瓦片地圖概念、Tile Palette（調色盤）與 Tilemap（網格畫布）作畫兩大步驟、三種佈局（Rectangular 矩形、Hexagonal 六邊形、Isometric 等角投影）。
4. **[04_scripts.md](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/04_scripts.md)**：建立「繼承自 `MonoBehaviour` 的 C# 腳本即自訂組件」心智模型，說明編輯器內建立與命名步驟。
5. **[05_physics.md](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/05_physics.md)**：Rigidbody 2D 啟用物理受控、四大物理反應（Gravity 重力、Mass 質量、Drag 阻力、Momentum 動量）、Body Type 類型與 `Simulated` 模擬總開關。
6. **[06_playmode.md](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/06_playmode.md)**：頂部固定工具列（Toolbar）特性，核心三按鈕：Play（切換 Game view 實機測試）、Pause（畫面凍結）、Step（單幀向前步進除錯）。

---

## 四、 Graph / Loop 工作流程說明

專案採用狀態機（State Machine）嚴格推進，完整架構詳見 [docs/workflow_graph.md](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/docs/workflow_graph.md) 與圖檔 [docs/workflow_graph.png](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/docs/workflow_graph.png)：
* **Node 0（規格定義）**：制定 `AGENTS.md` 規則。
* **Node 1 ~ Node 3（分批 Ingest 與驗證）**：分三批下載官方正文存入 `raw/`，提煉 Markdown 知識存入 `wiki/`，每批執行 Node 3 檢驗（來源、語言、版本、溯源與無幻覺檢查），若失敗依類型退回 Node 1 或 Node 2（上限 3 輪）。實務執行自動 Retry 次數為 0 次。
* **Node 4（大綱與缺口審查）**：規劃簡報大綱與知識缺口報告，經人工審查核准（HITL Checkpoint 1）。
* **Node 5 ~ Node 6（HTML 簡報生成與測試）**：生成單檔 HTML 簡報並執行事件流測試，若有錯誤退回 Node 5 修正。實務執行自動 Retry 次數為 0 次。
* **【HITL 人工驗收與需求調整】**：人工實測後提出 P8 鍵盤操作優化（WASD 控狗、左右方向鍵切頁），由工程端解耦完成，此為人機協同需求調整而非自動測試失敗。
* **Node 7（反思與交付）**：撰寫反思報告、產出工作流程圖並進行全專案成果驗收。

---

## 五、 HTML 教學簡報功能與開啟方式

* **檔案位置**：[presentation/index.html](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/presentation/index.html)
* **開啟方式**：直接以任何現代瀏覽器（如 Chrome, Edge, Safari, Firefox）雙擊檔案即可開啟，**無需連網、無需架設本機伺服器、無需安裝任何套件**。
* **核心功能**：
  * **純單檔離線架構**：CSS 樣式、SVG 圖像、JS 腳本完全內嵌，零外部 CDN 依賴。
  * **深藍雪夜視覺風格**：搭配高對比淺藍卡片與奶油白文字，排版簡潔大方。
  * **多元投影片導航**：支援底部上一頁/下一頁按鈕、頂部 10 圓點進度直接跳轉，以及鍵盤全域 `ArrowLeft` / `ArrowRight` 切換。
  * **第 8 頁狗狗座標互動模擬器**：純前端網頁繪製，使用鍵盤 **W / A / S / D** 或畫面四向按鈕控制小狗移動，即時呈現虛擬 Unity 座標 `(X, Y)` 數值跳動，並醒目標註網頁模擬免責聲明。
  * **第 10 頁知識小測驗**：點擊按鈕展開 3 題單選題，點選具備即時變色回饋（綠色正確/紅色錯誤）與 Wiki 原文依據解析卡。

---

## 六、 實際執行與測試摘要

* **真實 Ingest 歷程**：分 3 批依序成功下載並降噪 6 篇官方文件，Node 3 批次檢驗均一次通過（Retry Count = 0）。
* **人機協同優化**：在階段 3 生成簡報後，經人工驗收檢視，提出「狗狗移動改用純 WASD、方向鍵保留為全域切頁」之規格優化，順利完成程式碼解耦。
* **代碼檢驗實測**：透過測試腳本完成靜態結構檢查（0 外連網址、10 頁完整度）與 JavaScript 事件模擬測試（WASD 移動小狗、左右鍵切頁、四向按鈕點擊、座標公式映射）。

---

## 七、 專案檔案清單（供教師與評審查閱）

```text
unity-2d-llm-wiki/
├── AGENTS.md                  # 專案規格書、引用規範、Loop 路由與停止條件
├── raw/                       # 官方原始技術文章（降噪純文字）
│   ├── 01_game_objects.md
│   ├── 02_sprite_renderer.md
│   ├── 03_tilemaps.md
│   ├── 04_creating_scripts.md
│   ├── 05_rigidbody_2d.md
│   └── 06_the_toolbar.md
├── wiki/                      # 本地端結構化 LLM Wiki 知識庫（繁中、含四項溯源標籤）
│   ├── INDEX.md               # 知識庫總導覽與章節索引
│   ├── 01_basics.md           # 主題 1：Unity 基本概念
│   ├── 02_sprites.md          # 主題 2：2D 圖像與角色
│   ├── 03_tilemaps.md         # 主題 3：場景與地圖
│   ├── 04_scripts.md          # 主題 4：C# 腳本基礎
│   ├── 05_physics.md          # 主題 5：2D 物理與剛體
│   └── 06_playmode.md         # 主題 6：測試與除錯
├── docs/                      # 規劃、缺口檢驗、反思與交付摘要
│   ├── presentation_outline.md# 10 頁雪地狗狗主題簡報大綱與測驗題設計
│   ├── knowledge_gap_report.md# 知識缺口檢驗與簡化處置對照表
│   ├── reflection.md          # 課堂反思報告（動機、流程、真實經驗、心得）
│   ├── workflow_graph.md      # Graph / Loop 工作流程圖說明與 Mermaid 原始碼
│   ├── workflow_graph.png     # 專案流程圖高解析度圖檔（適合繳交平台展示）
│   └── submission_summary.md  # 本份成果摘要與繳交說明
├── presentation/              # HTML 簡報成果
│   └── index.html             # 單一獨立 HTML 檔案（內嵌 CSS、JS、SVG，支援離線瀏覽）
└── logs/                      # 真實執行歷程
    └── execution_log.md       # 自第一批起每步真實結果、檢查紀錄與優化歷程
```

---

## 八、 課程平台繳交說明草稿（可直接複製張貼）

```markdown
【生成式 AI 第十週作業繳交】

作業主題：從零開始的 Unity 2D 遊戲開發：LLM Wiki 與互動教學簡報系統

一、作業成果概述：
本專案為完全沒有 Unity 經驗的大學初學者打造。我們先從 Unity 6.0 官方手冊精確 Ingest 六篇核心文件，建立具備嚴格溯源（Strict Grounding）的本地端 LLM Wiki 知識庫；接著依循 Graph / Loop 狀態機工作流程，以此 Wiki 為唯一知識來源，製作出單檔獨立、可離線瀏覽的 10 頁 HTML 教學簡報。

二、核心交付成果：
1. 本地端 LLM Wiki（wiki/）：
   - 收錄 6 篇官方核心篇章，轉譯為繁體中文結構化知識，每個知識點均標記【官方來源】、【原始網址】、【段落章節】、【適用版本：Unity 6.0】。
   - 包含總索引檔案 wiki/INDEX.md。
2. 單一 HTML 教學簡報（presentation/index.html）：
   - 採用「製作一個簡單的雪地狗狗場景」情境貫穿 10 頁教學。
   - 零外部 CDN 或圖片依賴，100% 支援離線雙擊開啟。
   - 支援上一頁/下一頁、頁碼指示器跳轉、全域鍵盤左右方向鍵切頁。
   - 第 8 頁提供純前端小狗移動座標模擬器（支援鍵盤 WASD 與畫面按鈕，即時顯示虛擬 Unity 座標變化，並附醒目免責聲明）。
   - 第 10 頁具備「開始小測驗」按鈕，展開 3 題單選小測驗，點選後提供即時正誤回饋與 Wiki 原文依據解析。
3. 規劃與反思文件（docs/）：
   - presentation_outline.md：10 頁簡報逐頁規劃與 Wiki 映射表。
   - knowledge_gap_report.md：逐項檢視輸入系統、位移 API、碰撞幾何等缺口之簡化方案。
   - reflection.md：完整記錄專案動機、流程分析、防範幻覺之經驗與心得。
4. 真實執行紀錄（logs/execution_log.md）：
   - 自第一批 Ingest 起如實記錄每個節點狀態、檢驗數據與操作優化歷程，無虛構紀錄。

三、檔案開啟方式：
直接使用瀏覽器開啟專案目錄中的 presentation/index.html 即可開始瀏覽教學簡報。
```
