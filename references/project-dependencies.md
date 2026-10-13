# 配套项目与依赖

本 Skill 是 SkillFlow 项目的总控操作入口，需在已有完整工程的根目录运行。
单独克隆本仓库只获得 Skill 指令，不含 Python 执行器、生产媒体或风格资源。

- 视频生产工程：[skillflow-style-library](https://github.com/shuaige619/skillflow-style-library)。该仓库当前为私有，需要作者授予访问；旧导出版本可能不含最新 GitHub 分享功能。
- 动效检索工程：[skillflow-motion-library](https://github.com/shuaige619/skillflow-motion-library)。该仓库当前为私有，使用者须自行取得访问及所选媒体的使用权限。
- 在工作区确认 `skillflow/`、`scripts/`、`contracts/`、`libraries/` 和 `episodes/` 可用，再执行本 Skill 中的命令。缺少时报告具体依赖，不凭 Skill 文件虚构执行结果。
- 动效检索脚本路径由当前工作区指定，例如 `MOTION_LIBRARY_ROOT/scripts/search-motion-library.py`。这是示意变量，需要替换为实际取得的动效库路径。
- 风格迁移说明位于配套工程的 `libraries/talking-head-styles/README.md`，包含旧预览、历史样片和 Remotion 风格的使用边界。

公开副本仅替换本机路径并解释配套工程。原流程验收要求、阶段状态及第三方来源未改变；此包未宣称可独立完成视频生产。
