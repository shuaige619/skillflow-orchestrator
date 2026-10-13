# 镜头、转场、特效与片尾：0.3.2 本地接入

本项目采用 `libraries/motion-workflow/0.3.2/manifest.json` 列出的来源快照，冻结自抖音视频创作的 douyin-video-workflow 0.3.2。每期复制至工程 `motion-workflow/`，总控绑定版本和所有文件摘要。原项目后续变化不暗中替换本期规则。原文中的 DSH 工具、videos 目录及默认深色样式是来源环境信息；本项目使用下列入口、episodes 目录和本期 style_context，保留本期画幅、音色及上传权限边界。

## 制作前

读取工作单 `motion_context`。在冻结目录中先读 `docs/standards/motion-direction.md`、`speech-to-motion.md`、`motion-library-use.md` 与 `docs/templates/motion-director-brief.md`；按需参考 `integrations/deepseek-harness/douyin-video-workflow/references/validated-motion-example.md`。该示例的旧通过状态不是本期通过证据。

按语义、观看任务检索候选，实际播放源秒段，再决定复用组件、移植、按机制重做或保持静止。当前外部动效库仍可通过 `MOTION_LIBRARY_ROOT/scripts/search-motion-library.py` 检索；这是显式素材依赖，规范和校验器已迁入。将所选/未选候选的真实目录记录冻结为本期 `motion-catalog.json`，所看片段放在私有参考目录并记原文件摘要和许可边界。它们不进入公开上传包。

在同一份 `motion-usage.json` 记录候选、源秒段、实际看片、选择/拒绝理由、接入方式与可见特征。沿用来源 schemaVersion=1。`shots.json`（workflowVersion=0.3.2）按镜头记录：id、全片 range、watchingTask、scale、mainObject、实际词句 anchor、camera/object 各自 from/to/reason、readingWindow、transition（kind/initiator/preservedState/receiver）、effects（id/object/trigger/purpose/range/settle）或 staticReason、implementation（file/locator）。recentWorks 记录最近可用作品的布局、主运动与本期取舍，不硬凑数量。

`ending-card.json` 单独记录 shotId、主视觉 mainVisual、真实结果 realResult、试用邀请 invitation、接续对象 handoffObject、风格连续 styleContinuity、最终构图 finalFrame、稳定阅读 stableWindow 和前镜交接 handoffRange。主视觉必须承接本期结果；邀请在结果看清后出现，不把整面强调色加口号当作默认片尾。用户指定手绘线条风时，文字、轮廓、纸白空间和运动语法一致。

配音前完成初稿；已有获准声音直接按实际词句重排画面，不重配或压缩语速。制作前执行 `scripts/check_motion_workflow.py --project 工程 --stage plan`。未知声音锚点可先保留内部草稿；进入本期正式制作前补齐实际时间。静止与有意硬切都是合法导演选择，写明理由，不机械增加特效。

## 制作与代表段

所有选中机制落实到本期文件与对象/调用，保持身份、轮廓、路径、接管和回稳。相机与物体分别设计，关键文字不随容器挤扁。特效绑定筛选、处理、抵达、聚焦或核验事件；阅读时不争抢注意力。

冻结实际渲染输入到 `render-source-manifest.json`。导出含主要机制的代表段；独立系统分别检查。片尾代表段从前镜交接前开始直到最终末帧，带实际音轨和字幕，可因完整覆盖略长于通常 8–12 秒。正常速度查看并保存 `motion-pilot-review.json`：status、sourceManifestSha256、pilots[{file,sha256,globalRange,mechanisms,playback,observed,coversEnding}]。每项机制必须有代表段覆盖。内部审看沿用用户授权自行完成。

需要 Studio 预览时先打开再冻结：预览器可能给 HTML 补写 `data-hf-id` 等编辑标识，这同样会触发字节变化检查。发生变化时保留拦截记录，检查真实差异，重新检查并固定源版本。只有已证明纯编辑元数据变化、渲染结构/动作/素材未变时才可记录明确的等价依据，复用同版代表视频并重绑源清单；不把未知修改归为无影响。

`--stage integrated` 核对原版接入表、实际实现定位、代表段证据、源清单身份及片尾覆盖后才允许完整导出。项目检查命令通过不等于审美通过。

## 成片与交付

正常速度检查最终编码 MP4 的所有镜头及转场，逐项对照 expectedFeatures，查清运镜、对象连续、速度/错相、读字窗与末帧。在 motion-usage 的 export 写同一最终文件及 SHA；verification 记录源/成片播放、实际编码抽帧和每个特征观察。

另存 `motion-final-review.json`：status、playback、videoSha256、sourceManifestSha256、shots[{shotId,camera,transition,effects,reading,frames}]、ending{handoff,realResult,invitation,lastFrame,subtitleSafety}。改版把旧/新同语义区间和观看收益记进导演与验收文档。整体评分不能掩盖静态、动态或改版核心缺口。

`--stage export` 拒绝旧片哈希、缺镜头、缺特征或缺片尾证据。上传包只含发布必需素材；完整工程归档同时保存规则快照、三道检查结果、导演/镜头/动效记录、代表段与实际 MP4 证据。技术检查无法代替主观听感；同版已试听声音可复用真实验收与编码等价证据。
