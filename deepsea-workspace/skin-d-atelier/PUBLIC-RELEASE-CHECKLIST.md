# PUBLIC RELEASE CHECKLIST

项目：鲸鱼娘 × D老师 的工作室 / DeepSea Workspace
仓库位置：公开总仓库下的 `deepsea-workspace/`（已 `git init`，分支 `main`，未 commit、未 push）
检查日期：2026-10-06（最终检查）

状态口径：

- **READY** —— 仓库内该做的都做完了，本身没有缺陷
- **WAITING FOR USER ACTION** —— 需要你在仓库之外动手（授权、GitHub 侧操作）
- **BLOCKED** —— 有真实缺陷，不解决就不能发布

> 「尚未创建 GitHub Release / 尚未 push」属于 **WAITING FOR USER ACTION**，
> 不是项目缺陷。

---

## 0. 总览

| 阶段 | 状态 |
|---|---|
| README（中/英） | **READY** |
| 展示素材 | **READY** |
| 安装说明 | **READY** |
| Privacy / Secret 扫描 | **READY** |
| 仓库体积 | **READY** |
| LICENSE / Artwork / BGM 权利 | **READY** |
| Release Notes | **READY** |
| Git 仓库初始化 | **READY** |
| git commit / push | **WAITING FOR USER ACTION** |
| 创建 tag `v1.0.0` | **WAITING FOR USER ACTION** |
| 创建 GitHub Release + 上传 MP4 | **WAITING FOR USER ACTION** |
| 真实阻塞项 | **无** |

---

## 1. README 完成度

| 项 | 状态 | 说明 |
|---|---|---|
| 中文主 README | **PASS** | `README.md` 已重写：Hero → 关于 → 功能 → 深与浅 → 角色 → 细节 → 安装 → 使用 → 兼容性 → 已知限制 → 项目结构 → 演示视频 → 致谢与授权 |
| 英文 README | **PASS** | `README_EN.md`，与中文逐节对应；顶部双向语言切换（中文页 → `README_EN.md`，英文页 → `README.md`） |
| 首屏有视觉 | **PASS** | KV 主视觉 + 三枚 badge，未堆砌 |
| 安装说明基于实证 | **PASS** | `dsh plugin --profile web add <path>` 来自 `dsh --help` 实测输出，非猜测 |
| 未编造 URL | **PASS** | 视频章节改为「去 Releases 页下载 v1.0.0 附件」的相对导航；未伪造 Bilibili / YouTube 地址 |
| 图片全部相对路径 | **PASS** | 两版 README 各 6 张图，全部为仓库内相对路径（`docs/images/`、`preview/`） |
| 兼容性表述克制 | **PASS** | 仅表述 DSH `0.2.0-rc.2` 为实测；`0.1.x` 与其他 RC 明确标注未验证 |
| Suno / MEDIA-CREDITS 链接 | **PASS** | Suno 作品链接正确，并指向 `docs/MEDIA-CREDITS.md` |
| 无本机绝对路径 | **PASS** | 全仓库扫描 0 命中 |
| 移除可疑外链 | **FIXED** | 原首屏指向 `github.com/deepseek-ai` 的项目链接语义不实，已改为纯文本 + 无链接 badge |

## 2. 截图与素材

| 项 | 状态 | 说明 |
|---|---|---|
| 预览图 FINAL | **PASS** | `preview/light.webp` / `dark.webp`，2026-10-04 按实装重出，私人文字已模糊 |
| KV 主视觉 | **PASS** | `FINAL-KV-styleframe-v3.png` → `docs/images/key-visual.webp`（137 KB） |
| 角色展示图 | **PASS** | `S3-MINI-CHARACTERS-styleframe-v2.png` → `docs/images/characters.webp`（145 KB） |
| 侧栏 Q 版实拍 | **PASS** | `tmp/chibi-ab/final-dark-sidebar.png`，已裁掉底部版本提示条 |
| 未使用禁用素材 | **PASS** | 未使用 superseded styleframe、old chibi、测试截图、debug UI |
| 尺寸控制 | **PASS** | 全部转 WebP，合计约 345 KB；未把 1.6 MB PNG 塞进 README |

## 3. 安装流程

