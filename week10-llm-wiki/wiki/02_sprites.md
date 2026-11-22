# Wiki: 02. 2D 圖像與角色（Sprite Renderer）

本篇整理自 Unity 6.0 官方文件，旨在為完全沒有 Unity 經驗的初學者解說 2D 遊戲中最關鍵的視覺渲染組件：Sprite Renderer，以及如何透過圖層排序解決 2D 物件遮擋問題。

---

## 知識點 1：什麼是 Sprite Renderer 組件？

- **【官方來源】**：Sprite Renderer component reference
- **【原始網址】**：`https://docs.unity.com/en-us/engine/6000.0/manual/unity2d/sprite/sprite-renderer-reference`
- **【段落章節】**：Sprite Renderer component reference
- **【適用版本】**：Unity 6.0 (6000.0)

### 核心觀念
1. **2D 渲染核心**：在 Unity 2D 遊戲中，如果想讓一個 GameObject 顯示出 2D 圖片（Sprite），就必須在該物件上掛載 **`Sprite Renderer`** 組件。
2. **與 Transform 的協同運作**：Sprite Renderer 會讀取 GameObject 上 Transform 組件的座標、旋轉與縮放，並將指定的圖片精靈精確繪製在畫面對應位置上。

---

## 知識點 2：Sprite Renderer 的核心屬性

- **【官方來源】**：Sprite Renderer component reference
- **【原始網址】**：`https://docs.unity.com/en-us/engine/6000.0/manual/unity2d/sprite/sprite-renderer-reference`
- **【段落章節】**：Property 表格與 Draw Mode properties
- **【適用版本】**：Unity 6.0 (6000.0)

初學者在 Unity 檢查器（Inspector）中經常調整的基礎屬性如下：

| 屬性名稱（Property） | 功能說明（Description） | 初學者實務操作觀念 |
| :--- | :--- | :--- |
| **Sprite** | 設定 Unity 要在畫面中渲染的 2D 精靈資產。 | 可從專案視窗（Project window）將圖片直接拖曳進來，或點擊圓圈選取器（⊙）選取。 |
| **Color** | 為 Sprite 疊加調色濾鏡。 | 預設為純白色（代表原圖無染色）；若改成紅色或調整透明度 Alpha，角色外觀就會即時變色或變半透明。 |
| **Flip** | 沿著 X 軸（水平）或 Y 軸（垂直）鏡射翻轉貼圖。 | **重要特性**：勾選 Flip 只會單純翻轉外觀貼圖，**完全不會移動或改變 GameObject 本身的實際座標與 Transform**。常直觀用於角色轉身向左/向右。 |
| **Draw Mode** | 決定 Sprite 貼圖的縮放方式。 | • **Simple**（預設）：整張圖片均勻拉伸縮放。<br>• **Sliced**：9-slicing（九宮格）模式，拉伸中心但保持四角不變形。<br>• **Tiled**：平鋪重複模式，像鋪磁磚一樣平鋪貼圖。 |
| **Material** | 設定渲染該 Sprite 所使用的材質。 | Unity 6 預設材質為 `Sprite-Lit-Default`，能自動對應 2D 光照。 |

---

## 知識點 3：2D 圖層排序關鍵（Sorting Layer 與 Order in Layer）

- **【官方來源】**：Sprite Renderer component reference
- **【原始網址】**：`https://docs.unity.com/en-us/engine/6000.0/manual/unity2d/sprite/sprite-renderer-reference`
- **【段落章節】**：Additional Settings
- **【適用版本】**：Unity 6.0 (6000.0)

在 2D 遊戲中，因為所有物體都在同一個平面上，物體之間「誰在前、誰在後」由圖層排序屬性決定：

1. **Sorting Layer（排序圖層）**：
   - 決定物件屬於哪一個大圖層類別（例如自訂的 Background 背景層、Characters 角色層、Foreground 前景層）。
   - Unity 會嚴格依照 Tags and Layers 視窗中的圖層清單順序進行由底至頂的繪製。
2. **Order in Layer（圖層內部順序）**：
   - 當兩個 Sprite 處於**同一個 Sorting Layer** 時，由 `Order in Layer` 的整數數值決定遮擋關係。
   - **核心渲染規則**：**Unity 會先渲染數值較小的物件，再渲染數值較大的物件**。
   - 因此：**數值越大（Higher values），會顯示在最前方並遮擋住數值較小的物體**。

---

## 知識缺口與初學者簡化說明

- **高階功能簡化**：本篇暫不深入 `Rendering Layer Mask`（進階 URP 光照遮罩）與複雜的 `Mask Interaction`（剪裁遮罩），初學者只需掌握 `Sprite` 指定、`Flip` 水平翻轉、以及利用 `Sorting Layer` 與 `Order in Layer` 解決前後遮擋問題即可。
