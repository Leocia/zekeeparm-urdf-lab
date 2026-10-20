# Zekeeparm URDF Lab

在线站点：https://leocia.github.io/zekeeparm-urdf-lab/

这是同一 GitHub Pages 域名下的独立机械臂仿真工作台，支持浏览器内修改、校验和编译当前六轴机械臂 URDF，以及 TCP 拖拽、物理搬运、避障和障碍物尺寸编辑。站点只运行浏览器仿真，不连接 ROS、串口或真实机械臂。

教学实验舱支持实时 URDF 行号诊断、Link 坐标系、碰撞凸包与指垫显示、被拒直线与安全 TCP 轨迹对比、最近表面距离警戒线，以及真实采样/IK/碰撞检测日志。
点击「红色搬运场景」会应用示例箱体并启动归位。编辑器与教学实验舱内提供关节限位、障碍物布局实验说明。爆炸视图已移除。

规划器仍使用单个静态箱体与有限条启发式路线，采用离散关节采样、限速及 PD 跟踪；未实现三次时间插值或 RRT。红色路线也可能因 IK 或限位失败，日志会区分原因。重叠放置仍会被拒绝。

本仓库仅包含 Vite 构建生成的静态网页、MuJoCo WASM 和内置仿真模型，无需服务器后端。URDF 修改保存在当前浏览器的网站路径下，不修改服务器文件或其他访客的模型。点击「恢复网站模型」可清除本地副本；清除网站数据也会删除副本。

界面交互与工作台场景参考 [Yang-Ci/Rebot_Arm_AGV](https://github.com/Yang-Ci/Rebot_Arm_AGV/tree/445b48d5fd9fef8050c8a9ef5fd6ab32e3ace5cf/web_mujoco)，机械臂模型来自 Zekeeparm 工作区。上游参考仓库未提供根目录代码许可证，本部署不新增或声明其许可证。

GitHub Pages 从 `main` 分支根目录发布，保留 `.nojekyll`。更新前在源项目运行 `npm test` 和 `npm run test:static`，再同步 `dist/` 内容并推送。Service Worker 缓存和 URDF 副本按网站路径隔离。

如需撤销某次更新，在本仓库还原对应发布提交并推送；初次部署撤下站点可在仓库 Settings → Pages 中取消发布。原站点 https://leocia.github.io/zekeeparm-web-mujoco/ 单独保留。
