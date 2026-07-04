# 🍔 智能點餐系統智慧點餐系統 

這是一個結合了 C++ 後端高效運算 與 現代化網頁 UI 的智慧點餐解決方案。本系統旨在解決傳統餐飲業流程破碎、結帳效率低落的問題，透過前後端分離架構，實現即時購物車同步與自動化收據處理。
🚀 專案亮點 (Key Features)

    高效能後端邏輯： 採用 C++17 與物件導向設計，核心運算精準且快速。

    即時 Web 互動： 整合 cpp-httplib 實現 API 服務化，前端透過 Fetch API 與後端進行非同步資料交換，實現購物車即時更新。

    自動化結帳流程： 軟硬體整合接口，結帳後自動將詳細訂單輸出至 Linux 系統終端機，實現自動化管理。

    前後端分離架構： UI 與商務邏輯解耦，具備極高的擴充彈性，易於未來升級為手機 App 或整合進雲端系統。

🏗️ 系統架構 (System Architecture)

    Backend: C++17, cpp-httplib (HTTP API)

    Frontend: HTML5, Bootstrap 5, JavaScript (Fetch API)

    Environment: Ubuntu Linux

🛠️ 快速開始 (Quick Start)

請確保您的電腦已安裝 g++ 編譯器與必要的開發環境。
1. git colon
Bash

git clone https://github.com/your-username/order-food.git
cd order-food/scr

2. 編譯與執行
Bash

# 編譯程式碼
g++ main.cpp OrderSystem.cpp Menu.cpp MenuItem.cpp Order.cpp OrdeItem.cpp -o main -std=c++17 -pthread

# 啟動伺服器
./main

3. 存取系統

開啟瀏覽器並輸入：http://localhost:8080
📊 核心物件模型 (UML Structure)
<img width="1035" height="489" alt="圖片" src="https://github.com/user-attachments/assets/28d19cf8-4946-498c-a231-4f27c557b6a6" />


本系統基於物件導向設計，核心類別包含：

    OrderSystem: 系統總控制台，負責處理網路請求與調度訂單。

    Order: 管理購物車邏輯與加總運算。

    Menu: 提供動態菜單數據接口。



   #執行結果
   ---------------------------------------------------------------------------------------------------------
   1.顯示點餐名稱與價錢
   <img width="973" height="457" alt="圖片" src="https://github.com/user-attachments/assets/021d431b-89e9-4507-8dd7-dcb09fa9130d" />

   2.點選項要的項目系統將會計算好價錢
   <img width="973" height="457" alt="圖片" src="https://github.com/user-attachments/assets/f663485a-6dde-49df-a757-029e9b7f907b" />

   3.終端機會同步紀錄系統上的點餐明細
   <img width="1054" height="613" alt="圖片" src="https://github.com/user-attachments/assets/980d693b-dfec-4174-8d4f-fc253fae1e32" />

   4.按下結帳按鈕並在終端機可確認相對應明細按下0後輸出結帳成功
   <img width="990" height="554" alt="圖片" src="https://github.com/user-attachments/assets/f229a908-2d9a-43cf-8681-62d4318dc4b2" />




   
