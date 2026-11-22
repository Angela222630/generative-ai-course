# 簡報大綱與頁面規劃：從零開始的 Unity 2D 遊戲開發

本規劃依據 `AGENTS.md` 規範與 `wiki/` 知識庫（全 6 章）設計，全篇採用**繁體中文**，保留 Unity 英文專有名詞。

---

## 一、 簡報基本資訊與教學設計

* **目標讀者**：完全沒有 Unity 與程式開發經驗的大學初學者。
* **教學主題**：認識 Unity 2D 遊戲的基本製作流程與核心心智模型。
* **情境範例（貫穿全篇）**：**「製作一個簡單的雪地狗狗場景（Snow Dog Scene）」**。從零開始帶領初學者建立舞台、放入狗狗角色、鋪設雪地、賦予腳本與物理特性，最後完成測試。
* **簡報規格**：單一獨立 HTML 檔案（約 10 頁），內建上一頁/下一頁切換、知識小測驗與純前端視覺模擬 Demo。
* **唯一知識來源（Strict Grounding）**：全書內容 100% 映射自 `wiki/01_basics.md` 至 `wiki/06_playmode.md`，無任何未獲來源支持的外插知識。

---

## 二、 10 頁簡報逐頁結構規劃

### 第 1 頁：封面與學習導覽（Welcome to Unity 2D）
* **頁面標題**：從零開始的 Unity 2D：認識遊戲製作流程
* **教學目標**：了解 2D 遊戲製作的核心步驟，建立「雪地狗狗場景」的實作情境。
* **主要內容**：
  * 歡迎來到 Unity 2D 開發世界！
  * 情境任務：我們將帶領大家在 Unity 中打造一個小巧的「雪地狗狗場景」。
  * 學習地圖：從遊戲物件（GameObject）開始，認識組件（Component）、貼圖渲染（Sprite Renderer）、地圖（Tilemap）、程式邏輯（Script）、物理剛體（Rigidbody 2D）到最後的運行測試（Play Mode）。
