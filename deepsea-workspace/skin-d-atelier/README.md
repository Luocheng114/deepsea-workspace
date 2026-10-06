<div align="center">

<img src="docs/images/key-visual.webp" alt="鲸鱼娘 × D老师 的工作室" width="880">

# 鲸鱼娘 × D老师 的工作室

### DeepSea Workspace

为 DeepSeek Harness Web GUI 打造的双角色主题工作空间皮肤。
办公室背景、深浅两套界面基调、左右两个独立立绘位，再加一只住在侧栏里的 Q 版小人。

`中文 | [English](README_EN.md)`

![DSH](https://img.shields.io/badge/DeepSeek%20Harness-0.2.0--rc.2-4d6beb)
[![Code License](https://img.shields.io/badge/code-MIT-c0a97a)](LICENSE)
[![Artwork](https://img.shields.io/badge/artwork-CC%20BY--NC--SA%204.0-e0a458)](LICENSE-ARTWORK)

</div>

---

## 关于

这是一个**纯展示层**的客户端皮肤插件。它不注入服务端、不发出 Cordis 事件、不触碰模型请求——
`apply()` 只做三件事：给 `<html>` 打上作用域属性、按深/浅主题换上办公室背景、把角色立绘挂到透明图层上；
effect 被销毁时会把所有写入的 CSS 与 DOM 原样还原。

它派生自 [Small-tailqwq 的 maid-atelier（深海女仆工坊）](https://github.com/Small-tailqwq/dsh-deep-whale)，
保留了原有的深海蓝蕾丝骨架与 A 链署名素材，并把右位换成 D 老师、整体美术方向转向「深蓝办公室」。

## 功能

| | |
|---|---|
| **深浅双主题** | 跟随 DSH 的深/浅色切换，办公室背景、毛玻璃与边饰各自成套。 |
| **左右独立立绘位** | 左位默认鲸鱼娘、右位默认 D 老师。每边四张存图任选，也可以关掉只留一边。 |
| **单边水平翻转** | 左右位各自可镜像，方便同图不同向的排布。 |
| **侧栏 Q 版小人** | 男版（D 老师）/ 女版（鲸鱼娘）可切；作为背景图层垫在工作区列表后面。 |
| **头尺对齐** | 两张立绘按头部高度统一缩放；全身像一起踩地平线，半身像贴底锚定，左右完全对称。 |
| **输入框三态** | 常驻 / 空态胶囊 / 上滚隐去下滚渐现。 |
| **主题化界面** | 输入框、按钮、侧栏、工作区文件夹、管理页底色都成套换肤。 |
| **移动端适配** | 竖屏阈值 ≤700px；导航支持角标 / 顶栏 / 纵向 rail 三种方式。 |

> 「不那么二次元模式」「对话区字体」「按所选模型显隐立绘」「录制清场」等开关见 DSH 内
> **设置 → 皮肤 → 鲸鱼娘 × D老师 的工作室**，本 README 不逐项复述。

## 深与浅

办公背景·明 ｜ 办公背景·暗

<table>
<tr>
<td align="center" width="50%"><img src="preview/light.webp" alt="Light workspace" width="100%"></td>
<td align="center" width="50%"><img src="preview/dark.webp" alt="Dark workspace" width="100%"></td>
</tr>
<tr>
<td align="center">Light Workspace</td>
<td align="center">Dark Workspace</td>
</tr>
</table>

## 角色

### 鲸鱼娘

左侧主角。深海蓝配色、长发、围裙女仆装，视觉上与整套蕾丝界面同源；
站姿全身与抱笔记本两版可换，侧栏 Q 版女档也是她。

### D 老师

右侧主角。深色西装与领带的沉静一侧，与鲸鱼娘的明亮形成左右对照；
西装 / 黑毛衣两版可换，侧栏 Q 版男档默认是他。

<img src="docs/images/characters.webp" alt="鲸鱼娘与D老师" width="100%">

四张立绘分别是：女版·鲸鱼娘（站姿全身）、女版·抱笔记本、男版·西装、男版·黑毛衣。
任意一张都能放到任意一边，两边也可以选同一张再靠翻转区分。

## 细节

<table>
<tr>
<td align="center"><img src="docs/images/input-box-light.webp" alt="输入框" width="100%"></td>
<td align="center"><img src="docs/images/sidebar-chibi-dark.webp" alt="侧栏 Q 版" width="130"></td>
</tr>
<tr>
<td align="center">输入框：多层蓝框 + 侧挂笔记本</td>
<td align="center">侧栏 Q 版（背景图层）</td>
</tr>
</table>

## 安装

本包是一个标准的 DSH 插件 bundle，不需要编译，也不需要 `pnpm install`。

1. **下载或克隆本仓库**，得到 `skin-d-atelier/` 目录。
2. **装进你的 DSH profile**：

   ```powershell
   dsh plugin --profile web add <你放 skin-d-atelier 的目录>
   ```

   `<目录>` 是**包含 `package.json` 的那一层**，不是仓库根目录。
   本机开发时也常用 `link:` 形式：`dsh plugin --profile web add link:/abs/path/to/skin-d-atelier`。

3. **重启一次 DSH**。
4. **启用皮肤**：在设置里的皮肤管理器中选择「鲸鱼娘 × D老师 的工作室」。
   与基座 maid-atelier **互斥**，同一时刻只能启用一套。

> **适用版本**：DSH `0.2.0-rc.2`（本机实测）。其他版本**未验证**。
> `dsh plugin` 是把参数转交给 profile 目录下的 pnpm，profile 名按你自己的 `--profile` 改。

## 使用

启用之后在 **设置 → 皮肤** 里调这几项即可，改动走配置热重载，通常不用重启：

- **左位立绘 / 右位立绘**：四张任选或关闭
- **左位水平翻转 / 右位水平翻转**：单边镜像
- **侧栏 Q 版**：男版 / 女版
- **显示双立绘**：整体开关
- **输入框显示方式**：常驻 / 空态胶囊 / 上滚隐去
- **移动端导航方式**：角标 / 顶栏 / rail

深浅主题跟随 DSH 自己的设置，不用在这里切。

**恢复默认**：在同一个皮肤管理器里关掉本皮肤，或停用对应条目即可；
effect 销毁会还原全部样式，不需要卸载插件。

## 兼容性

| 项 | 状态 |
|---|---|
| DSH 版本 | `0.2.0-rc.2` 实测可用；`0.1.x` 与其它 RC **未验证** |
| 平台 | Windows 11 + Chrome / Electron 实测 |
| 分辨率 | 桌面 1920×1034 基准；立绘与边饰随窗口伸缩，窄窗口下留白会变小 |
| 与其它皮肤 | 与 maid-atelier、deep-whale-manager 互斥 |
| 移动端 | 竖屏阈值 ≤700px，导航三模式 |

## 已知限制

- 官方皮肤中心（`web-ui-skin-center`）与基座的 deep-whale 皮肤管理器**不能同时启用**，
  症状是设置按钮消失或侧栏错乱。本包假定你在用其中一套。
- 立绘对齐依赖内置的头部度量常量，换图后需要重算，不是完全自动的。
- 录屏时右下角的余额气泡、小游戏按钮、鲸鱼挂件需要手动用「录制清场」开关隐藏。
- 演示视频不随仓库分发，作为 Release 附件（见下）。

## 项目结构

```text
skin-d-atelier/
├─ lib/
│  ├─ index.js        # 插件入口
│  └─ client.js       # 皮肤运行时（预构建，含内嵌素材）
├─ preview/           # 皮肤管理器里显示的 light / dark 预览
├─ assets/icons/      # 应用图标
├─ docs/images/       # README 展示素材
├─ skin.json          # 皮肤元数据
├─ cordis.patch.yml   # 插件注册补丁
├─ LICENSE            # 代码 MIT + 美术不在其内的声明
├─ LICENSE-ARTWORK    # 美术 CC BY-NC-SA 4.0
└─ NOTICE             # 逐张素材来源、哈希与署名链
```

## 演示视频

演示片不放进本仓库——14 MB 的二进制不该由 Git 历史背着走。
它在 **v1.0.0 Release 的 Assets 里**，到仓库的 **Releases** 页面下载
`MASTER-v6-FINAL-MIX-v3.mp4` 即可。

| 项 | 值 |
|---|---|
| 规格 | 1920×1080 / 30 fps / 1297 帧 / 约 43.2 秒 |
| 编码 | H.264 + AAC 48 kHz 立体声 |
| 大小 | 14,382,939 B（约 13.7 MB） |
| SHA-256 | `f424f0382ae29e4c6d3f250bd5d195f28d0e3719cd36a0d4460dc43b749f010e` |

下载后可以核对一下 SHA-256，确认拿到的是原始成片。
配乐出处见 [docs/MEDIA-CREDITS.md](docs/MEDIA-CREDITS.md)。

## 致谢与授权

这个项目叠了三层来源，改动与再分发都要同时满足它们：

- **代码与界面骨架** — MIT，Copyright (c) 2026 Small-tailqwq（maid-atelier 基座）
- **女仆工坊装饰素材（A 链）** — CC BY-NC-SA 4.0
  一创 上善 → 二创 ZipZipPipe → 三创 Small-tailqwq，署名必须原样保留
- **D 老师素材（B 链）** — 原作者子午，公开授权「不商用即可」，本仓库不含任何变现入口

两张女版立绘为本项目使用 AI 工具重新制作，不属于上述任何原作。
逐张来源、SHA-256 与处理方式见 [NOTICE](NOTICE)。

**授权是分开的**：

- 代码、脚本、配置 → [MIT](LICENSE)
- 美术资源、角色、背景、图标、预览图（含 AI 生成与 AI 辅助）→ [CC BY-NC-SA 4.0](LICENSE-ARTWORK)，**仅限非商业使用**

美术被打包进 `lib/` 的 CSS 或 base64 里**不会**改变它的许可。权利人提出异议即下架。

### 开发工具

工程脚手架（目录模板与构建预设）来自
[zhu1090093659/dsh-web-ui](https://github.com/zhu1090093659/dsh-web-ui)（作者 Solitude）。
本仓库只分发**成品**，不包含 patch 脚本与构建流程。

演示片配乐《Bright Bell Motif》由 [Suno AI](https://suno.com/s/qNyElpaJUK0jTZ4Z) 生成。
逐项出处见 [docs/MEDIA-CREDITS.md](docs/MEDIA-CREDITS.md)。
