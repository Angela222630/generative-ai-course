# Unity 2D 初學者知識庫索引（LLM Wiki Index）

本知識庫專門為大學「生成式 AI」第十週作業建置，旨在為完全沒有 Unity 經驗的大學初學者提供結構化、高可讀性、且 100% 嚴格溯源自 Unity 6.0 官方文件的 2D 遊戲開發知識庫。

---

## 一、 知識庫分類與章節進度（全 6 章已全數完成 Ingest）

| 主題編號 | 分類主題 | Wiki 章節檔案 | 對應官方來源名稱 | 目前狀態 | 官方版本 |
| :---: | :--- | :--- | :--- | :---: | :---: |
| **主題 1** | **Unity 基本概念** | [01_basics.md](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/01_basics.md) | Game objects | **已完成 (Batch 1)** | Unity 6.0 |
| **主題 2** | **2D 圖像與角色** | [02_sprites.md](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/02_sprites.md) | Sprite Renderer component reference | **已完成 (Batch 1)** | Unity 6.0 |
| **主題 3** | **場景與地圖** | [03_tilemaps.md](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/03_tilemaps.md) | Tilemaps | **已完成 (Batch 2)** | Unity 6.0 |
| **主題 4** | **C# 腳本** | [04_scripts.md](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/04_scripts.md) | Creating scripts | **已完成 (Batch 3)** | Unity 6.0 |
| **主題 5** | **2D 物理** | [05_physics.md](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/05_physics.md) | Rigidbody 2D | **已完成 (Batch 2)** | Unity 6.0 |
| **主題 6** | **測試與除錯** | [06_playmode.md](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/06_playmode.md) | The Toolbar | **已完成 (Batch 3)** | Unity 6.0 |

---

## 二、 核心知識導覽（全 6 篇完整概覽）

### 1. [主題 1：01_basics.md - Unity 基本概念](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/01_basics.md)
* **GameObject 容器論**：遊戲內的一切實體皆是 GameObject，其本身無預設功能，依賴掛載組件賦予能力。
* **Transform 不可移除**：每個 GameObject 唯一必備的組件是 Transform，記錄其 Position（位置）、Rotation（旋轉）與 Scale（縮放）。
* **Component 組合模式**：藉由組合不同組件（例如 Light、Renderer、Collider），定義出物件的具體外觀與功能。

### 2. [主題 2：02_sprites.md - 2D 圖像與角色](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/02_sprites.md)
* **Sprite Renderer 組件職責**：將 2D 圖片（Sprite）渲染在場景中。
* **常用屬性**：Sprite 指定圖片、Color 濾鏡染色、Flip 水平/垂直鏡射翻轉（不影響 Transform 座標）。
* **Draw Mode**：Simple（等比縮放）、Sliced（九宮格拉伸）、Tiled（連續平鋪）。
* **圖層遮擋排序（核心）**：
  * **Sorting Layer**：決定大層級繪製優先序。
  * **Order in Layer**：同層子排序，**數值越小先繪製（底層），數值越大後繪製（頂層遮擋）**。

### 3. [主題 3：03_tilemaps.md - 場景與地圖](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/03_tilemaps.md)
* **Tilemap 核心定位**：透過在場景上繪製瓦片（Painting Tiles），直觀快速建立 2D 遊戲世界與環境地形。
* **兩大步驟**：建立 Tile Palette（瓦片調色盤，放瓦片資產） ➔ 建立 Tilemap（畫布區域）並使用筆刷塗抹作畫。
* **三大佈局類型**：Rectangular（矩形，預設值）、Hexagonal（六邊形，策略遊戲）、Isometric（等角投影，2.5D 立體錯覺）。

### 4. [主題 4：04_scripts.md - C# 腳本基礎](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/04_scripts.md)
* **腳本即自訂組件**：繼承自 `MonoBehaviour` 的 C# 腳本，就是自訂組件（Custom Components），可掛載至 GameObject 控制其行為。
* **建立管道**：透過主選單 `Assets > Create > Scripting` 或專案視窗工具列 `+ > Scripting` 建立。
* **命名注意事項**：建立時及時命名，保持檔名與類別名稱一致。

### 5. [主題 5：05_physics.md - 2D 物理與剛體](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/05_physics.md)
* **Rigidbody 2D 核心定位**：讓 GameObject 在 2D 物理引擎控制下行動，賦予物理行為。
* **物理反應**：自然具備重力反應（Gravity）、質量（Mass）、阻力（Drag）與動量（Momentum）。
* **Body Type 概念**：決定剛體在物理世界中的行為模式。
* **Simulated 屬性**：控制該物件及其附加組件是否參與物理模擬計算的開關（Start / Stop）。

### 6. [主題 6：06_playmode.md - 測試與除錯](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/06_playmode.md)
* **Toolbar 工具列特性**：位於編輯器頂端，唯一固定不可重新排列的區塊。
* **Play Mode Controls（核心三按鈕）**：
  * **Play**：進入 / 退出運行模式，切換至 Game view 進行實機測試。
  * **Pause**：凍結遊戲運行畫面，便於從容檢查異常。
  * **Step**：單幀向前推進一步（move forward by one frame），進行逐幀精密除錯。
* **輔助工具**：Layout 版面配置切換、Undo History 復原歷程、Global Search 全域搜尋。

---

## 三、 嚴格溯源（Strict Grounding）守則聲明
本 Wiki 為後續 HTML 教學簡報與測驗題目的**唯一知識來源**。未記錄於本 Wiki 之 Unity 功能、API 或外部外掛，嚴禁於教學簡報中發揮或捏造。
