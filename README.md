# Skill 到分享视频总控

将公开需求调研、Skill设计开发、真实验证实操、素材录制、口播视频、双封面和抖音上传素材包串成一期可恢复流程。用于从需求跑完整内容生产链，或继续本项目中断的阶段；不用于自动发布或只答一个知识问题。

`skillflow-orchestrator` · 原创 Skill · 内容版本 `42c6e2efb53b`

## 适用场景

将公开需求调研、Skill设计开发、真实验证实操、素材录制、口播视频、双封面和抖音上传素材包串成一期可恢复流程。用于从需求跑完整内容生产链，或继续本项目中断的阶段；不用于自动发布或只答一个知识问题。

## 安装与使用

```sh
git clone https://github.com/shuaige619/skillflow-orchestrator.git
cd skillflow-orchestrator
```

将此目录按宿主支持的方式登记为本地 Skill，或把 [SKILL.md](SKILL.md) 交给支持 Agent Skills 的助手读取。保留 `scripts/`、`references/` 等配套目录的相对位置；下载完成不代表宿主已加载。

需要已有完整 SkillFlow 项目和其 Python 执行器、脚本、合同与资源库。独立 Skill 仓库不包含这些工程，详见 references/project-dependencies.md。

## 输入与输出

**输入：** 明确的一期需求，或当前 episode 的 pipeline.json/state.json 与冻结产物。

**输出：** 各阶段真实产物、验收记录、可恢复工作单、素材包与独立上传回执。

## 使用示例

```text
请在已有 SkillFlow 项目中读取当前期状态，按 skillflow-orchestrator 继续尚未完成的工作单；只报告实际产物与检查结果。
```

以上是调用示例，不是已完成业务运行的记录。

## 工作方式

- 启动与继续
- 执行交接
- 选用迁入的风格库
- 关键规则

- [references/github-sharing.md](references/github-sharing.md)
- [references/motion-workflow.md](references/motion-workflow.md)
- [references/operating-contract.md](references/operating-contract.md)
- [references/project-dependencies.md](references/project-dependencies.md)

## 验证与限制

本发布步骤核对文件结构、README、上传前后文件摘要；未在本步骤重新执行业务效果验证。

这是依赖项目源码的总控 Skill，单独下载不能执行生产流程。公开包不含私有媒体和既有案例输入。

## 来源与二创说明

本项目原创。发布副本补充工程依赖说明，以可配置路径替换本机路径；release-provenance.json 保存源文件与修改身份。

文件身份与发布标准版本记录在 [发布清单](skill-release.json) 中。问题反馈请附复现输入、期望结果及内容版本，并先移除私人数据。

## 许可证

以仓库随附的 LICENSE / NOTICE 为准；未附许可证的部分尚未授予额外使用许可，请联系作者。
