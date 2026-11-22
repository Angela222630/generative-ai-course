# Wiki: 06. 測試與除錯（The Toolbar 與 Play Mode）

本篇整理自 Unity 6.0 官方文件，旨在為完全沒有 Unity 經驗的大學初學者解說編輯器頂部工具列（The Toolbar）的核心功能，特別是進行遊戲即時測試與除錯最重要的 Play Mode 控制項。

---

## 知識點 1：什麼是 The Toolbar（頂部工具列）？

- **【官方來源】**：The Toolbar
- **【原始網址】**：`https://docs.unity.com/en-us/engine/6000.0/manual/unity-editor/editor-navigating-managing/toolbar`
- **【段落章節】**：The Toolbar
- **【適用版本】**：Unity 6.0 (6000.0)

### 核心觀念
1. **位置與特性**：**Toolbar** 位於 Unity 編輯器的最頂端。它並非一般的子視窗，而且是 Unity 編輯器介面中**唯一無法被重新排列或拖曳移動的固定區塊**。
2. **主要職責**：提供開發者快速存取 Unity 最常用的核心工具與控制選項（包含帳號、版面配置、復原歷史以及最關鍵的遊戲運行測試按鈕）。

---

## 知識點 2：Play Mode Controls（運行模式控制項）

- **【官方來源】**：The Toolbar
- **【原始網址】**：`https://docs.unity.com/en-us/engine/6000.0/manual/unity-editor/editor-navigating-managing/toolbar`
- **【段落章節】**：Property 表格 - Play Mode Controls
- **【適用版本】**：Unity 6.0 (6000.0)

在工具列正中央的 Play Mode 控制按鈕，是用來控制**遊戲視窗（Game view）**中專案執行狀態的核心樞紐：

| 控制按鈕 | 操作與功能說明 | 初學者測試與除錯應用 |
| :--- | :--- | :--- |
| **Play（播放按鈕）** | 點擊此按鈕可將編輯器切換為 **Play mode（運行模式）**；再次點擊則退出運行模式。 | 初學者完成物件擺放或掛載腳本後，按下 Play 即可在 Game view 中即時測試遊戲真實執行效果。 |
| **Pause（暫停按鈕）** | 點擊此按鈕可**暫停（Pause）當前正在運行的 Play mode**。 | 當遊戲中發生異常（如物件突然消失或穿透）時，可即刻凍結畫面，方便在 Scene 或 Inspector 中從容檢查物件數值。 |
| **Step（步進按鈕）** | 在暫停狀態下點擊，可使遊戲**向前推進恰好一個影格（move forward by one frame）**。 | 極為強大的精密除錯工具，讓初學者能逐幀觀察角色位移、動畫過渡或物理運動的微妙變化。 |

---

## 知識點 3：輔助測試與介面管理工具

- **【官方來源】**：The Toolbar
- **【原始網址】**：`https://docs.unity.com/en-us/engine/6000.0/manual/unity-editor/editor-navigating-managing/toolbar`
- **【段落章節】**：Property 表格
- **【適用版本】**：Unity 6.0 (6000.0)

工具列同時整合了提升開發效率的常用輔助功能：
* **Layout（版面配置）**：切換檢視視窗的排列佈局，可將自訂的工作區版面儲存起來，或切換回原廠預設佈局。
* **Undo History（復原歷史紀錄）**：檢視、復原（Undo）或重做（Redo）在編輯器中所執行的各項編輯動作，避免誤刪物件。
* **Global Search（全域搜尋）**：在專案資產與場景中快速搜尋特定名稱的 GameObject 或資源。

---

## 知識缺口與初學者簡化說明

- **除錯工具簡化**：本篇官方文件聚焦於 Toolbar 工具列介面與 Play / Pause / Step 的控制功能。進階的 Console（控制台報錯視窗）與程式碼中斷點除錯（Debugger）不在此篇範疇內，後續教學簡報將重點引導初學者學會「利用 Play 進入測試、利用 Pause/Step 凍結與逐幀觀察」的測試觀念。
