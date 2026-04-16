# DISC 性格测试系统

面试者远程 DISC 性格测试系统。面试官发送测试链接给候选人，候选人在手机/电脑上填写 40 题 DISC 测试，提交后面试官可在管理后台实时查看所有候选人的测试结果。

## 技术栈

- **前端**：React 18 + TypeScript + Vite 5 + Tailwind CSS 3
- **后端**：Supabase (PostgreSQL + Realtime)
- **部署**：Vercel

## 快速开始

### 1. 配置 Supabase

1. 注册 [Supabase](https://supabase.com/) 并创建项目
2. 进入项目 Dashboard → **SQL Editor**，执行 `supabase/schema.sql` 中的 SQL 脚本
3. 在 Dashboard → **Settings → API** 中获取 `Project URL` 和 `anon public key`

### 2. 配置环境变量

```bash
cp .env.example .env
```

编辑 `.env` 文件，填入 Supabase 配置：

```
VITE_SUPABASE_URL=https://your-project.supabase.co
VITE_SUPABASE_ANON_KEY=your-anon-key
```

### 3. 安装依赖并启动

```bash
npm install
npm run dev
```

### 4. 访问

- **候选人测试页**：`http://localhost:5173/`
- **面试官管理后台**：`http://localhost:5173/admin`

## 页面说明

### 候选人测试页 (`/`)

1. 欢迎页面 → 阅读答题须知
2. 填写姓名
3. 开始答题（40 题，10 分钟限时）
4. 提交后查看 DISC 得分结果
5. 进入 5 分钟冷却期（防刷）

### 管理后台 (`/admin`)

- 查看所有候选人提交记录
- 按姓名搜索筛选
- 点击查看详细得分分析
- Realtime 实时推送新提交

## 部署

本项目部署在 [Vercel](https://vercel.com/)。

### 手动构建

```bash
npm run build
```

产物位于 `dist/` 目录。

### Vercel 部署步骤

1. 在 [Vercel](https://vercel.com/) 导入本项目的 Git 仓库
2. Framework Preset 选择 **Vite**
3. 在 **Settings → Environment Variables** 中配置以下环境变量：
   - `VITE_SUPABASE_URL`：Supabase 项目 URL
   - `VITE_SUPABASE_ANON_KEY`：Supabase anon public key
4. 部署完成后，后续每次推送到主分支将自动触发部署

> **注意**：由于项目使用了客户端路由，Vercel 会自动处理 SPA 的路由回退，无需额外配置。
