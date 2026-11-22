# Wiki: 01. Unity 基本概念（Game objects）

本篇整理自 Unity 6.0 官方文件，旨在為完全沒有 Unity 經驗的初學者建立最核心的心智模型：認識遊戲物件（GameObject）與組件（Component）的容器關係。

---

## 知識點 1：什麼是 GameObject（遊戲物件）？

- **【官方來源】**：Game objects
- **【原始網址】**：`https://docs.unity.com/en-us/engine/6000.0/manual/working-with-gameobjects/game-objects`
- **【段落章節】**：Introduction to GameObjects
- **【適用版本】**：Unity 6.0 (6000.0)

### 核心觀念
1. **最重要的基礎概念**：在 Unity 編輯器中，**GameObject** 是最核心的概念。遊戲中的所有實體——從玩家角色、可收集道具、背景樹木，到看不見的燈光（Light）、攝影機（Camera）與音效來源（Audio Source），全體都是 GameObject。
2. **容器特性（Container）**：GameObject 本身**無法單獨發揮任何具體功能**。單純的一個空 GameObject 就只是一個「空容器」，你必須為它添加各種**組件（Components）**來賦予它外觀、行為或物理特性，它才能真正成為一個角色、環境障礙或特殊效果。

---

## 知識點 2：Component（組件）如何賦予物件功能？

- **【官方來源】**：Game objects
- **【原始網址】**：`https://docs.unity.com/en-us/engine/6000.0/manual/working-with-gameobjects/game-objects`
- **【段落章節】**：Introduction to GameObjects
- **【適用版本】**：Unity 6.0 (6000.0)

### 核心觀念
1. **組件的職責**：組件（Component）是真正實作遊戲功能與外觀的核心單位。想要讓 GameObject 變成什麼，就替它掛載對應的組件組合。
2. **官方範例說明**：
   - 一個**燈光物件（Light GameObject）**：是藉由在 GameObject 上掛載 `Light` 組件來實現照亮場景。
   - 一個**實心方塊物件（Cube GameObject）**：結合了 `Mesh Filter` 與 `Mesh Renderer` 組件來繪製方塊表面，並掛載 `Box Collider` 組件來具備物理實體體積。
3. **擴充方式**：Unity 內建了大量現成的組件，開發者也可以透過自訂 C# 腳本（Scripting API）製作專屬的組件。

---

## 知識點 3：不可移除的核心組件——Transform

- **【官方來源】**：Game objects
- **【原始網址】**：`https://docs.unity.com/en-us/engine/6000.0/manual/working-with-gameobjects/game-objects`
- **【段落章節】**：Details
- **【適用版本】**：Unity 6.0 (6000.0)

### 核心觀念
1. **唯一不可移除**：任何一個 GameObject 建立時，**必定會自動掛載一個 `Transform` 組件，且無法被刪除**。
2. **Transform 的功能**：用來記錄該遊戲物件在空間中的**位置（Position）**、**旋轉角度（Rotation）**與**縮放比例（Scale）**。
3. **組件操作管道**：除了 Transform 之外的其他功能組件，都可以透過 Unity 編輯器的 **Component 選單** 或 **自訂腳本** 來隨時新增或移除。

---

## 知識缺口與初學者簡化說明

- **Scene（場景）概念邊界**：本篇官方文件聚焦於 GameObject 作為 Component 容器的概念。在 Unity 中，Scene 即是承載這群 GameObject 共同運作的「關卡舞台與世界」。後續簡報將以此概念為基準，不深入複雜的跨場景非同步加載（`SceneManager`）。
