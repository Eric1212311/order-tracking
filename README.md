# 订单追踪系统 - GitHub Pages 部署

网页版订单追踪系统，前端部署在 GitHub Pages，数据存储在 Google Sheets。

## 架构

```
浏览器 → GitHub Pages (index.html) → Apps Script API → Google Sheets
```

## 部署步骤

### 1. 部署 Apps Script 后端

1. 在 Google Sheets 中打开 `Order_Tracking_Template.xlsx`
2. 扩展程序 → Apps Script
3. 删除默认代码，粘贴项目根目录的 `AppsScript_API.js` 全部内容
4. 保存 (Ctrl+S)
5. 点击右上角「部署」→「新部署」
6. 类型选择「Web 应用」
7. 执行身份：我
8. 访问权限：**任何人**
9. 点击「部署」→ 复制生成的 URL

### 2. 配置前端

编辑 `index.html`，将第 `API_URL` 替换为你的 Apps Script URL：

```javascript
const API_URL = 'https://script.google.com/macros/s/XXXXX/exec';
```

### 3. 部署到 GitHub Pages

```bash
# 在项目根目录
cd github-pages
git init
git add .
git commit -m "订单追踪系统"
git branch -M main
git remote add origin https://github.com/你的用户名/order-tracking.git
git push -u origin main
```

然后在 GitHub 仓库设置中启用 Pages：
- Settings → Pages → Source: Deploy from a branch → main → /(root) → Save

### 4. 访问

几分钟后 GitHub Pages URL 即可用：`https://你的用户名.github.io/order-tracking/`

## 功能

- 📊 看板：五态实时汇总
- 📋 订单管理：未排产 → 已排产 → 已发货 → 已完成
- ⏰ 临期订单：自动识别 7 天内交期
- 👥 客户列表
- 📦 SKU 管理
- ✅ 确认弹窗防误操作
- 🔄 数据与 Google Sheets 实时同步

## 同时使用

- 网页版：GitHub Pages URL（外网可访问）
- 表格版：Google Sheets（可以直接编辑）
- 两边数据实时同步
