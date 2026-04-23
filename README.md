# Built4AI

> 项目管理中枢 - 组织、规范、协调所有 Built4* 产品线

## 项目定位

Built4AI 是一个**项目管理中枢**，而非代码仓库。各产品以独立repo形式存在：
- **开源基础设施**：独立公开repo，建立独立社区
- **商业产品**：独立私有repo，集成基础设施

## 产品线规划

| 产品 | 类型 | Repo | 技术栈 | 状态 |
|------|------|------|--------|------|
| Built4rag | 开源基础设施 | `built4rag` (public) | Python + FastAPI | Planning |
| Built4skill | 开源社区 | `built4skill` (public) | TypeScript | Planning |
| Built4design | 商业产品 | 私有repo | TBD | Planning |
| ... | ... | ... | ... | ... |

## 目录结构

```
Built4AI/                       # 项目管理中枢（本repo）
├── README.md                   # 项目概述
├── roadmap/                    # 产品roadmap和规划
│   ├── built4rag.md            # Built4rag的roadmap
│   ├── built4skill.md          # Built4skill的roadmap
│   └── decisions.md            # 技术决策日志
├── specs/                      # 跨项目规范
│   ├── architecture.md         # 架构设计原则
│   ├── api-conventions.md      # API设计规范
│   ├── docker-integration.md   # Docker集成标准
│   └── security.md             # 安全标准
├── templates/                  # 项目模板
│   ├── python-fastapi/         # Python项目模板
│   ├── typescript-node/        # TypeScript项目模板
│   ├── devcontainer/           # DevContainer配置模板
│   └── github-workflows/       # CI/CD workflow模板
├── scripts/                    # 管理脚本
│   ├── create-product.sh       # 创建新产品repo
│   ├── sync-templates.sh       # 同步模板到各项目
│   └── update-remotes.sh       # 更新git remotes
└── projects/                   # 本地开发工作区（git clone目标）
    ├── built4rag/              # git clone的本地副本
    ├── built4skill/            # git clone的本地副本
    └── ...                     # 其他产品
```

## 开发环境管理

### 原则
每个产品repo**独立管理自己的开发环境**，Built4AI提供统一模板和规范。

### Python产品（Built4rag等）
- 使用 **uv** 管理（你已确定）
- 模板路径：`templates/python-fastapi/`

### TypeScript产品（Built4skill等）
- 使用 **pnpm** + **turbo**（如果需要monorepo）
- 或 **pnpm** 单包
- 模板路径：`templates/typescript-node/`

### Go产品
- 使用 **go modules** 标准
- 模板路径：`templates/go/`（待创建）

### DevContainer统一开发环境
- 提供统一的DevContainer配置模板
- 各产品继承或自定义
- 模板路径：`templates/devcontainer/`

## Git策略

### Repo公开/私有策略

| Repo类型 | 公开/私有 | 原因 |
|----------|-----------|------|
| Built4AI | **Public** | 项目中枢，公开roadmap吸引关注 |
| Built4rag | **Public** | 开源基础设施，建立社区 |
| Built4skill | **Public** | 开源社区，吸引贡献 |
| 商业产品 | **Private** | 商业代码，保护IP |

### Git Remotes管理
```bash
# 在Built4AI中管理所有产品remotes
git remote add built4rag https://github.com/archywu/built4rag
git remote add built4skill https://github.com/archywu/built4skill

# 批量操作
scripts/update-remotes.sh  # 同步所有remotes
```

## License策略

### 开源产品（Built4rag, Built4skill）
推荐使用 **Apache 2.0**：
- 允许商业使用（你的商业产品可以自由集成）
- 保护专利权
- 要求保留版权声明
- 要求说明代码修改部分

### 商业产品
私有repo，无需开源license。商业license由单独的EULA定义。

### Built4AI（项目管理中枢）
使用 **CC BY 4.0**：
- 文档和规范性质，适合CC license
- 允许自由分享和改编
- 要求署名

## 工作流程

### 创建新产品
```bash
# 1. 使用模板创建repo
./scripts/create-product.sh built4rag python-fastapi

# 2. 在GitHub创建对应repo（public/private）

# 3. 初始化开发
cd projects/built4rag
uv init  # Python项目
pnpm init  # TypeScript项目
```

### 开发流程
1. 在 `projects/<product>/` 中开发（独立repo）
2. Roadmap更新在 `roadmap/<product>.md`
3. 跨项目决策记录在 `roadmap/decisions.md`

## 参考案例

类似的项目管理中枢案例：
- [sindresorhus/awesome](https://github.com/sindresorhus/awesome) - 列表式管理
- [facebook/create-react-app](https://github.com/facebook/create-react-app) - 模板分发
- [vercel/next.js](https://github.com/vercel/next.js) - 框架 + 示例组织

## 下一步行动

1. 创建 `roadmap/` 目录，规划首个产品 Built4rag
2. 创建 `templates/python-fastapi/`，基于 uv 的项目模板
3. 创建 GitHub repo `built4rag`（public）
4. 在 `projects/built4rag/` clone 并开始开发