* **呈現方式**：簡潔具設計感的主視覺封面、情境簡介卡片、學習路徑導覽圖。
* **對應 Wiki 來源**：
  * [wiki/INDEX.md](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/INDEX.md)
  * [wiki/01_basics.md (知識點 1)](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/01_basics.md#L9-L23)

---

### 第 2 頁：遊戲世界的基石——GameObject（遊戲物件）
* **頁面標題**：萬物的容器：什麼是 GameObject？
* **教學目標**：建立「遊戲內的一切實體皆是 GameObject 空容器」的核心心智模型。
* **主要內容**：
  * 在 Unity 編輯器中，**GameObject** 是最核心的概念。
  * 在我們的雪地場景中，玩家操作的狗狗小花、場景裡的雪松樹、可收集的骨頭、照亮雪地的燈光、乃至於攝影機（Camera），全部都是 GameObject。
  * **容器特性**：GameObject 本身無法單獨發揮具體功能，它是一個空容器，必須藉由裝入「組件（Components）」才能具備外觀與能力。
* **呈現方式**：比喻圖解（空盒子 ➔ 裝入不同配件變成不同物品）、雪地物件清單對比。
* **對應 Wiki 來源**：
  * [wiki/01_basics.md (知識點 1)](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/01_basics.md#L9-L23)

---

### 第 3 頁：功能的賦予者——Component 與必備的 Transform
* **頁面標題**：賦予物件靈魂：Component 與唯一必備的 Transform
* **教學目標**：理解組件組合模式（Composition），以及 Transform 在空間中的絕對地位。
* **主要內容**：
  * **Component（組件）**：是真正實作遊戲功能與外觀的核心單位。想要讓物件具備什麼功能，就替它掛載對應的組件。
  * 官方範例：燈光物件是掛載 `Light` 組件；實心方塊是組合 `Mesh Filter`、`Mesh Renderer` 與 `Box Collider`。
  * **唯一不可移除的組件——Transform**：任何 GameObject 建立時必定自帶 `Transform` 組件且無法刪除，負責記錄空間中的：
    1. **Position（位置）**
    2. **Rotation（旋轉）**
    3. **Scale（縮放）**
* **呈現方式**：Inspector 檢查器面板結構圖、Transform 座標三要素解析卡。
* **對應 Wiki 來源**：
  * [wiki/01_basics.md (知識點 2, 3)](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/01_basics.md#L25-L53)

---

### 第 4 頁：讓角色現身——Sprite Renderer（2D 圖像渲染）
* **頁面標題**：看見狗狗：Sprite Renderer 組件與外觀控制
* **教學目標**：掌握 2D 圖片如何繪製在畫面上，以及初學者常用的外觀調節屬性。
* **主要內容**：
  * **Sprite Renderer**：讓 GameObject 顯示出 2D 圖片（Sprite）的核心渲染組件。它會讀取 Transform 座標，把貼圖正確畫在畫面上。
  * 初學者必學核心屬性：
    * **Sprite**：指定圖片資產（將雪地狗狗圖片拖入）。
    * **Color**：疊加調色濾鏡（純白代表原色，可調節色彩或透明度）。
    * **Flip（鏡射翻轉）**：沿 X 軸（水平）或 Y 軸（垂直）翻轉外觀。**關鍵觀念：只翻轉外觀貼圖，完全不改變 GameObject 本身的 Transform 實際座標**（非常適合製作狗狗轉身向左/向右）。
    * **Draw Mode**：Simple（等比縮放）、Sliced（九宮格拉伸）、Tiled（平鋪）。
* **呈現方式**：Inspector 屬性對照表、狗狗 Flip X 翻轉效果圖解。
* **對應 Wiki 來源**：
  * [wiki/02_sprites.md (知識點 1, 2)](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/02_sprites.md#L9-L42)

---

### 第 5 頁：誰站在前面？——2D 圖層遮擋排序
* **頁面標題**：前後分明：Sorting Layer 與 Order in Layer
* **教學目標**：解決 2D 遊戲最常見的「物體被地圖吃掉或穿透遮擋」問題。
* **主要內容**：
  * 2D 遊戲所有物體都在同一平面，如何確保狗狗站在雪地草叢前面，而不是被埋在草底下？
  * **Sorting Layer（排序圖層）**：定義大層級繪製優先權（如 Background 背景層、Characters 角色層、Foreground 前景層）。
  * **Order in Layer（圖層內部順序）**：在同一個 Sorting Layer 內部的子層級整數數值。
  * **核心繪製法則**：**Unity 永遠先渲染數值較小者，再渲染數值較大者**。
  * 結論：**數值越大（Higher values），會顯示在最前方並遮擋住數值較小的物體**！
* **呈現方式**：分層三明治立體透視圖示、Order in Layer 數值大小對比示意。
* **對應 Wiki 來源**：
  * [wiki/02_sprites.md (知識點 3)](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/02_sprites.md#L44-L63)

---

### 第 6 頁：鋪設雪地世界——Tilemap（瓦片地圖）
* **頁面標題**：像畫畫一樣鋪設關卡：認識 Tilemap 與 Tile Palette
* **教學目標**：了解如何利用瓦片地圖系統快速構建 2D 關卡與地形障礙。
* **主要內容**：
  * **什麼是 Tilemap？**：透過在場景畫布上「繪製瓦片（Painting Tiles）」來快速拼湊雪地平原、冰湖與岩石障礙。
  * **瓦片作畫兩大步驟**：
    1. **建立 Tile Palette（瓦片調色盤）**：收藏作畫所用的瓦片資產（Tile assets，官方定義為矩形、等角或六邊形的 Sprite）。
    2. **建立 Tilemap 網格畫布**：在場景中用筆刷將調色盤上的雪地磚刷到 Tilemap 上。
  * **三種佈局類型（Types of tilemap）**：
    * **Rectangular（矩形）**：系統預設值，適合最經典的 2D 橫向捲軸與俯視角雪地地圖。
    * **Hexagonal（六邊形）**：蜂巢狀，常見於戰棋策略。
    * **Isometric（等角投影）**：2.5D 斜角透視，營造立體深度錯覺。
* **呈現方式**：調色盤 ➔ 筆刷 ➔ 地圖網格之工作流程圖解、三種佈局外觀範例。
* **對應 Wiki 來源**：
  * [wiki/03_tilemaps.md (知識點 1, 2, 3)](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/03_tilemaps.md#L9-L49)

---

### 第 7 頁：賦予行為邏輯——C# 腳本即自訂組件
* **頁面標題**：撰寫程式行為：C# 腳本與 MonoBehaviour
* **教學目標**：認識 C# 腳本在 Unity 中的本質，建立「腳本就是自訂組件」的概念。
* **主要內容**：
  * 有了外觀和地圖，狗狗如何具備自主行為？需要撰寫 C# 腳本！
  * **腳本即自訂組件（核心觀念）**：繼承自 Unity 內建 **`MonoBehaviour`** 類別的腳本，本質上就是開發者打造的「自訂組件（Custom Components）」。
  * 只要把寫好的腳本掛載到狗狗 GameObject 上，就能在裡面撰寫邏輯控制狗狗的動作。
  * **建立腳本管道**：主選單 `Assets > Create > Scripting` 或專案視窗工具列 `+ > Scripting`。
  * 命名小叮嚀：建立時需立即確認檔名，確保與檔案內部類別名稱一致。
* **呈現方式**：GameObject 掛載自訂 C# 腳本卡片、編輯器建立腳本步驟說明。
* **對應 Wiki 來源**：
  * [wiki/04_scripts.md (知識點 1, 2)](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/04_scripts.md#L9-L40)

---

### 第 8 頁：【前端概念模擬】狗狗位置座標變化示範
* **頁面標題**：觀察座標改變：狗狗位置移動的純前端視覺互動模擬
* **教學目標**：透過網頁模擬，觀察位置座標改變時，狗狗在畫面中的位置如何改變，建立「角色在畫面中的呈現由 Transform 座標決定」之心智模型。
* **主要內容**：
  * 在遊戲運行時，角色的視覺位置由 Transform 的 Position 座標決定。
  * **【純前端網頁視覺互動模擬】**：
    * 提供一個雪地畫布框，初學者可點擊畫面四向按鈕或使用鍵盤 **W / A / S / D** 控制畫面中的可愛小狗位置，觀察其在畫布中的座標平移。
    * 即時在畫布旁顯示模擬的 `Position (X, Y)` 數值變化。
  * **重要免責聲明**：*「本模擬僅供體會位置座標變化之概念，由 HTML/CSS/JavaScript 實作，非 Unity 引擎實際角色移動之實作方式與程式碼。」*
  * **操作防衝突與鍵盤分離設計**：
    * 狗狗移動**嚴格限定使用 W、A、S、D 鍵或畫面按鈕**，上下方向鍵不再控制狗狗。
    * **左右方向鍵（← / →）在包含第 8 頁在內的全 10 頁中均維持正常切換投影片功能**，徹底杜絕操作衝突。
* **呈現方式**：互動式迷你畫布（Mini Canvas / Mock UI）、座標即時顯示面板、顯著的網頁模擬標籤。
* **對應 Wiki 來源**：
  * [wiki/04_scripts.md (知識缺口與初學者簡化說明)](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/04_scripts.md#L42-L46)
  * [wiki/01_basics.md (知識點 3 Transform Position)](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/01_basics.md#L39-L53)

---

### 第 9 頁：感受自然定律——Rigidbody 2D（2D 物理與剛體）
* **頁面標題**：重力與物理規律：認識 Rigidbody 2D 組件
* **教學目標**：了解如何利用 2D 物理引擎讓物件具備重力下墜與質量等物理行為。
* **主要內容**：
  * 狗狗站在雪坡上，如何讓它像真實物體一樣受重力影響？掛載 **`Rigidbody 2D`** 組件！
  * **啟用物理行為**：讓 GameObject 在 2D 物理引擎的控制下行動。
  * **四大物理特性**：
    1. **Gravity（重力）**：自然往下掉落。
    2. **Mass（質量）**：物體本身的質量數值。
    3. **Drag（阻力）**：運動時的空氣阻力。
    4. **Momentum（動量）**：運動衝量與慣性。
  * **Body Type（剛體類型）**：決定物件在物理世界中的行為模式（如動態下墜或固定不動）。
  * **Simulated 屬性**：整個 2D 物理模擬的開關（Start / Stop），控制物件是否參與物理計算。
* **呈現方式**：物理受力示意圖、Simulated 開關切換圖解。
* **對應 Wiki 來源**：
  * [wiki/05_physics.md (知識點 1, 2, 3)](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/05_physics.md#L9-L50)

---

### 第 10 頁：即時驗收成果——The Toolbar 與 Play Mode 測試除錯
* **頁面標題**：測試你的雪地世界：Toolbar 工具列與 Play Mode
* **教學目標**：學會使用 Unity 最重要的頂部工具列進行即時運行測試與單幀除錯。
* **主要內容**：
  * 雪地場景佈置完畢、組件掛載齊全後，如何驗證遊戲好不好玩？使用頂部的 **The Toolbar（工具列）**！
  * **Toolbar 特性**：位於編輯器頂端，唯一固定不能重新排列的控制列。
  * **Play Mode Controls（運行核心三按鈕）**：
    * **Play（播放）**：切換至 **Game view（遊戲視窗）**，即時運行並測試遊戲真實效果。
    * **Pause（暫停）**：當狗狗發生異常時隨時凍結畫面，方便在場景中檢查物件數值。
    * **Step（單幀步進）**：暫停時點擊，讓遊戲「向前推進恰好一個影格（move forward by one frame）」，精密觀察每一幀的物理與位移變化。
  * **成果驗收折疊區塊**：頁面下方設有「開始小測驗」按鈕，點擊後展開 3 題單選小測驗，避免畫面過度擁擠。
* **呈現方式**：Toolbar 按鈕視覺模擬、Play/Pause/Step 三步驟測試流程圖、可折疊展開的測驗互動面板。
* **對應 Wiki 來源**：
  * [wiki/06_playmode.md (知識點 1, 2)](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/06_playmode.md#L9-L44)

---

## 三、 知識小測驗規劃（點擊「開始小測驗」後展開）

為驗收初學者的吸收成效，設計 3 題單選小測驗，**所有題目與答案均 100% 來自 Wiki**：

### 題目 1（基本概念與 Transform）
* **題目**：在 Unity 中，當你建立任何一個新的 GameObject 時，哪一個組件是必定會自動掛載且**無法被刪除**的？
  * (A) Sprite Renderer
  * (B) Transform（正確）
  * (C) Rigidbody 2D
  * (D) Tilemap
* **正解解析**：`Transform` 組件用來記錄物件的位置（Position）、旋轉（Rotation）與縮放（Scale），是唯一不可移除的核心組件。
* **對應 Wiki 依據**：[wiki/01_basics.md 知識點 3](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/01_basics.md#L39-L44)。

---

### 題目 2（2D 視覺與圖層遮擋）
* **題目**：在同一 Sorting Layer（排序圖層）、兩個 Sprite 重疊時，如果雪地地面的 Order in Layer 設定為 0，而狗狗的 Order in Layer 設定為 2，兩者的前後顯示關係為何？
  * (A) 雪地地面會遮擋住狗狗
  * (B) 狗狗會顯示在雪地地面最前方，遮擋住雪地（正確）
  * (C) 兩者數值不同所以無法同時顯示
  * (D) 數值越小的物體永遠顯示在最前方
* **正解解析**：在同一 Sorting Layer 且物件重疊時，Unity 圖層渲染規則是「先渲染數值較小者，再渲染數值較大者」，因此數值越大（Higher values）會顯示在最前方並遮擋數值較小者。
* **對應 Wiki 依據**：[wiki/02_sprites.md 知識點 3](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/02_sprites.md#L44-L63)。

---

### 題目 3（測試除錯與 The Toolbar）
* **題目**：在 Unity 頂部工具列中，當遊戲處於暫停（Pause）狀態時，點擊「Step」按鈕具體有什麼效果？
  * (A) 重新開始遊戲
  * (B) 自動儲存當前場景
  * (C) 使遊戲向前推進恰好一個影格（move forward by one frame）（正確）
  * (D) 退出 Play Mode 運行模式
* **正解解析**：Step 按鈕的作用是單幀步進，可在暫停期間使遊戲前進恰好一個影格，是精密除錯的絕佳工具。
* **對應 Wiki 依據**：[wiki/06_playmode.md 知識點 2](file:///c:/Users/loves/OneDrive/桌面/AI/unity-2d-llm-wiki/wiki/06_playmode.md#L27-L44)。
