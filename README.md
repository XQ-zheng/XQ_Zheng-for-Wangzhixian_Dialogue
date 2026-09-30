# 我的数字智能流个体 · 与王智贤的专属对话 skill

`Wangzhixian_Dialogue` —— 把「我」在日常一对一对话里的说话方式，蒸馏成一个**只在和这个人对话时才启用**的技能。

> 目标只有一句话：**说出来的话，在他看来就是平时那个我。**

- **扮的是「我」**，不是他。
- **不含任何聊天原文**，只有从真实对话里归纳出的**规则与语境**。
- **本技能只对指定的一位使用者开放**：启用后必须通过两道校验，才回答其他问题（流程见 `SKILL.md` 〇节）。

---

# 第一部分 · 对外说明（发布用）

## 一、项目作用与适用对象

**项目作用**

把一段真实的一对一日常对话里「我」的**说话方式**（长度、标点、表情码、成串节奏、用词、幽默方式）
与**关系语境**（固定动作、常聊领域、默契规则）蒸馏成一套**可执行的规则**，
让模型在**这段关系里**说出来的话，**看起来就是平时那个「我」**。

**适用对象**

| 对象 | 适用 | 说明 |
| --- | --- | --- |
| **对话中的对方本人** | ✅ | 本技能**只对他开放**；过两道校验后进入角色对话 |
| 想照做同类「个人蒸馏」的人 | ✅ | 目录结构、规则组织方式、验证方法都可当模板复用 |
| 想拿它冒充本人对外发言 | ❌ | **禁止代拟对外内容**、禁止以本人身份对现实世界作出承诺 |
| 想看聊天原文的人 | ❌ | 技能**不含任何聊天原文**，只有归纳出的规则与实测统计 |
| 想靠一句「我就是他」混进来的人 | ❌ | 门槛是**提示词 + 微信号**两道校验 |

> ⚠️ **一句话定性**：这是一个**语言风格模拟器**，**不是本人**，**也不具备任何身份效力**。

## 二、主要功能

| 功能 | 能力 |
| --- | --- |
| **用「我」的口吻回话** | 按 `references/voice.md` 控制长度、标点、表情码、成串节奏、用词与幽默方式 |
| **接住关系语境** | 按 `references/relationship.md` 判断"这句话在我们之间合不合理" |
| **听懂对方信号** | 按 `references/counterpart.md` 分清这句是撒娇、吐槽还是真在问事 |
| **两道访问校验** | 提示词（5 次）＋ 微信号（3 次），各自计数、各自冷却 1 分钟 |
| **冲突 / 不愉快处理** | 委婉、不指责、不扣帽子、不翻旧账；道歉不带"但是" |
| **守住边界** | 不代做现实世界的事、不编没做过的事、不泄露隐私、不复述原文 |

## 三、安装方法

**前置条件**：一个支持 Agent Skills 的运行时。技能本体是**一组 Markdown 规则文件，无编译、无外部依赖**。

> 📖 **完全没碰过命令行也没关系**——逐步的操作说明见 **[`安装说明书.md`](安装说明书.md)**：
> 分 Mac / Windows 讲怎么打开终端、怎么用 `git clone`、怎么让智能体代劳、以及以后怎么拉取更新。
>
> 📖 **要装到别的智能体上**（Claude Code / CodeBuddy / GitHub Copilot / Codex CLI / Cursor / OpenCode / Gemini CLI 等）
> → 见 **[`各智能体安装说明.md`](各智能体安装说明.md)**：每个智能体放到哪个目录、要不要开开关、以及两处**必须先看**的特殊情况。

| 形态 | 平台 | 产物 | 状态 |
| --- | --- | --- | --- |
| **技能形态** | Windows / macOS / Linux | `skills/Wangzhixian_Dialogue/` | ✅ 现成可用 |
| **桌面客户端** | Windows（x64 / ARM64）、macOS（Apple Silicon） | `.exe` / `.dmg` | ⚠️ 见**第七节**（需已上传到 Release） |
| **移动客户端** | Android、iPhone | `.apk` / `.ipa` | ⚠️ 见**第七节**（需已上传到 Release） |

