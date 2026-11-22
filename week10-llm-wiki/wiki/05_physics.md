# Wiki: 05. 2D 物理與剛體（Rigidbody 2D）

本篇整理自 Unity 6.0 官方文件，旨在為完全沒有 Unity 經驗的初學者建立 2D 物理系統的基本概念：認識 Rigidbody 2D 如何讓遊戲物件受物理引擎與重力控制。

---

## 知識點 1：什麼是 Rigidbody 2D（2D 剛體）？

- **【官方來源】**：Rigidbody 2D
- **【原始網址】**：`https://docs.unity.com/en-us/engine/6000.0/manual/unity2d/2d-physics/rigidbody-2d`
- **【段落章節】**：Introduction to Rigidbody 2D
- **【適用版本】**：Unity 6.0 (6000.0)

### 核心觀念
1. **啟用物理行為**：**Rigidbody 2D** 是一個 2D 組件，只要在 GameObject 上掛載它，就能讓該物件「在 2D 物理引擎的控制下行動（act under the control of physics）」。
2. **基本物理反應**：掛載 Rigidbody 2D 後，物件將具備現實世界中的基本物理反應，包含：
   - **重力反應（Gravity）**：物體會自然受重力影響而往下墜落。
   - **質量（Mass）**：物體本身的質量數值。
   - **阻力（Drag）**：移動時受到的空氣阻力。
   - **動量（Momentum）**：物體運動時具備的慣性與衝量。
3. **與 Collider 2D 的協同關係**：在 2D 物理模擬中，Rigidbody 2D 是產生動態運動的核心，並能與 Collider 2D（碰撞組件）相互搭配進行互動。

---

## 知識點 2：Body Type（剛體類型）與物理行為定義

- **【官方來源】**：Rigidbody 2D
- **【原始網址】**：`https://docs.unity.com/en-us/engine/6000.0/manual/unity2d/2d-physics/rigidbody-2d`
- **【段落章節】**：Rigidbody 2D body types
- **【適用版本】**：Unity 6.0 (6000.0)

### 核心觀念
1. **行為模式選擇**：開發者透過設定 Rigidbody 2D 上的 **Body Type** 屬性，來決定該物件在物理世界中表現出何種行為特徵。
2. **初學者理解定位**：
   - 不同的遊戲角色與障礙物需要不同的物理特性（例如有些角色完全受重力牽引、有些平台固定在空中不動、有些則由程式純運動學控制）。透過選擇正確的 Body Type，便能精確控制該物件是否會下墜或被撞飛。

---

## 知識點 3：Simulated 屬性（物理模擬開關）

- **【官方來源】**：Rigidbody 2D
- **【原始網址】**：`https://docs.unity.com/en-us/engine/6000.0/manual/unity2d/2d-physics/rigidbody-2d`
- **【段落章節】**：Rigidbody 2D Simulated property
- **【適用版本】**：Unity 6.0 (6000.0)

### 核心觀念
1. **模擬控制開關**：Rigidbody 2D 提供了 **`Simulated`** 屬性。
2. **主要功能**：開發者可以利用此屬性來**啟動（Start）或停止（Stop）**該 Rigidbody 2D 以及其底下附帶的 Collider 2Ds / Joint 2Ds 參與整個 2D 物理模擬計算。
3. **實務應用情境**：當遊戲暫停、物體被凍結、或暫時不希望物體參與物理碰撞計算時，可將其關閉以節省運算資源或維持特定遊戲狀態。

---

## 知識缺口與初學者簡化說明

- **物理與碰撞簡化**：本篇官方文件聚焦於 Rigidbody 2D 的功能、物理控制要素（重力、質量、阻力、動量）、Body Type 概念與 Simulated 開關。
- **邊界守則**：本篇不深入進階物理數學公式（向量動量、扭矩計算），亦不擅自擴充未列於本篇的具體 Collider 形狀參數（如 BoxCollider2D/CircleCollider2D 半徑）或 Trigger 程式事件（`OnTriggerEnter2D`），讓初學者專注掌握「剛體賦予物體重力與物理運動能力」的核心心智模型。
