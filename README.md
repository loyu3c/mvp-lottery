# MVP 抽獎機

礁溪老爺酒店年度運動會 MVP 抽獎系統，運動風格主題，透過 Firebase Realtime Database
讓「後台輸入頁面（手機）」與「大螢幕頁面」即時同步。

## 上線網址

- 首頁：<https://mvp-draw.zeabur.app/>
- 大螢幕（投影用）：<https://mvp-draw.zeabur.app/screen.html>
- 後台（手機用）：<https://mvp-draw.zeabur.app/admin.html>

## 檔案結構

- `index.html` — 首頁，導向大螢幕頁與後台頁
- `screen.html` — 大螢幕投影頁，播放老虎機抽獎動畫
- `admin.html` — 手機後台頁，輸入四項冠軍名單、上傳照片並觸發開獎

## 部署前必做：設定 Firebase

> 目前這個 repo 的 `screen.html` / `admin.html` 已經填好 Firebase 設定並連上線上資料庫，
> 以下步驟是給之後想重新部署一份（例如換一個活動）的人參考。

1. 到 [Firebase Console](https://console.firebase.google.com) 建立新專案（免費 Spark 方案）
2. 左側選單「Build → Realtime Database」→ 建立資料庫 → 選離台灣近的地區 → 先選「測試模式」
3. 左側「專案設定」→「一般」→ 新增網頁應用程式（`</>`）→ 複製出現的 `firebaseConfig`
4. 把這組設定貼到 `screen.html` 和 `admin.html` 兩個檔案裡的 `FIREBASE_CONFIG`
   （**兩邊必須完全一樣**，才能連到同一個資料庫）

> ⚠️ 測試模式的資料庫規則 30 天後會自動關閉讀寫權限，正式使用前記得到
> Realtime Database → 規則，改成長期允許讀寫。

## 部署到 Zeabur

1. 在 Zeabur 建立新專案 → 選擇「GitHub」服務類型 → 連接這個 repo
2. 因為專案內沒有特定語言（純 HTML），Zeabur 會自動以靜態網頁模式部署
3. 部署完成後會有三個網址，格式如上方「上線網址」

## 使用方式

1. 大螢幕開啟 `screen.html`，先點右上角「🔈 開啟音效」解鎖音效（瀏覽器限制需手動點一次），
   有需要投影可以再點「⛶ 全螢幕」
2. 手機開啟 `admin.html`，輸入四項競賽的項目名稱、冠軍姓名，並可上傳冠軍照片
   （沒上傳的話大螢幕會顯示預設頭像圖示）
3. 可先按「📤 同步名單到大螢幕」讓大螢幕提前顯示候選人名單和照片，不會觸發抽獎動畫
4. 準備好後按「🎲 開始抽獎」，大螢幕會先倒數 3-2-1，接著播放老虎機抽獎動畫並停在隨機抽出的 MVP
