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
python kiki_os.py --exec "help" --auto-login admin    # 执行完自动退出
python kiki_os.py --play snake admin                  # 直接启动游戏
# 注意：--auto-login 需要配合 --terminal 或 --exec 才能生效，不能单独用
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

## 发展史

从 v0.14 的 MiniOS 到今天的 KIKI OS，完整版本记录见 [CHANGELOG.md](CHANGELOG.md)。

| 版本 | 代号 | 里程碑 |
|---|---|---|
| **v0.14** | MiniOS | 🚀 第一个公开版本 |
| **v1.0** | KIKI OS | 正式更名，大胆创新 |
| **v2.0** | CTk 新生 | UI 从 Tk 迁移到 CTk |
| **v3.0** | 多用户纪元 | 多用户逻辑 + VFS 扩充 |
| **v4.0** | Play & Persist | 小游戏 + 持久化 |
| **v5.0** | Egg Hunt | 小彩蛋（凑数版） |
| **v6.0** | Guardian | 审计日志 + 持久化数据统一 |
| **v7.0** | Renaissance | 解释器 + AI + 核心应用 |
| **v8.0** | Metropolis | 桌面生态 + 系统工具全上 |
| **v9.0** | Voice Awakening | AI + 语音 + 沙盒 |
| **v9.1** | Desktop Sync | 桌面双向同步 + GPL v3 |

---

## 许可

仅供学习研究使用。

**Made with ❤️ by Robin-KK-Lab**
