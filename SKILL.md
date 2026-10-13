---
name: skillflow-orchestrator
description: 将公开需求调研、Skill设计开发、真实验证实操、素材录制、口播视频、双封面和抖音上传素材包串成一期可恢复流程。用于从需求跑完整内容生产链，或继续本项目中断的阶段；不用于自动发布或只答一个知识问题。
---

# Skill 到分享视频总控

使用前读取[配套项目与依赖](references/project-dependencies.md)。本仓库只分发操作 Skill，实际执行需要完整 SkillFlow 工程。

先读取当前项目 README.md、docs/node-workflows.md 和目标 episode 的 pipeline.json/state.json。已完成阶段以冻结产物及验收记录为准，不因对话变短或重启而重做。

## 启动与继续

在包含 skillflow/ 的项目目录运行：

```sh
python3 -m skillflow status episodes/本期编号
python3 -m skillflow audit episodes/本期编号
python3 -m skillflow run episodes/本期编号
```

新一期先 `init episodes/本期编号 --id 本期编号 --title 本期主题`。默认生成十二节点的完整内部交接步骤；按实际工作台和供应商将可确定执行的步骤绑定 command/import，保留需要模型判断、UI录制和实际审阅的 handoff。现有新案例 pipeline.json 可作有真实执行证据的适配示例，复制时必须替换本期路径与任务，不能继承上期通过状态。

## 执行交接

`needs_input` 产生一个包含依赖快照、输入指纹、预期输出和检查项的 request.json。这里通常表示当前代理需要执行下一子流程，不表示必须把填表工作交还用户。

1. 读取当前请求，只处理本期已授权范围；调用节点对应的现有专业 Skill、脚本或工作台。
2. 产物放在当前 episode 内，保留原输入。外部生成保存 job/request ID、状态与原始文件；未知结果先查状态，不盲目重发。
3. 实际检查文件与效果。回执 reviewer 使用 name、kind、method；checks 使用 name、status、observation、evidence_path。没有做的检查写 not_run，不能复制上一期分数。
4. `scripts/prepare_response.py` 将真实输出、证据和当前输入指纹绑定为回执，再 `python3 -m skillflow submit episodes/本期编号 回执路径`。
5. 继续执行直到下一个需要实际操作的子流程。只在确实缺少用户信息或真实听感反馈时询问，同时完成独立工作。

## 选用迁入的风格库

本项目共用 `libraries/talking-head-styles/`，来源是 ai-talking-head-studio。新一期制作前，用 `python3 -m skillflow styles` 查候选，查看对应预览与设计文件，再按内容和用户已给方向选用。已有本期风格按冻结版本继续，不为更新共享库而改动已完成案例。

`python3 -m skillflow use-style episodes/本期 风格ID --aspect 16:9` 将规则与资源固定到本期，并把同一个 `style_context` 接入制作、封面、成片验收和归档。也可在 `init` 时给 `--style`。读工作单中的风格 Brief 和锁定文件，导演/封面记录应用依据，成片检查与选定方向一致，归档纳入全部冻结资源。改选用 `--replace`，保留旧快照并重验受影响下游。

原库存在旧版预览、缺失历史样片和 Remotion 专用风格；看 [迁移说明](references/project-dependencies.md) 的具体边界。预览不能替代本期代表段检查；源项目封面比例不自动覆盖本期合同；该库与动效库分别承担视觉语言和具体动作参考。

## 关键规则

Skill 分享使用 [GitHub 分享流程](references/github-sharing.md)。原创和二创均登记；新一期 verify 的 share-ready 工作单按项目 README 标准生成分享资料，来源和业务验证范围绑定本版本。用户已明确要求 GitHub 上传或在页面点击上传时，执行建仓、上传、远端回读并保留独立回执；不能把素材包就绪视为已上传，不能更改视频发布状态。

含画面制作时读取[新版动效流程](references/motion-workflow.md)，以工作单 `motion_context` 中的冻结规范执行。镜头景别与相机/对象姿态、转场发起与接收、特效语义和片尾执行卡必须进入本期实际实现。`init` 自动绑定 0.3.2 及 plan/integrated/export 三道程序检查；已有一期用 `python3 -m skillflow use-motion episodes/本期 --project work/视频目录` 明确采用，保留旧产物并使制作下游失效。完成当前要求后再提交回执，不能用通用技术报告替代新版动态验收。

- 实际模型调用、直接脚本调用、人工构造样例、真实业务输入分别记录；输出文件必须回读。
- 录屏保留原始帧或原片、时序、操作标记、程序版本和结果；解释动画不能冒充真实宿主录屏。
- 实操演示默认边操作边讲，交代当前动作、系统反馈和可见结果；只保留必要短停顿，不默认插入整段无解说空白。字幕避开正在检查的内容。用户明确要求静音观察时另行记录。
- 先定口播和导演方案，再生成配音；以实际音频排时，保存完整及独立音轨与字幕。
- 听感采用真实试听证据。用户已试听通过的音轨可用编码后等价检查证明同版；没有主观试听记录不能自动标为通过。
- 正常播放实际MP4；图片检查原尺寸和缩略图。技术检查不能替代审美检查。
- 内容变化调用 invalidate，由依赖关系使相关下游失效；失败或中断先检查副作用，再 retry。完成的不可变产物可以复用。
- 上传包就绪与已经上传、已经发布独立。生成素材包不触发外部上传或发布。
- 当前执行器是本地单写者，按DAG依次推进；可并行准备独立素材，不能声称已有分布式队列或自动无人值守审核。

详见 [节点、产物与适配器](references/operating-contract.md)。
