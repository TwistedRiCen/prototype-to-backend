# prototype-to-backend

[English](README.md) | [简体中文](README.zh-CN.md)

`prototype-to-backend` 是一个用于将产品原型和需求资料转换为后端开发设计产物的 AI Skill。

它主要面向使用 Codex 的后端开发人员。这个 Skill 的重点不是生成前端页面，而是从 HTML 原型、Axure 原型包、在线原型、PRD 或截图中识别业务含义，并输出后端开发可以直接参考的系统分析、领域模型、数据库设计、接口设计、审批流、状态机、权限模型、开发任务拆分、待确认问题和设计评审。

## 这个 Skill 能做什么

- 分析 Axure HTML 原型包、在线原型地址、产品需求文档和截图。
- 提取用户角色、模块树、菜单树、页面清单、表单字段、查询条件、列表字段、按钮动作和后端操作。
- 生成后端开发材料，包括系统概览、领域模型、数据库设计、REST API 设计、状态机、审批流、权限模型、开发计划和产品待确认问题。
- 模板采用中文优先、中英双语的结构，方便中文团队评审，同时保留英文技术命名供后端实现使用。
- 在分析中文企业系统时保留中文业务术语，并为实体、接口、权限、状态和表名补充英文技术命名。
- 区分已确认事实、合理假设和待确认问题，避免把无法确认的信息写成确定结论。
- 内置 grill-me 风格的设计评审阶段：先生成后端设计产物，再主动拷问这些产物，找出接口缺口、薄弱的数据模型、不闭环的流程、权限缺口和模糊业务规则。

## 支持的输入

- Axure HTML 原型包。
- 在线原型地址。
- 产品需求文档。
- 业务流程文档。
- 截图，作为缺少更完整资料时的 fallback。

## 生成的输出产物

模板使用中文优先的双语标题和表头，例如 `系统概览 / System Overview`、`字段 / Field`。

- `01-system-overview.md`
- `02-domain-model.md`
- `03-database-design.md`
- `04-api-design.md`
- `05-state-machine.md`
- `06-workflow.md`
- `07-permission-model.md`
- `08-development-plan.md`
- `09-open-questions.md`
- `10-design-review.md`

## 安装命令

```bash
npx skills@latest add https://github.com/<owner>/prototype-to-backend --skill prototype-to-backend -g -a codex -y
```

请将 `<owner>` 替换为托管该仓库的 GitHub 用户或组织名称。`-a codex` 表示只安装给 Codex，避免选择一堆不需要的 Agent。

## 更新方式

当该仓库发布新版本后，使用 Skills CLI 安装的用户可以通过下面的命令更新本地已安装的 Skill：

```bash
npx skills@latest update -g prototype-to-backend
```

常用相关命令：

```bash
# 查看已安装的 skills
npx skills@latest list

# 检查是否有可用更新
npx skills@latest check

# 如果之前误选了很多 Agent 导致更新失败，可以只重新安装到 Codex
npx skills@latest add https://github.com/<owner>/prototype-to-backend --skill prototype-to-backend -g -a codex -y

# 更新所有全局 skills
npx skills@latest update -g
```

Codex 通常会自动检测 Skill 变更。如果更新后没有出现新版本，可以重启 Codex。

## 使用示例

```text
使用 prototype-to-backend 分析 ./prototype 目录下的 Axure HTML 原型包，并生成后端开发设计产物。重点关注系统概览、领域模型、SQL Server 友好的数据库设计、REST API、审批流、状态机、权限模型、开发计划和待确认问题。保留中文业务术语，并补充英文技术命名。不要生成前端代码。
```

```text
请从后端开发视角分析这份中文 OA 审批 PRD，输出领域模型、数据库表、接口、审批流程、状态机、权限点和待确认问题。无法确认的规则必须放入 Open Questions。
```

```text
原型地址是 https://example.com/prototype。请先检查 sitemap、页面、表单、列表、按钮、交互和备注，再生成适用于 Spring Boot REST 后端开发的设计文档。
```

## 推荐工作流程

1. 提供尽可能完整的资料，优先使用 Axure HTML 原型包或在线原型地址。
2. 先让 Agent 盘点页面、菜单、表单、列表、按钮、状态和交互。
3. 先生成前 9 个后端设计产物。
4. 执行内置的 grill-me 风格设计评审，并生成 `10-design-review.md`。
5. 与产品经理、业务方和后端开发一起评审 `09-open-questions.md` 和 `10-design-review.md`。
6. 在确认业务规则和设计修正后更新设计产物。
7. 使用 `08-development-plan.md` 拆分后端开发任务。

## 仓库结构

```text
prototype-to-backend/
|-- README.md
|-- README.zh-CN.md
|-- LICENSE
`-- skills/
    `-- prototype-to-backend/
        |-- SKILL.md
        |-- agents/
        |   `-- openai.yaml
        |-- templates/
        |   |-- 01-system-overview-template.md
        |   |-- 02-domain-model-template.md
        |   |-- 03-database-design-template.md
        |   |-- 04-api-design-template.md
        |   |-- 05-state-machine-template.md
        |   |-- 06-workflow-template.md
        |   |-- 07-permission-model-template.md
        |   |-- 08-development-plan-template.md
        |   |-- 09-open-questions-template.md
        |   `-- 10-design-review-template.md
        `-- examples/
            |-- axure-html-package-example.md
            |-- oa-approval-example.md
            |-- procurement-system-example.md
            `-- design-review-example.md
```

## 使用限制

- 该 Skill 不能推断原型和需求资料中不存在的隐藏业务规则。
- 模糊规则必须记录为假设或待确认问题。
- 仅基于截图进行分析的可靠性低于 HTML 原型包或 PRD。
- 生成的数据库和 API 设计是可用于开发讨论的草案，仍需要业务和技术评审确认。
- 设计评审阶段只能基于已有原型和产物发现风险；未确认的产品或业务规则仍需要业务方确认。

## 许可证

本项目使用 MIT License，详见 [LICENSE](LICENSE)。
