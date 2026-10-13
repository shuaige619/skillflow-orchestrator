# 节点与实际适配

| 节点 | 内部流程 | 本项目接入方式 |
|---|---|---|
| research | 采集→审阅→选择 | 既有 Skill 雷达 collector，原始数据及需求卡 |
| brief | 合同→冻结样例→录制计划 | 验收JSON、需求文档与有哈希的样例 |
| build | 实现→审阅→冻结版本 | skill-creator、候选目录与安装ZIP |
| verify | 程序检查→原生任务→回读矩阵 | 测试报告、WorkBuddy实际任务、JSON/Markdown/CSV回读 |
| demo | 预检→操作录制→播放审看 | CUA CDP采集、CFR编码、原始帧与操作标记 |
| script | 证据→连续稿→初评改稿复评 | 分享口播Skill、segments、claim-map、评分 |
| produce | 导演→声音字幕→代表段→成片 | 既定火山音色、实际音频时轴、HyperFrames本地导出 |
| cover_copy | 文案→新人物→两画幅→检查 | imagegen与HTML封面，原尺寸及缩略图 |
| final_review | 技术→动态画面→听感与事实 | ffprobe、完整解码、音频等价、实际MP4观察 |
| package | 版本汇合→打包→解包比对 | media_pipeline bundle、SHA-256载荷清单 |
| archive | 收集→可编辑源归档→恢复核对 | media_pipeline archive、逐文件字节恢复验证 |
| feedback | 真实反馈→复现分类→修订 | 默认关闭，只有已有反馈时开启 |

每个工作单包含当前输入指纹；提交上期或失效回执会被拒绝。审核方法、执行者、实际观察和证据文件必须明确。状态文件不可手工改为 passed。

新供应商或新宿主优先增加边界明确的适配脚本，使用 argv 数组，不使用拼接shell。步骤输入应包含影响结果的源文件或版本清单。人机交接是可运行协议，不是无人值守自动批准。
