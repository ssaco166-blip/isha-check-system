# IshaCheck Public Release (Backend Only)

此資料夾為可公開上傳版本（後端-only），已移除執行紀錄資料與示範截圖，可用於 GitHub 分享。

## 1) 最小運行需求

- Python 3.11+（建議 3.12）
- Windows 10/11 或 Linux
- 可連外網路（僅安裝套件時需要）

## 2) 安裝與啟動

1. 建立虛擬環境
   - Windows: `python -m venv .venv && .\.venv\Scripts\activate`
   - Linux: `python3 -m venv .venv && source .venv/bin/activate`
2. 安裝套件
   - `pip install -r software/requirements.txt`
3. 啟動服務
   - Windows: `python software/start.py`
   - Linux: `python3 software/start.py`
4. 開啟登入頁
   - `http://127.0.0.1:5000/login`

## 3) 初始登入帳號（測試用）

- Username: `admin`
- Password: `admin123`

安全提醒：正式上線後請立即變更密碼，不要長期使用預設帳密。

## 4) 首次啟動行為

- 首次啟動會自動建立空白運行資料（例如 `database.db`、`logs` 目錄）。
- 這些資料屬於執行期檔案，不應提交到 GitHub。

## 5) 自動化 Smoke Test（至少驗證可登入）

- 執行：`python software/scripts/smoke_login.py`
- 驗證內容：
  - 服務可啟動
  - `/login` 可連線
  - 使用 `admin/admin123` 登入成功

若失敗，腳本會回傳明確分類：
- `STARTUP_FAILURE`：服務啟動失敗
- `CONNECTION_FAILURE`：無法連線到登入頁
- `LOGIN_FAILURE`：帳密登入未成功
