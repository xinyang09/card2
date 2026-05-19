
兑换前端（Vue 3 + Element Plus + Vite）。

[API对接文档](API文档-api.node-card.com.md)
## 特性

- 单个兑换、批量兑换、消费记录查询、只查询不兑换
- 前端默认请求本站 `/api`，真实 API 地址由本地开发代理或 Nginx 代理转发。
- 对接需要提供域名白名单，添加跨域访问白名单后才能直接调用。
- 公告内容从 `public/notice.txt` 读取，修改该文件后刷新页面即可更新。
## 开发

```bash
npm install
npm run dev
```

本地开发时，`/api` 默认代理到 `https://api.node-card.com`。如需修改代理目标：

```bash
API_PROXY_TARGET=https://api.node-card.com npm run dev
```

## 打包

```bash
npm run build
```

产物目录：`dist/`

## Docker Compose 部署

公告内容从 `public/notice.txt` 读取，部署前直接修改该文件即可。

```bash
docker compose up -d --build
```

默认映射端口为 `8080`，访问：

```bash
http://localhost:8080
```

如需修改端口或 API 地址：

```bash
APP_PORT=3000 API_PROXY_TARGET=https://api.node-card.com docker compose up -d --build
```

## 接口配置

浏览器只会请求当前站点下的 `/api/...`，真实 API 地址不会写进前端打包文件。

默认代理目标：

```env
API_PROXY_TARGET=https://api.node-card.com
```

如需改为其他域名，部署时设置 `API_PROXY_TARGET` 即可。
