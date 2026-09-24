# KIKI OS

> 一个用纯 Python 从零搭建的虚拟操作系统 + 图形桌面 + AI 助手。

KIKI OS 不是 Linux 套壳，而是把「操作系统该有的东西」全部用 Python 手搓了一遍。

## 特性

### 虚拟文件系统（VFS）
- SQLite 持久化，支持目录、文件、权限、所有者
- 回收站 + 恢复，软删除与永久删除分离
- 内置加密审计日志（Fernet + PBKDF2）
- 快照与回滚

### 图形桌面
- 自定义 CTk 窗口系统（标题栏/最小化/最大化/贴边）
- 桌面图标与 VFS Desktop 目录双向同步
- 拖拽自动网格对齐，就近吸附
- 多虚拟桌面、Dock 任务栏、通知中心
- 液态玻璃 / 亚克力视觉效果

### AI 助手
- 三种引擎：离线规则 / 在线 OpenAI 兼容 API / 本地 Ollama
- AST 工具协议：AI 直接输出 new_folder(path="x") 函数调用
- [THINKING] 思考过程可视
- 多代理工作流，复杂任务自动拆解
- 语音识别 + 语音合成

### 沙盒安全
- 子进程隔离执行 Python 代码
- 危险模块代理拦截，防结果不防过程
- 主线程不阻塞，60 秒超时兜底

### 杀毒引擎
- YARA 规则 + 内置启发式扫描
- 首次启动自动生成默认规则库
- 特征库保存后立即生效（无需重启）

## 安装

```bash
pip install customtkinter requests pillow psutil
```

可选依赖：

```bash
pip install litellm                # AI 在线引擎
pip install SpeechRecognition      # 语音识别
pip install vosk sounddevice       # 离线语音（推荐）
pip install edge-tts pygame        # 语音合成
pip install yara-python            # YARA 杀毒
pip install cryptography           # 加密
```

## 运行

```bash
python kiki_os.py
```

默认账户：

- 管理员：`admin` / `kiki`
- 访客：`guest` / `guest`

**首次登录请立即修改密码。**

## 命令行模式

```bash
python kiki_os.py --terminal                   # 纯终端模式
# 纯终端模式下不会启动图形界面，适合服务器/无桌面环境
python kiki_os.py --exec "help" --auto-login admin
python kiki_os.py --play snake admin
```

## 常用命令

| 命令 | 说明 |
|---|---|
| `help` | 查看所有命令 |
| `fm` | 打开图形文件管理器 |
| `ai <问题>` | 和 AI 对话 |
| `store` | 应用商店 |
| `security` | 打开安全中枢 |
| `voice` | 语音控制 |
| `snapshot create` | 创建系统快照 |
| `refreshdesktop` | 刷新桌面图标 |

## 更新日志

### v9.1 (2026-09)
- 桌面图标与 VFS Desktop 目录双向同步
- 拖拽实时网格对齐 + 就近吸附
- 审计 VFS 密钥持久化（跨会话可解密）
- 首次启动自动生成 YARA 规则库
- 特征库保存立即生效（无需重启）
- cd/ls 区分「路径不存在」与「权限不足」

### v9.0 (2026-09)
- AI 支持离线 / 在线 / Ollama 三模式
- AST 工具协议
- 沙盒从"禁过程"改为"禁结果"
- Python REPL 非阻塞
- 语音识别主线程调度修复

## 许可

仅供学习研究使用。

**Made with ❤️ by Robin-KK-Lab**
