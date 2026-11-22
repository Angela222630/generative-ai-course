# Wiki: 03. 場景與地圖（Tilemaps）

本篇整理自 Unity 6.0 官方文件，旨在為完全沒有 Unity 經驗的初學者解說 2D 關卡建置的核心心智模型：如何利用 Tilemap（瓦片地圖）像畫畫一樣快速繪製 2D 遊戲世界與環境地圖。

---

## 知識點 1：什麼是 Tilemap（瓦片地圖）？

- **【官方來源】**：Tilemaps
- **【原始網址】**：`https://docs.unity.com/en-us/engine/6000.0/manual/unity2d/tilemaps/tilemaps`
- **【段落章節】**：Introduction to tilemaps
- **【適用版本】**：Unity 6.0 (6000.0)

### 核心觀念
1. **地圖繪製概念**：在 2D 專案中，**Tilemap** 讓開發者能夠透過「將瓦片（Tiles）繪製（Painting）到場景上」的方式，直觀且快速地建立遊戲世界與關卡地形（例如草地、道路、牆壁障礙）。
2. **套件先決條件**：專案中需安裝 `2D Tilemap Editor` 套件（Unity 2D 專案預設已內建）即可直接使用。
3. **渲染管線支援**：Tilemap 支援所有具備 2D 功能的渲染管線。

---

## 知識點 2：瓦片繪製的兩個核心步驟（Tile Palette 與 Tilemap）

- **【官方來源】**：Tilemaps
- **【原始網址】**：`https://docs.unity.com/en-us/engine/6000.0/manual/unity2d/tilemaps/tilemaps`
- **【段落章節】**：Introduction to tilemaps
- **【適用版本】**：Unity 6.0 (6000.0)

要使用瓦片在場景中作畫，主要遵循兩大步驟：

1. **建立瓦片調色盤（Create a Tile Palette）**：
   - **Tile Palette** 就像畫家的「調色盤」，它是你作畫所使用之瓦片資產（Tile assets）的集合清單。
   - 依據官方文件，瓦片資產（Tile assets）即為矩形（rectangular）、等角（isometric）或六邊形（hexagonal）的精靈（Sprites）。
2. **建立瓦片地圖並開始繪製（Create a Tilemap & Paint）**：
   - **Tilemap** 是你作畫的「畫布區域」（鋪設在 Grid 網格上）。
   - 建立 Tilemap 後，選取調色盤上的瓦片，即可使用筆刷工具直接在場景中點擊繪製出關卡地面與地貌。

---

## 知識點 3：常見的 Tilemap 網格佈局類型（Types of tilemap）

- **【官方來源】**：Tilemaps
- **【原始網址】**：`https://docs.unity.com/en-us/engine/6000.0/manual/unity2d/tilemaps/tilemaps`
- **【段落章節】**：Types of tilemap
- **【適用版本】**：Unity 6.0 (6000.0)

Unity 官方支援以下三種主要的瓦片網格排列方式：

| 佈局類型（Layout Type） | 官方特色與應用場合 | 初學者理解 |
| :--- | :--- | :--- |
| **Rectangular（矩形 / 正方形）** | **系統預設值（Default）**。最常見的四邊形格線。 | 適合絕大多數 2D 平台跳躍遊戲、橫向捲軸或經典 RPG（如寶可夢風格地圖）。 |
| **Hexagonal（六邊形 / 蜂巢狀）** | 瓦片為六角形，可排列為頂部尖角（Point top）或頂部平邊（Flat top）。 | 常見於戰棋、策略回合制地圖（如文明帝國系列）。 |
| **Isometric（等角投影 / 2.5D）** | 利用 2D 斜角網格創造出具備 3D 高度與深度的立體視覺錯覺。 | 常用於斜視角模擬經營、農場模擬或 2.5D RPG。 |

---

## 知識缺口與初學者簡化說明

- **地圖系統簡化**：本篇官方文件聚焦於 Tilemap 的整體建置概念（Tile Palette、繪製流程與網格類型）。針對進階的自動鋪路規則（Rule Tiles）、程式動態刷地圖或瓦片碰撞設定，本教學予以簡化，初學者只需建立「調色盤選瓦片、在 Tilemap 上刷出地圖」之心智模型即可。
