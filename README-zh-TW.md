<p align="center">
    <img src="doc/demo/logo.png" width="80px" />
    <h1 align="center">Cloud Mail</h1>
    <p align="center">基於 Cloudflare 的簡約響應式信箱服務，支援郵件寄送、附件收發 🎉</p> 
    <p align="center">
        <a href="/README.md" style="margin-left: 5px">简体中文</a> | 繁體中文 | <a href="/README-en.md" style="margin-left: 5px">English </a>
    </p>
    <p align="center">
        <a href="https://github.com/maillab/cloud-mail/tree/main?tab=MIT-1-ov-file" target="_blank" >
            <img src="https://img.shields.io/badge/license-MIT-green" />
        </a>    
        <a href="https://github.com/maillab/cloud-mail/releases" target="_blank" >
            <img src="https://img.shields.io/github/v/release/maillab/cloud-mail" alt="releases" />
        </a>  
        <a href="https://github.com/maillab/cloud-mail/issues" >
            <img src="https://img.shields.io/github/issues/maillab/cloud-mail" alt="issues" />
        </a>  
        <a href="https://github.com/maillab/cloud-mail/stargazers" target="_blank">
            <img src="https://img.shields.io/github/stars/maillab/cloud-mail" alt="stargazers" />
        </a>  
        <a href="https://github.com/maillab/cloud-mail/forks" target="_blank" >
            <img src="https://img.shields.io/github/forks/maillab/cloud-mail" alt="forks" />
        </a>
    </p>
    <p align="center">
        <a href="https://trendshift.io/repositories/20459" target="_blank" >
            <img src="https://trendshift.io/api/badge/repositories/20459" alt="trendshift" >
        </a>
    </p>
</p>


## 專案簡介

只需要一個網域，就可以建立多個不同的信箱，類似各大信箱平台，本專案支援部署到 Cloudflare Workers，降低伺服器成本，打造屬於自己的信箱服務

## 專案展示

- [線上展示](https://skymail.ink)<br>
- [部署文件](https://doc.skymail.ink)<br>

| ![](/doc/demo/demo1.png) | ![](/doc/demo/demo2.png) |
|-----------------------|-----------------------|
| ![](/doc/demo/demo3.png) | ![](/doc/demo/demo4.png) |




## 功能介紹

- **💰 低成本使用**：可部署到 Cloudflare Workers，降低伺服器成本

- **💻 響應式設計**：響應式版面自動適配 PC 與大部分手機端瀏覽器

- **📧 郵件寄送**：整合 Resend 寄送郵件，支援群發、內嵌圖片與附件寄送、寄送狀態查看

- **🛡️ 管理員功能**：可對使用者、郵件進行管理，透過 RBAC 權限控制功能與使用資源限制

- **📦 附件收發**：支援收發附件，使用 R2 物件儲存來保存與下載檔案

- **🔔 郵件推播**：接收郵件後可轉寄到 Telegram 機器人或其他服務商信箱

- **📡 開放 API**：支援使用 API 批次建立使用者、多條件查詢郵件

- **🔢 驗證碼辨識**：使用 Workers AI，自動辨識郵件驗證碼

- **📈 資料視覺化**：使用 ECharts 將系統資料詳情、使用者郵件成長視覺化呈現

- **🎨 個人化設定**：可自訂網站標題、登入背景、透明度

- **🤖 人機驗證**：整合 Turnstile 人機驗證，防止機器人批次註冊

- **📜 更多功能**：持續開發中⋯⋯



## 技術棧

- **平台**：[Cloudflare Workers](https://developers.cloudflare.com/workers/)

- **Web 框架**：[Hono](https://hono.dev/)

- **ORM：**[Drizzle](https://orm.drizzle.team/)

- **前端框架**：[Vue3](https://vuejs.org/) 

- **UI 框架**：[Element Plus](https://element-plus.org/) 

- **郵件推播：** [Resend](https://resend.com/)

- **快取**：[Cloudflare KV](https://developers.cloudflare.com/kv/)

- **資料庫**：[Cloudflare D1](https://developers.cloudflare.com/d1/)

- **檔案儲存**：[Cloudflare R2](https://developers.cloudflare.com/r2/)

## 目錄結構

```
cloud-mail
├── mail-worker				    # worker 後端專案
│   ├── src                  
│   │   ├── api	 			    # api 介面層			
│   │   ├── const  			    # 專案常數
│   │   ├── dao                 # 資料存取層
│   │   ├── email			    # 郵件處理接收
│   │   ├── entity			    # 資料庫實體
│   │   ├── error			    # 自訂例外
│   │   ├── hono			    # web 框架設定、攔截器、全域例外等
│   │   ├── i18n			    # 語言國際化
│   │   ├── init			    # 資料庫快取初始化
│   │   ├── model			    # 回應體資料封裝
│   │   ├── security			# 身分權限驗證
│   │   ├── service			    # 業務服務層
│   │   ├── template			# 訊息範本
│   │   ├── utils			    # 工具類
│   │   └── index.js			# 進入點檔案
│   ├── pageckge.json			# 專案相依套件
│   └── wrangler.toml			# 專案設定
│
├── mail-vue				    # vue 前端專案
│   ├── src
│   │   ├── axios 			    # axios 設定
│   │   ├── components			# 自訂元件
│   │   ├── echarts			    # echarts 元件匯入
│   │   ├── i18n			    # 語言國際化
│   │   ├── init			    # 進站初始化
│   │   ├── layout			    # 主體版面元件
│   │   ├── perm			    # 權限驗證
│   │   ├── request			    # api 介面
│   │   ├── router			    # 路由設定
│   │   ├── store			    # 全域狀態管理
│   │   ├── utils			    # 工具類
│   │   ├── views			    # 頁面元件
│   │   ├── app.vue			    # 進入點元件
│   │   ├── main.js			    # 進入點 js
│   │   └── style.css			# 全域 css
│   ├── package.json			# 專案相依套件
└── └── env.release				# 專案設定
```

## 贊助

<a href="https://doc.skymail.ink/support.html" >
<img width="170px" src="./doc/images/support.png" alt="">
</a>

## 授權條款

本專案採用 [MIT](LICENSE) 授權條款	


## 交流

[Telegram](https://t.me/cloud_mail_tg)
