# YouTube 監控器
這是一個使用 Flask 框架開發的 Python 應用程式，設計用於監控 YouTube 活動。它使用 Google 的 OAuth 2.0 進行身份驗證，並與 Firebase 進行資料存取。

## 功能
- Google OAuth 2.0 整合：應用程式使用 Google 的 OAuth 2.0 協議進行身份驗證，允許用戶使用他們的 Google 帳戶登入。
- Firebase 整合：應用程式使用 Firebase Admin SDK for Python 與 Firebase 進行互動，Firebase 是 Google 的行動和網頁應用程式開發平台。它使用 Firebase 進行資料儲存和檢索。
- 環境變數支援：當不在生產環境中運行時，應用程式使用 dotenv 套件從 `.env` 文件中加載環境變數。這允許將敏感信息（如 API 密鑰和資料庫憑證）安全地並與程式碼分開儲存。

## 設定

- 環境變數：如果您不在生產環境中運行應用程式，請在項目的根目錄中創建一個 `.env` 文件，並在其中添加您的環境變數。應用程式將在啟動時載入這些變數。
- Youtube密鑰文件：應用程式需要一個 Google 的 OAuth 2.0 協議的客戶端密鑰文件。該文件應命名為 `client_secret.json`，並放置在項目的根目錄中。您可以從 Google Cloud Console 獲取此文件。
- Firebase：應用程式使用 Firebase 的 Realtime Database 劑型儲存。您需要設置一個 Firebase 項目，並將必要的網址添加到您的環境變數或您的 .env 文件中。

## 取得 Google OAuth 2.0 `client_secret.json` 步驟

1. 首先，您需要訪問 [Google Cloud Console](https://console.cloud.google.com/)。
2. 如果您還沒有創建項目，請創建一個。在項目創建後，請確保您已選擇該項目。
3. 在左側導航欄中，點擊 "APIs & Services"，然後選擇 "Credentials"。
4. 在 "Credentials" 頁面上，點擊 "Create Credentials"，然後選擇 "OAuth client ID"。
5. 如果您還未配置 "OAuth consent screen"，系統將提示您配置。在 "OAuth consent screen" 中，至少需要填寫 "App name" 和 "User support email"，然後保存並繼續。
6. 在 "Create OAuth client ID" 頁面，選擇 "Web application"。在 "Authorized redirect URIs" 欄位中，輸入您的應用程式的重定向 URI。如果您正在本地開發，可能會是 `http://localhost:5000/` 或者是您的 Flask 應用程式的某個路由。
7. 點擊 "Create"。您的客戶端 ID 和客戶端密鑰將會顯示在彈出的窗口中。
8. 在彈出的窗口中，點擊 "Download JSON"，將會下載一個名為 `client_secret.json` 的文件。
9. 將下載的 `client_secret.json` 文件放到您的項目根目錄中。

完成以上步驟後，您的應用程式應該可以使用 Google OAuth 2.0 進行身份驗證了。

## 執行程式

### 建立虛擬環境

```
python -m venv venv
```
### 載入 Python 虛擬環境

```
source venv/bin/activate
```

### 安裝套件

```
pip install -r requirements.txt
```

### 執行 Python 檔案

```
python main.py
```