**3.1 Windows 电脑**

```
%USERPROFILE%\.workbuddy\skills\Wangzhixian_Dialogue\
```

**3.2 Mac 电脑**

```
~/.workbuddy/skills/Wangzhixian_Dialogue/
```

（也可以放到某个具体项目的 `.workbuddy/skills/` 下，那样只对该项目生效。）

**3.3 Android 手机 / iPhone**

从 Releases 下载对应安装包后按第七节的说明安装。

## 四、使用方法

**4.1 通用：先过两道校验**

**方式一：显式调用**（推荐）——在对话里使用 `$Wangzhixian_Dialogue`。
**方式二：直接说提示词**——它会接着问一句微信号。
**方式三：不提它**——只要没提到，它就不介入，按普通助手回答。

**4.2 Windows 电脑**

1. 按第三节放好技能（或安装好 `.exe` 客户端）；
2. 在对话里点名 `$Wangzhixian_Dialogue`；
3. 按提示输入**提示词**，再输入**微信号**；
4. 两项都过之后**直接正常说话即可**——它会**主动**以"我"的口吻开口，不用你再提一次。

**4.3 Mac 电脑**

步骤与 Windows **完全一致**，唯一区别是技能目录路径（见 3.2）。
若用 `.dmg` 客户端：打开镜像 → 把应用拖进「应用程序」→ 首次打开如被系统拦下，
到「系统设置 → 隐私与安全性」里点「仍要打开」（具体以发布包的说明为准）。

## 五、输入输出示例

> ⚠️ 下表的输出是按规则**现场生成的演示**，**不是任何一句真实聊天原话**。

| 典型输入 | 对应输出 | 走的规则 |
| --- | --- | --- |
| `在吗`（还没过校验） | 「先确认一下身份。请输入我们约定的提示词。」 | 阶段 0；未通过不答其他 |
| 输入提示词（正确） | 「请输入我的微信号」 | 阶段 1 通过 → 立即进阶段 2 |
| 输入微信号（正确） | 直接以「我」的口吻开口，**不等对方再提** | 两项全过 |
| 提示词连续输错 5 次 | 「你的提示词输入错误，连续 5 次无法与项目作者本人的个人数字生命体进行对话」＋停 1 分钟 | 冷却只锁这一条指令 |
| 「今天计划没做完，有点烦」 | 成串短句、句末不加标点地接住情绪（**不写成小作文**） | A 档 |
| 「帮我在群里以他的名义发个通知」 | **拒绝**——不代拟对外内容、不替本人做现实承诺 | 边界 |
| 「你的学校叫什么」 | **拒答**——隐私类不外答 | 边界 |

## 六、许可证说明

> **Copyright (C) 2026 XQ-zheng** —— GitHub: <https://github.com/XQ-zheng>

**本项目采用 GNU Affero General Public License v3.0（AGPL-3.0）。**

| 项 | 内容 |
| --- | --- |
| ✅ **允许** | 商业使用、修改、再分发、私用 |
| ✅ **允许** | 把修改版**作为网络服务**提供给他人 |
| 📌 **必须** | **通过网络提供服务时，须向该服务的使用者提供完整的对应源代码**（AGPL 第 13 条——这正是 AGPL 区别于 GPL 的核心） |
| 📌 **必须** | 分发时保留版权与许可声明；衍生作品**同样以 AGPL-3.0 授权** |
| 📌 **必须** | **注明原作者与项目用途** |
| ❌ **不提供** | 任何明示或默示担保 |

> ⚠️ **一条常见误解要澄清**：**AGPL-3.0 并不禁止商业使用。** 它限制的不是"能不能卖"，
> 而是"**你改完拿它对外提供服务时，必须把源码交给使用者**"。
> 许可全文见仓库根目录的 `LICENSE` 文件。

