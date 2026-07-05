#  智能點餐系統智慧點餐系統 

這是一個結合了 C++ 後端高效運算 與 現代化網頁 UI 的智慧點餐解決方案。本系統旨在解決傳統餐飲業流程破碎、結帳效率低落的問題，透過前後端分離架構，實現即時購物車同步與自動化收據處理。

＃＃  專案亮點 

    高效能後端邏輯： 採用 C++17 與物件導向設計，核心運算精準且快速。

    即時 Web 互動： 整合 cpp-httplib 實現 API 服務化，前端透過 Fetch API 與後端進行非同步資料交換，實現購物車即時更新。

    自動化結帳流程： 軟硬體整合接口，結帳後自動將詳細訂單輸出至 Linux 系統終端機，實現自動化管理。

    前後端分離架構： UI 與商務邏輯解耦，具備極高的擴充彈性，易於未來升級為手機 App 或整合進雲端系統。

＃＃  系統架構

    Backend: C++17, cpp-httplib (HTTP API)

    Frontend: HTML5, Bootstrap 5, JavaScript (Fetch API)

    Environment: Ubuntu Linux

＃＃ 快速開始 

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


---
## 挑戰與克服 
1. 前後端通訊架構的落差

    困難： 傳統 C++ 程式與 Web 瀏覽器對於資料的認知方式完全不同。C++ 依賴記憶體指標與物件參照，而網頁依賴 JSON 文字格式。

    解決方式： 實作了一套「序列化橋接機制」。在 OrderSystem 中手動編寫 JSON 格式轉換函式，成功將後端複雜的物件指標資料，轉換為輕量級的 JSON 字串發送至前端，解決了資料跨系統傳輸的相容性問題。

2. 非同步狀態同步的挑戰

    困難： 網頁點餐按鈕與後端記憶體狀態不一致。使用者點餐後，網頁不會自動刷新，導致購物車顯示滯後。

    解決方式： 導入了 JavaScript 的 Fetch API 配合強制快取更新機制」。透過在 API 請求中加入時間戳記 ，確保每次點餐請求都能獲取最新的 C++ 後端狀態，達成零延遲的即時體驗。
3. C++ 連結錯誤與模組化管理

    困難： 隨著系統規模擴大，類別間的相依性導致編譯連結時出現 undefined reference 錯誤，這反映了對專案目錄結構與編譯器路徑的掌握度不足。

    解決方式： 重新優化專案目錄架構，將原始碼統一管理於 scr 目錄，並改寫編譯參數（使用 -I. 指定路徑與 -std=c++17 標準）。這不僅解決了連結錯誤，更建立了一套規範化的編譯流程，顯著提升了開發維護的效率

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

---
## 專題開發心得：從終端機走向網路服務的技術蛻變
1. 對於物件導向設計的重新認識

過去寫程式時，物件導向對我來說只是一種語法規則；但在本次開發中，我真正體會到了模組化的力量。當我將 OrderSystem、Menu、Order 與 OrderItem 拆解獨立後，我發現原本以為很複雜的購物車即時運算，其實只要調用各個物件的介面就能完成。這種將複雜問題拆解為單純物件互動的思維，是我在本次專題中最深刻的技術成長。
2. 技術突破：打破 C++ 的邊界

開發過程中最大的困難，在於如何讓純 C++ 語言與網路協定對接。起初，我對於如何處理 HTTP 請求感到迷茫，但透過 cpp-httplib 這一類輕量級網路庫的應用，我理解了：無論什麼語言，核心都是資料的流動。只要理解了 HTTP 的 Request 與 Response 模型，無論是 C++、Python 還是 Node.js，本質邏輯皆是互通的。這份專題讓我學會了如何讓 C++ 這個傳統的高效語言，也能擁有現代化服務的靈魂。


   
