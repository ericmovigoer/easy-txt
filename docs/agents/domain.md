# 领域文档

工程技能探索代码库时，应按以下规则使用本仓库的领域文档。

## 探索前读取

- 根目录的 `CONTEXT.md`；或者
- 如果根目录存在 `CONTEXT-MAP.md`，它会指向各上下文的 `CONTEXT.md`，读取与当前主题相关的文件
- `docs/adr/` 中与即将处理区域有关的 ADR；在多上下文仓库中，还应检查 `src/<context>/docs/adr/` 下的上下文级决策

如果这些文件不存在，静默继续。不要报告缺失，也不要预先建议创建。`domain-modeling` 技能会在术语或决策真正明确后按需创建它们。

## 文件结构

Single-context 仓库：

```text
/
├── CONTEXT.md
├── docs/adr/
│   ├── 0001-event-sourced-orders.md
│   └── 0002-postgres-for-write-model.md
└── src/
```

Multi-context 仓库（根目录存在 `CONTEXT-MAP.md`）：

```text
/
├── CONTEXT-MAP.md
├── docs/adr/                          ← 系统级决策
└── src/
    ├── ordering/
    │   ├── CONTEXT.md
    │   └── docs/adr/                  ← 上下文级决策
    └── billing/
        ├── CONTEXT.md
        └── docs/adr/
```

## 使用词汇表中的术语

输出中命名领域概念时——例如 issue 标题、重构建议、假设或测试名称——使用 `CONTEXT.md` 中定义的术语，不要改用词汇表明确避用的同义词。

如果需要的概念尚未出现在词汇表中，这通常意味着正在发明项目未使用的语言，或者确实存在需要交由 `domain-modeling` 处理的领域空缺。

## 标明与 ADR 的冲突

如果输出与现有 ADR 冲突，应明确指出，而不是静默覆盖：

> 与 ADR-0007（事件溯源订单）冲突，但值得重新讨论，因为……
