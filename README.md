# 跨行业通用架构师团队（architect-common-team-0903）

> 汇总仓 · 由本地 DeepSeek Harness 的 0903 架构师模式沉淀而来
> 权威副本维护于本地 `dsh-home/.agent-presets/architect-common-team-0903/`，本仓为公开镜像与索引。

## 定位

不存在「一个通用架构师解决所有行业」——不同行业（游戏 / 金融 / 视频创作 / 小说创作 / 软件开发…）架构差异很大。
**通用架构师的价值 = 维护通用主干（各行业共享机制）+ 持续扩展行业架构师类型 + 把任务路由到匹配的管线。**

本体系按三层组织（0903，0831 的升级版，新增代替修改）：

| 层 | 内容 | 权威文件 |
|---|---|---|
| 主干（全行业共享） | 会话/角色/行业注册表、接力卡（relay）流转、平面直角坐标系自动合并、Issue/PR 团队主干、run_code 工具规范、记忆沉淀 | 本 README + 模式规格（见 agent.cordis.yml） |
| 路由层（0903 新增） | 行业类型注册表 + 关键词路由 + 管线装配（主干 + 领域包）+ 类型化角色命名空间 | [registry/industry-registry-0903.json](registry/industry-registry-0903.json) · [docs/ROUTING_LAYER_0903.md](docs/ROUTING_LAYER_0903.md) |
| 跨行业角色层（0903 新增） | 混合型人才注册（如 金融×软件、游戏×视频），专职优先 → 混合 → generic 兜底 | [registry/hybrid-registry-0903.json](registry/hybrid-registry-0903.json) · [docs/HYBRID_ROLES_0903.md](docs/HYBRID_ROLES_0903.md) |

## 仓库地图

```
kuahangyetongyongjiagoushituandui/
├── README.md                        # 本文件：定位 + 地图
├── .cnb.yml                         # 云原生构建流水线（文档与注册表完整性检查）
├── docs/
│   ├── INDEX.md                     # 详细索引
│   ├── ROUTING_LAYER_0903.md        # 路由层规则（行业注册 / 路由判定 / 领域包 / 升级协议）
│   └── HYBRID_ROLES_0903.md         # 跨行业角色层规则（混合注册 / 解析顺序 / 跨域纪律）
└── registry/
    ├── industry-registry-0903.json  # 行业类型注册表（唯一事实源）
    └── hybrid-registry-0903.json    # 混合角色注册表
```

## 协同生态（同一组织下的兄弟仓）

| 仓库 | 说明 |
|---|---|
| [xinxichidu（信息池）](https://cnb.cool/dongdongxiaozu/xinxichidu) | 全行业适配定位、ISSUE 看板、自动哨兵计划任务（HviCNB-Sentinel） |
| [zhuanyemishutuan（专业秘书团）](https://cnb.cool/dongdongxiaozu/zhuanyemishutuan) | 秘书机制：接收诉求 / 翻译意图 / 分类路由 |

## 核心机制速览

1. **接力卡流转**：任务 = relay 卡（五要素 + industry/architect_type 等 0903 字段），open → in_progress → done，自动派发器按角色注册表投递，卡 done 唯一依据 = 产物落盘 + 门禁真实 + 验收人确认。
2. **平面直角坐标系自动合并**：分支/门禁状态灌坐标系 → 决策（dispatch/wait/merge/escalate/block）→ 仅 merge 才真正合并。
3. **升级纪律**：0831 / 0901 preset 原样保留、独立演进；任何升级优先「新增代替修改」；新行业类型只追加注册表条目，绝不修改旧条目。
4. **高可用**：generic 兜底管线永存；行业专职 → 混合角色 → generic 三级降级，处处留痕。

## 构建

```bash
# push 时自动执行（.cnb.yml）：校验 registry JSON 可解析 + README 存在性
```

## 维护

- 镜像来源：`E:\1shuju\dsh-home\.agent-presets\architect-common-team-0903\`
- 完整模式规格（含主干规则全文）位于该 preset 的 `agent.cordis.yml`（运行时配置，不镜像进本仓）。
