# pi-webUI

基于 [pi-web](https://github.com/123zhaodehai/pi-web) 改造的 pi 编程智能体网页界面。

在浏览器中浏览会话、与智能体对话、分叉对话、切换消息分支。

## 快速开始

**本地开发：**

```bash
git clone git@github.com:123zhaodehai/pi-webUI.git
cd pi-webUI
npm install
npm run dev
```

启动后打开 [http://localhost:30141](http://localhost:30141)。

**可选参数：**

```bash
npm run dev -- --port 8080               # 自定义端口
npm run dev -- --hostname 127.0.0.1      # 仅本机访问
PORT=8080 npm run dev                    # 也支持环境变量
```

## 功能介绍

- **会话浏览器** — 按工作目录分组展示所有 pi 会话
- **实时对话** — 通过 SSE 流式输出与智能体实时交互
- **会话分叉** — 从任意用户消息创建独立的新会话分支
- **会话内分支** — 回退到任意节点继续对话，在同一文件内创建分支
- **分支导航器** — 可视化切换同一会话内的各个分支
- **模型切换** — 对话中途随时切换模型
- **工具面板** — 控制智能体可使用的工具
- **压缩会话** — 对长会话进行摘要，节省上下文窗口
- **引导 / 追加** — 打断正在运行的智能体，或在其完成后追加消息

## 注意事项

- **数据目录** — 默认读取 `~/.pi/agent/sessions` 下的会话文件。可通过环境变量 `PI_CODING_AGENT_DIR` 指定其他目录。
- **模型配置** — 从智能体数据目录下的 `models.json` 读取可用模型，可在侧边栏的「Models」面板中编辑。
- **文件浏览** — 侧边栏内置文件浏览器，可在标签页中查看当前工作目录下的文件。

## 项目结构

```
app/
  api/
    sessions/      # 读写会话文件
    agent/         # 发送命令、SSE 事件流
    files/         # 文件内容读取
    models/        # 可用模型列表与默认模型
    models-config/ # 读写 models.json
components/        # UI 组件
lib/
  session-reader.ts  # 解析 .jsonl 会话文件
  rpc-manager.ts     # 管理 AgentSession 生命周期
  normalize.ts       # 规范化 toolCall 字段名
  types.ts
```

会话文件存储路径：`~/.pi/agent/sessions/<编码后的工作目录>/<时间戳>_<uuid>.jsonl`

## 开发计划

- 基于个人使用需求持续优化 UI 交互
- 逐步添加自定义功能与主题

## 许可证

MIT