| 项 | 状态 | 说明 |
|---|---|---|
| 安装命令 | **PASS** | `dsh plugin --profile web add <path>` 实证 |
| 放置位置说明 | **PASS** | README 明确「path 是包含 package.json 的那一层，不是仓库根」 |
| 是否需解压 / 编译 | **PASS** | 无需；预构建 bundle |
| 启用位置 | **PASS** | 设置 → 皮肤管理器（实测 `cordis.patch.yml` 有 `dsh-skin managed` 块） |
| 是否需重启 | **PASS** | 安装后重启一次；之后切换走热重载 |
| 恢复默认方式 | **PASS** | 皮肤管理器内关闭，effect 销毁自动还原 |

## 4. Privacy 扫描

| 项 | 状态 | 说明 |
|---|---|---|
| `client.js` 隐私扫描 | **PASS** | 0 命中（Windows 用户名 / 本机绝对路径 / QQ 号 / 手机号 / 邮箱均 0） |
| 配置文件扫描 | **PASS** | `skin.json` / `cordis.patch.yml` / `package.json` 均无私人路径 |
| README 旧版路径泄露 | **FIXED** | 源包 `README.md:97` 有一处指向私有工作区 patch 目录的绝对路径，公开版 README 已重写、不含该路径；该文件**未复制**到公开仓库 |
| 本文档自身的路径 | **FIXED** | 首版 CHECKLIST 引用了私有工作区绝对路径，已改为相对写法 |
| 截图私人信息 | **PASS** | 预览图私人文字已模糊；侧栏截图已裁掉提示条；KV 与角色图为纯美术图 |
| 未跟踪源码泄露 | **PASS** | patch 脚本与探针目录（`_asm` / `_v3probe` / `work\`）**均未复制** |

**复审记录**：15 个复制文件逐一 SHA-256 比对，与源包完全一致；复制后在公开仓库路径下
重跑一次全量隐私/secret 扫描，无新增命中。

## 5. Secrets 扫描

| 项 | 状态 | 说明 |
|---|---|---|
| API key / token | **PASS** | 全包 0 命中（唯一 `sk-` 匹配是 CSS 属性 `sk-position`，误报） |
| Cookie / Authorization | **PASS** | 0 命中 |
| 凭据文件 | **PASS** | 无 `.credentials.yaml`、无 `*.key`、无 `.env` |
| Session ID / 账号 ID | **PASS** | 0 命中 |

## 6. 仓库体积

| 项 | 状态 | 说明 |
|---|---|---|
| 皮肤包体积 | **PASS** | 15 文件 / 约 6.0 MB（含 5.29 MB 预构建 bundle） |
| 展示素材 | **PASS** | docs/images 约 345 KB |
| 总计 | **PASS** | 约 6.4 MB，远低于 GitHub 限制 |
| 宣传片未入仓 | **PASS** | 13.72 MB MP4 **未复制**；按 Release 附件分发 |
| 渲染中间产物未入仓 | **PASS** | `_asm` / `_v3probe` / `99_ARCHIVE` / `fonts` 均未复制 |

> ⚠️ **原始记忆仓库另有隐患**（不影响本仓库）：私有工作区的 `.git` 已达 818 MB，
> 含 electron.exe 233 MB、pnpm-native.exe 52 MB 与多份 25 MB 测试垃圾。
> 那是加密备份仓库的问题，不在本次发布范围内。

## 7. LICENSE 状态

| 项 | 状态 | 说明 |
|---|---|---|
| 代码许可 | **PASS** | MIT，Copyright (c) 2026 Small-tailqwq —— 你已确认维持现状 |
| 美术许可 | **PASS** | CC BY-NC-SA 4.0，`LICENSE-ARTWORK` 完整正文 |
| 分离声明 | **PASS** | `LICENSE` 顶部明确美术不在 MIT 范围内，含 AI 生成图 |
| README 一致 | **PASS** | README「致谢与授权」节与两份 LICENSE 口径一致 |

**不需要你再决定。**

## 8. Artwork 权利

| 项 | 状态 | 说明 |
|---|---|---|
| A 链（女仆工坊装饰） | **PASS** | 上善 → ZipZipPipe → Small-tailqwq 三创链完整，NOTICE 原样保留 |
| B 链（D 老师） | **PASS** | 原作者子午；公开授权「不商用即可」；仓库无变现入口 |
| AI 生成立绘 | **PASS** | 两张女版立绘标注为本项目 AI 重新制作，不属任何原作 |
| NOTICE 完整性 | **PASS** | 逐张来源、SHA-256、处理方式（抠图/缩放，未重绘）齐全 |
| 下架承诺 | **PASS** | README 与 NOTICE 均写明「权利人要求即下架」 |

**不需要你再决定**（沿用基座既有结论，未新增任何素材）。

## 9. BGM 版权

| 项 | 状态 | 说明 |
|---|---|---|
| BGM 来源 | **PASS** | `Bright Bell Motif (1).mp3` 由 **Suno AI** 生成 |
| 作品链接 | **PASS** | <https://suno.com/s/qNyElpaJUK0jTZ4Z>，已写入 README Credits 与 `docs/MEDIA-CREDITS.md` |
| 文件指纹 | **PASS** | SHA-256 `ec2e7bb5af07e077fa87aefc515f088b4a882d0658fbb3d0c50cdaedd096b978`（4,085,196 B） |
| 处理方式 | **PASS** | 仅剪辑区间 + 与旁白 ducking 混音，未改写、未重新生成 |
| 遗留说明 | 已记录 | MP3 内嵌 ID3 artist 为乱码 `zzzzzz12TSSEL`，故以 Suno 作品链接作为权威出处记录 |

**不需要你再决定。**

## 10. 视频状态

| 项 | 状态 | 说明 |
|---|---|---|
| 成片存在 | **PASS** | `MASTER-v6-FINAL-MIX-v3.mp4`，14,382,939 B |
| SHA-256 校验 | **PASS** | `f424f0382ae29e4c6d3f250bd5d195f28d0e3719cd36a0d4460dc43b749f010e`，与权威值逐字一致 |
| 帧数 | **PASS** | 1297 帧（`ffmpeg -c copy -f null` 实测） |
| 时长 | **PASS** | 43.23 s（容器），视频流 43.16 s |
| 分辨率 | **PASS** | 1920×1080 |
| 视频流 | **PASS** | H.264 High / yuv420p / 30 fps |
| 音频流 | **PASS** | AAC LC / 48 kHz / 立体声 / 197 kb/s |
| 解码完整性 | **PASS** | 全片解码无报错 |
| 未重新编码 | **PASS** | 仅做只读探测与 null 输出统计，未写出任何新文件 |
| 未内嵌仓库 | **PASS** | MP4 未复制进公开仓库；`.gitignore` 已有 `*.mp4` 规则 |
| 分发方式 | **READY** | README 中英双版均写明「在 v1.0.0 Release 的 Assets 里下载」并附规格与 SHA-256 |
| 实际上传到 GitHub | **WAITING FOR USER ACTION** | 需你授权后创建 Release 并上传 |

## 11. Release Notes

| 项 | 状态 | 说明 |
|---|---|---|
| 正文 | **READY** | `RELEASE-NOTES-v1.0.0.md`，已按 GitHub Release 正文重排 |
| 内容覆盖 | **PASS** | 首次发布、深浅双主题、双角色、四张立绘切换、左右独立翻转、Q 版侧栏、输入框与工作区主题化、移动端适配、DSH 0.2.0-rc.2 实测、安装方式、License 与署名提醒、演示视频 asset 信息 |
| 未写不存在功能 | **PASS** | 全部条目可在 `skin.json` / `client.js` / `NOTICE` 中找到依据 |
| 未实际发布 | **WAITING FOR USER ACTION** | 未创建 tag、未 push、未发布 Release —— 等你授权 |

## 12. Git 仓库状态

| 项 | 状态 | 说明 |
|---|---|---|
| 仓库位置 | **PASS** | 与私有工作区物理隔离 |
| 初始化 | **PASS** | 已 `git init`，分支 `main`（unborn，尚未有 commit） |
| commit / push | **WAITING FOR USER ACTION** | 未执行，等你授权 |
| 工作树状态 | **PASS** | 全部内容均为 untracked 待加入；无 staged、无已提交历史 |
| 待加入文件数 | **PASS** | 31 个 |
| 仓库体积 | **PASS** | 6.33 MB（`.git` 仅 0.03 MB） |
| 大文件 | **PASS** | 最大为 `lib/client.js` 5.29 MB（皮肤运行时本体，正常） |
| 视频误入 tracking | **PASS** | 未加入，`.gitignore` 有 `*.mp4` |
| 临时文件 / 缓存 | **PASS** | 无 `.tmp`/`.log`/`.cache`/`node_modules` |
| `git user.name` / `user.email` | **WAITING FOR USER ACTION** | 两者均为空，不擅自代填 |

## 13. `.gitignore` 规则验证

实测 `git check-ignore`：

| 路径 | 预期 | 结果 |
|---|---|---|
| `.../tmp/x.log` | 忽略 | ✅ 命中 `tmp/` |
| `.../a.mp4` | 忽略 | ✅ 命中 `*.mp4` |
| `.../node_modules/x.js` | 忽略 | ✅ 命中 `node_modules/` |
| `.../.env` | 忽略 | ✅ 命中 `.env` |
| `.../_asm/f.png` | 忽略 | ✅ 命中 `_asm/` |
| `.../preview/light.webp` | **保留** | ✅ 未被忽略 |
| `.../lib/client.js` | **保留** | ✅ 未被忽略 |
| `.../docs/images/key-visual.webp` | **保留** | ✅ 未被忽略 |
| `.../assets/icons/sleepy.ico` | **保留** | ✅ 未被忽略 |

正式资产没有被误伤。

---

## 阻塞项

**无。** 没有 BLOCKED 项。

早前记录的 BLOCKER-01（视频分发途径）已由你决定为 **GitHub Release asset**，
README 已按该方案改写，不再是阻塞项，转为等待你授权的 GitHub 侧操作。
BLOCKER-02（BGM 佐证）已由你提供的 Suno 链接消除。

---

## 等待你授权的操作

1. `git add` + `git commit`
2. 创建 tag `v1.0.0`
3. `git push` 到 GitHub 远端
4. 创建 GitHub Release `v1.0.0`，上传 `MASTER-v6-FINAL-MIX-v3.mp4`
5. 配置 `git user.name` / `git user.email`（我不代填）

---

## 提交方案（建议，待你确认）

| 项 | 建议值 |
|---|---|
| First commit message | `feat: DeepSea Workspace v1.0.0 — 鲸鱼娘 × D老师 的工作室` |
| 备用（更简） | `Initial commit: DeepSea Workspace v1.0.0` |
| Tag | `v1.0.0`（annotated：`git tag -a v1.0.0 -m "DeepSea Workspace v1.0.0"`） |
| Release title | `鲸鱼娘 × D老师 的工作室 · v1.0.0 — DeepSea Workspace` |
| Release body 来源 | 仓库内 `RELEASE-NOTES-v1.0.0.md` 全文，直接粘贴为 Release 正文 |
| Release asset | `MASTER-v6-FINAL-MIX-v3.mp4`（14,382,939 B，SHA-256 `f424f038…f010e`） |
| 建议勾选 | Release 创建后 README 里的「Releases 页面下载」导航即生效，无需再改文档 |

---

## 已解决（过程中发现并处理）

- 皮肤包原本**没有自己的 Git 仓库**，只在私有加密仓库里 → 已按你的要求新建公开总仓库
  下的 `deepsea-workspace/`
- 源 README 含一处私人绝对路径 → 公开版 README 已重写，不含该路径
- `skin.json` 的 `dshCompatibility` 写的是过时的 `0.1.5rc2` → 已更正为实测的 `0.2.0-rc.2`
- `package.json` 里 `repository` / `homepage` / `bugs` 指向的是**基座上游仓库**，
  发布后会误导 → 已移除，改为 `keywords`
- `package.json` 的 `description` 还在说「local fork」→ 已改为项目实际描述
- BGM 授权证据链薄弱 → 你已提供 Suno 作品链接 <https://suno.com/s/qNyElpaJUK0jTZ4Z>，
  已写入 README（中英）、`docs/MEDIA-CREDITS.md`；新增文件记录了文件指纹与处理方式
- 品牌名从「D 老师工作室 / D Studio」改为「鲸鱼娘 × D老师 的工作室 / DeepSea Workspace」
- 首屏指向 `github.com/deepseek-ai` 的链接语义不实 → 已移除，改为纯文本表述
- 设置路径写的是旧名「D 老师工作室」→ 已统一为「鲸鱼娘 × D老师 的工作室」

---

## 结论

**READY 的部分**：README、素材、安装说明、许可、Release Notes、仓库初始化 —— 全部完成，
仓库本身没有任何待修缺陷。

**WAITING FOR USER ACTION 的部分**：commit / tag / push / GitHub Release / 上传 MP4，
以及 `git user.name`、`git user.email` 的填写。

一次授权即可完成全流程。在你确认之前，我没有执行任何写操作之外的 Git 命令。
