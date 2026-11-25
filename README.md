# Resource Forum Admin · B 端内容社区治理中后台

> **在线体验（Live Demo）**：👉 [https://kellanzhuo.github.io/resource-forum-admin/](https://kellanzhuo.github.io/resource-forum-admin/)  
> 演示账号已预填：`admin` / `password`（纯前端 Mock 持久化模式，所有审核、上下架、分类校验与配置修改刷新后均保存在浏览器 `localStorage`，可直接交互体验）

## 项目定位与我的分工

本项目提取自北京理工大学计算机工程实践团队项目（[resource-sharing-forum](https://github.com/resource-sharing-team/resource-sharing-forum)）中的**管理端前端工程**，定位为面向内容分享社区的 **B 端内容治理、风控审核与参数配置中后台**。

- **个人职责**：负责管理端 **6 大核心模块的交互设计、业务防呆规则落地、前端工程实现及接口联调**（基于 React + TypeScript + Vite）。

---

## 核心功能模块（6 大业务闭环）

| 模块 | 核心治理能力 | 产品与防呆亮点 |
|---|---|---|
| **内容综合管理** | 资源审核、上下架管理、求资源帖治理、评论管控（4 维切换） | 列表一键通过；**驳回强制填写原因**并即时同步状态，降低误操作成本 |
| **用户账号管理** | 管理员查询、用户启用/禁用管控 | 账号状态即时联动后台权限校验与通知闭环 |
| **举报与版权投诉** | 违规举报处理、版权侵权下架、用户申诉复核 | 结构化合规处置流程，覆盖审核→下架→申诉完整链路 |
| **分类与标签体系** | 固定两级分类维护、规范词库标签增删/禁用/合并/一键补齐 | **同级分类防重名**、禁用一级分类前**校验启用子分类**；标签受控防碎片化 |
| **系统参数配置** | 会员等级权益、积分与悬赏风控规则、配置保存与缓存刷新 | 将核心增长与风控杠杆产品化配置，支持热更新 |
| **操作审计日志** | 全量关键管理动作记录与分页检索 | 保障 B 端敏感操作全链路可追溯 |

---

## 工程架构亮点

- **权限拦截与状态安全**：登录仅放行 `ADMIN` 角色；Axios 响应拦截器捕获 `401` 自动清空本地鉴权态并跳转 `/login`，彻底避免半登录脏状态。
- **双模式联调架构**：默认对接后端 `/api/admin/**` REST 接口；设置 `VITE_ENABLE_MOCKS=true` 即可一键切换至内置 Mock + `localStorage` 持久化演示模式，支持前后端并行开发与零后端在线演示。
- **统一分页与自动化验证**：全站 5 大列表页复用统一后端分页协议，配套 **Vitest + Testing Library** 单元测试与 **GitHub Actions** CI/CD 自动构建部署。

---

## 技术栈

`React 19` · `TypeScript` · `Vite` · `React Router` · `Ant Design` · `TanStack Query` · `Zustand` · `Axios` · `Vitest`

---

## 本地运行与验证

```bash
npm install

# 本地零后端演示模式（Mock + localStorage 持久化）
VITE_ENABLE_MOCKS=true npm run dev

# 运行单元测试 & 生产构建
npm run test
npm run build
```
