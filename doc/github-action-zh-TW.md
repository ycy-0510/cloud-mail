## Github Action 部署

**設定 Github 儲存庫**

1. Fork 或 Clone 儲存庫 [https://github.com/eoao/cloud-mail](https://github.com/eoao/cloud-mail)
2. 進入您的 GitHub 儲存庫設定
3. 前往 Settings → Secrets and variables → Actions → New Repository secrets
4. 新增以下 Secrets：

| Secret 名稱             | 必填 | 用途                                                  |
| ----------------------- | :--: | ----------------------------------------------------- |
| `CLOUDFLARE_API_TOKEN`  |  ✅  | Cloudflare API 權杖（需要 Workers 與相關資源權限）    |
| `CLOUDFLARE_ACCOUNT_ID` |  ✅  | Cloudflare 帳戶 ID                                    |
| `D1_DATABASE_ID`        |  ✅  | 您的 D1 資料庫的 ID                                     |
| `KV_NAMESPACE_ID`       |  ✅  | 您的 KV 命名空間的 ID                                   |
| `R2_BUCKET_NAME`        |  ✅  | 您的 R2 儲存桶的名稱                                    |
| `DOMAIN`                |  ✅  | 您要用於郵件服務的網域（例如 `["xx.xx"]，多個網域以,分隔`）        |
| `ADMIN`                 |  ✅  | 您的管理員信箱位址（例如 `admin@example.com`）      |
| `JWT_SECRET`            |  ✅  | 用於產生與驗證 JWT 的隨機長字串                     |
| `INIT_URL`              |  ❌  | （選填）部署後用於初始化資料庫的 Worker URL（格式參考下述手動初始化）           |

---

**取得 Cloudflare API 權杖**

1. 前往 [Cloudflare Dashboard](https://dash.cloudflare.com/profile/api-tokens)
2. 建立新的 API 權杖
3. 選擇「編輯 Cloudflare Workers」範本，並參照下表新增相應權限
   ![dc2e1dc8dcd217644759c46c6c705de1](https://i.miji.bid/2025/07/07/dc2e1dc8dcd217644759c46c6c705de1.png)
4. 儲存權杖並複製到 GitHub Secrets 中的 `CLOUDFLARE_API_TOKEN`

**取得 Cloudflare 帳戶 ID**
1. 帳戶 ID 可以在 Cloudflare 儀表板的帳戶設定中找到。
2. 複製到 GitHub Secrets 中的 `CLOUDFLARE_ACCOUNT_ID`

**執行工作流程**
1. 接著在 Actions 頁面手動執行工作流程，後續同步上游後便會自動部署到 Cloudflare Workers。若未設定 `INIT_URL`，則需要手動造訪 `https://你的專案網域/api/init/你的jwt_secret` 進行資料庫初始化。
2. 自動同步上游可使用 bot 或手動點擊 Sync Upstream 按鈕。
