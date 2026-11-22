# Unity 2D 教學簡報製作流程（Graph／Loop）

本文件提供專案工作流程之可編輯 Mermaid 原始碼，採直式簡潔架構設計，清楚呈現 Node 0～7 之推進順序、Node 3 與 Node 6 菱形判斷、失敗返回迴圈（Loop）與人機協同標示。

---

## 一、 Mermaid 流程圖原始碼（簡潔版）

```mermaid
flowchart TD
    %% 樣式類別定義 (淺藍、深藍、白、金)
    classDef mainNode fill:#16223f,stroke:#38bdf8,stroke-width:2.5px,color:#ffffff,font-size:16px;
    classDef checkNode fill:#0e3254,stroke:#60a5fa,stroke-width:2.5px,color:#ffffff,font-size:16px;
    classDef hitlBadge fill:#312005,stroke:#f59e0b,stroke-width:1.8px,color:#fef08a,font-size:13px;

    %% 節點定義 (直式核心流程)
    N0["Node 0：規格制定"]:::mainNode
    N1["Node 1：官方資料擷取"]:::mainNode
    N2["Node 2：知識庫建立"]:::mainNode
    N3{"Node 3：Wiki 檢查"}:::checkNode
    N4["Node 4：簡報大綱規劃"]:::mainNode
    H1["人工確認大綱"]:::hitlBadge
    N5["Node 5：HTML 簡報生成"]:::mainNode
    N6{"Node 6：HTML 測試"}:::checkNode
    H2["第 8 頁操作曾經人工調整"]:::hitlBadge
    N7["Node 7：反思報告與交付"]:::mainNode

    %% 直式主要推進
    N0 --> N1
    N1 --> N2
    N2 --> N3

    %% Node 3 判定與 Loop
    N3 -- "PASS（通過）" --> N4
    N3 -- "PASS（下一批，共3批）" --> N1
    N3 -. "FAIL（資料不全，重擷取）" .-> N1
    N3 -. "FAIL（Wiki錯誤，重整理）" .-> N2

    %% 大綱至生成
    N4 --> H1
    H1 --> N5
    N5 --> N6

    %% Node 6 判定與 Loop
    N6 -- "PASS（通過）" --> H2
    N6 -. "FAIL（測試失敗，重生成）" .-> N5

    %% 交付
    H2 --> N7

    %% 邊線樣式
    linkStyle 0,1,2,6,7,8,11 stroke:#38bdf8,stroke-width:2.2px;
    linkStyle 3,9 stroke:#34d399,stroke-width:2.5px;
    linkStyle 4 stroke:#38bdf8,stroke-width:2px;
    linkStyle 5,10 stroke:#f87171,stroke-width:2.2px,stroke-dasharray: 4 4;
```

---

## 二、 流程設計與圖面重點說明

1. **核心流程清晰直觀**：
   * 採用直式向下推進，各節點僅保留核心繁體中文功能名稱（Node 0～7）。
   * 老師在 10 秒內即可掌握從官方資料 Ingest、提煉 Wiki，到大綱審查、HTML 簡報生成、測試與最終交付的完整生命週期。
2. **菱形檢驗與 Loop 閉環**：
   * 僅在 **Node 3（Wiki 檢查）** 與 **Node 6（HTML 測試）** 設置菱形判斷框。
   * 檢查失敗時以**紅色虛線箭頭**清楚指向退回節點（Node 3 失敗退回 Node 1 或 Node 2；Node 6 失敗退回 Node 5），展現嚴謹的自我修正迴圈。
3. **人機協同（HITL）簡單標示**：
   * 階段間的人工介入以精巧的琥珀金色標籤嵌入流程線中（「人工確認大綱」與「第 8 頁操作曾經人工調整」），不干擾主流程視覺。
4. **真實執行紀錄標記**：
   * 圖片下方註明：「**本次自動重試 0 次；第 8 頁操作方式曾經人工調整。**」，如實反映實務執行成果。
