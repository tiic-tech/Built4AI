# 技术决策日志

> 记录Built4*产品线的重要技术决策

---

## 2026-04-23: 项目架构选择 Polyrepo

### 背景
- 规划开发多个Agent相关产品
- 产品分为开源基础设施（Built4rag, Built4skill）和商业产品
- 各产品技术栈不同（Python、TS、Go等）
- 单人开发 + AI Agent Team

### 决策
选择 **Polyrepo**：每个产品独立repo

### 决策理由
1. 开源产品需要独立repo建立社区
2. 产品独立 + Docker集成 → Monorepo共享代码优势不明显
3. 单人开发 → 管理成本可控

---

## 2026-04-23: License策略

| Repo类型 | License |
|----------|---------|
| 开源产品 | Apache 2.0 |
| 商业产品 | 私有EULA |
| Built4AI | CC BY 4.0 |

---

## 待决策
- Built4rag差异化定位
- Built4skill具体形态
- 商业产品技术栈
- Docker集成标准