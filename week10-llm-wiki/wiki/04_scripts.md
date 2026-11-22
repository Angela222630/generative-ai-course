# Wiki: 04. C# 腳本基礎（Creating scripts）

本篇整理自 Unity 6.0 官方文件，旨在為完全沒有程式經驗的大學初學者建立 C# 腳本與 Unity 遊戲物件的核心心智模型：腳本如何作為自訂組件（Custom Components）來控制 GameObject 的行為。

---

## 知識點 1：什麼是腳本？腳本如何控制 GameObject？

- **【官方來源】**：Creating scripts
- **【原始網址】**：`https://docs.unity.com/en-us/engine/6000.0/manual/scripting/get-started/creating-scripts`
- **【段落章節】**：Creating scripts
- **【適用版本】**：Unity 6.0 (6000.0)

### 核心觀念
1. **擴充遊戲功能**：腳本（Scripts）允許開發者透過編寫 **C# 程式碼**，自訂並擴充遊戲應用程式的功能。
2. **腳本即自訂組件（核心觀念）**：
   - 繼承自 Unity 內建 **`MonoBehaviour`** 類別的腳本，本質上就是開發者打造的**自訂組件（Custom Components）**。
   - 將這些腳本組件掛載至 GameObject 上，即可用來**控制該遊戲物件的具體行為**。
3. **其他官方提及之腳本類型**：
   - 繼承自 `ScriptableObject`：用於在專案中高效儲存大量共用資料。
   - 空白 C# 類別：用於開發不依附於 Unity 生命週期的獨立類別。

---

## 知識點 2：如何在 Unity 編輯器中建立新腳本？

- **【官方來源】**：Creating scripts
- **【原始網址】**：`https://docs.unity.com/en-us/engine/6000.0/manual/scripting/get-started/creating-scripts`
- **【段落章節】**：Creating scripts
- **【適用版本】**：Unity 6.0 (6000.0)

與大部分需要外部匯入的遊戲素材不同，腳本通常直接在 Unity 內部建立。建立管道有兩種：

1. **透過主選單建立**：
   - 點擊頂部主選單：**Assets > Create > Scripting**，選擇所欲建立的腳本類型。
2. **透過專案視窗建立（Project Window）**：
   - 在專案視窗工具列點擊 **Create 選單（加號標誌 +）**：選擇 **Scripting** 並選取腳本類型。
3. **命名注意事項**：
   - 腳本建立後會立刻位於當前 Project 面板選取的資料夾中，系統會自動選取檔案名稱供開發者重新命名。在 Unity 中，腳本檔名與內部的類別名稱保持一致是良好的實務原則。

---

## 知識缺口與初學者簡化說明

- **輸入與位移 API 缺口**：本篇官方文件核心聚焦於「C# 腳本繼承 `MonoBehaviour` 以作為自訂組件控制物件」與「腳本建立步驟」。文中並未涵蓋鍵盤輸入（如 `Input` API）或座標位移（如 `Translate`）。
- **簡化方案**：在教學簡報中，角色行為將聚焦於「撰寫腳本組件賦予物件邏輯」的心智模型，角色移動的原理以「程式在每幀中更新物體座標概念」進行概念性說明，不外插捏造未有來源的具體輸入函式；狗狗移動 Demo 則以網頁前端模擬呈現。
