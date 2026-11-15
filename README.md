# webone-server

待办清单的后端接口。前端在 <https://github.com/Ink-saber/webone>（部署在 GitHub Pages）。

## 技术栈

- Node.js + Express
- 存储：JSON 文件（`store.js`），不依赖任何原生模块或数据库服务

## 接口

| 方法 | 路径 | 作用 |
| --- | --- | --- |
| GET | `/api/items` | 查列表（可选 `?done=true/false`、`?q=关键字`） |
| GET | `/api/items/:id` | 查一条 |
| POST | `/api/items` | 新增（body: `title` 必填，`note`、`done` 可选） |
| PUT | `/api/items/:id` | 修改 |
| DELETE | `/api/items/:id` | 删除 |
| GET | `/` | 自检 |

返回格式统一为 `{ code, data, msg }`，`code` 为 `0` 表示成功。
已开启跨域（CORS），响应头为 `Access-Control-Allow-Origin: *`。

## 本地运行

```bash
npm install
npm start
```

默认监听 `4000` 端口，可用环境变量 `PORT` 覆盖。
首次启动会自动写入 7 条初始数据。

## 环境变量

| 变量 | 说明 |
| --- | --- |
| `PORT` | 监听端口，平台通常会自动注入 |
| `DB_PATH` | 数据文件路径，默认 `data.json`；目录不可写时自动降级为内存模式 |

## 部署

- 平台：Railway
- 构建：`npm install`
- 启动：`npm start`
- 根目录：仓库根目录（本仓库只含后端，不含静态页面）

`railway.json` 已固定构建方式与启动命令。
