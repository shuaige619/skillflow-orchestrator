# GitHub 分享流程

在包含 skillflow/ 的项目根目录执行。规范为项目 `docs/standards/skill-sharing-readme.md`；结构化模板为 `contracts/skill-share-profile.template.json`。

1. `python3 -m skillflow share list` 汇总已配置目录、二创结果与本期冻结候选。来源缺失会明确列出；未列入的自有目录用 `share add 目录 --origin original|remix` 登记。同名不同版本保留，优先核对所选来源。
2. 根据真实功能、输入输出、最小调用、依赖与验证记录写发布资料。二创保留原作链接、具体增量和许可证。使用 `share profile SkillID 资料.json` 保存，或启动 `share serve` 在页面编辑。
3. `share prepare SkillID` 生成独立快照，回读 README 和文件清单；处理缺失引用、本机路径或未完成草稿。只修改发布副本，不改旧案例和验收状态。
4. 用户明确授权本次 GitHub 上传时，`share publish SkillID` 或点击“一键上传到 GitHub”；已给定的账号、仓库、可见性无需重复确认。授权缺少目标信息时先准备可审阅包，再询问必要信息。常规生产 run 不调用 publish。
5. 以实际远端内容回读通过的回执为上传成功依据。失败保留 operations/，重试先查副作用；同名未受管仓库与远端冲突不覆盖。GitHub 的 uploaded、视频 uploaded/published 和业务 verify 分别记录。