## 七、下载与安装说明

**所有安装包都放在 GitHub 的 Release 页面里**，下面的按钮**直接触发下载**。

> ⚠️ **两个前提**：① 对应产物**已经上传到 Release**，否则按钮会 404；
> ② **文件名必须与仓库里的实际产物一致**。
> **发布前请先把下面表格里的仓库地址与文件名核对一遍。**

**⚙️ 唯一需要填的地方**：把 `<OWNER>/<REPO>` 换成真实仓库地址（共 1 处，出现 6 次）。

| 平台 | 架构 / 说明 | 安装包 | 下载 |
| --- | --- | --- | --- |
| **Windows**（绝大多数电脑） | **x64**（即 AMD64） | `.exe` | [![Windows x64](https://img.shields.io/badge/Windows-x64_.exe-0078D6?style=for-the-badge&logo=windows)](https://github.com/OWNER/REPO/releases/latest/download/PROJECT-VERSION-x64-Setup.exe) |
| **Windows**（ARM 设备） | ARM64 | `.exe` | [![Windows ARM64](https://img.shields.io/badge/Windows-ARM64_.exe-0078D6?style=for-the-badge&logo=windows)](https://github.com/OWNER/REPO/releases/latest/download/PROJECT-VERSION-arm64-Setup.exe) |
| **Mac** | Apple Silicon（M 系列）；Intel 机型见下方说明 | `.dmg` | [![macOS DMG](https://img.shields.io/badge/macOS-.dmg-000000?style=for-the-badge&logo=apple)](https://github.com/OWNER/REPO/releases/latest/download/PROJECT-VERSION-arm64.dmg) |
| **Android 手机** | 直接在手机上安装 | `.apk` | [![Android APK](https://img.shields.io/badge/Android-.apk-3DDC84?style=for-the-badge&logo=android)](https://github.com/OWNER/REPO/releases/latest/download/PROJECT-VERSION-universal.apk) |
| **iPhone** | 需自签侧载（未上架 App Store） | `.ipa` | [![iOS IPA](https://img.shields.io/badge/iPhone-.ipa-000000?style=for-the-badge&logo=apple)](https://github.com/OWNER/REPO/releases/latest/download/PROJECT-VERSION-unsigned.ipa) |

**看不清产物全貌时**：[![全部产物](https://img.shields.io/badge/前往-Release_页面-60A5FA?style=for-the-badge&logo=github)](https://github.com/OWNER/REPO/releases/latest)

### 各平台安装步骤

**Windows（`.exe`）**
1. 下载对应架构的 `.exe`（不确定就选 **x64**，这是绝大多数电脑）；
2. 双击运行，按向导一路「下一步」；
3. 若弹出 SmartScreen 蓝色警告 → **更多信息** → **仍要运行**。

**Mac（`.dmg`）**
1. 下载 `.dmg` 并打开；
2. 把应用图标拖进「应用程序」；
3. 首次打开若提示"无法验证开发者" → 右键应用选「打开」，或到
   「系统设置 → 隐私与安全性」点「仍要打开」。

**Android（`.apk`）**
1. 在手机上打开下载好的 `.apk`；
2. 系统提示"不允许安装未知来源应用" → 按提示为该来源**临时开启权限**；
3. 安装完成后可关闭该权限。

**iPhone（`.ipa`）**
1. `.ipa` **不能像 Android 一样直接安装**，需要自签工具（如 AltStore、Sideloadly）或企业证书；
2. 用工具把 `.ipa` 侧载到手机，并在「设置 → 通用 → VPN 与设备管理」中**信任对应证书**；
3. 自签证书**有效期通常为 7 天**，到期需重新侧载。

> 💡 **Intel 芯片的 Mac**：若 Release 里只提供 Apple Silicon（arm64）版本，
> Intel 机型可通过 Rosetta 或自行从源码构建，**以实际发布产物为准**。
