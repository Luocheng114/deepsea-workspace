# 目录与产物

```text
GitHubPublic/
├─ README.md                    总仓库说明（GitHub 首页展示这个）
├─ .github/                     总仓库元数据
└─ deepsea-workspace/           项目：鲸鱼娘 × D老师 的工作室
   └─ skin-d-atelier/           DSH 皮肤包本体，仓库以这个目录为根
      ├─ README.md              中文主文档
      ├─ README_EN.md           英文版
      ├─ RELEASE-NOTES-v1.0.0.md
      ├─ PUBLIC-RELEASE-CHECKLIST.md
      ├─ lib/                   预构建皮肤运行时
      ├─ preview/               深/浅预览图
      ├─ assets/icons/          应用图标
      ├─ docs/images/           README 展示素材
      ├─ skin.json              皮肤元数据
      ├─ cordis.patch.yml       插件注册补丁
      ├─ LICENSE / LICENSE-ARTWORK / NOTICE
      └─ .github/               项目级 issue / PR 模板
```

## 当前状态

- 已完成 README 重写、素材整理、隐私与 secret 扫描
- 尚未 `git init`、尚未 commit、尚未 push
- 演示视频待定公开分发方式

## 新增项目时的检查清单

1. 扫一遍绝对路径、真实姓名、账号 ID
2. 扫一遍 token / key / cookie / 凭据文件
3. 截图里的私人文字模糊掉，提示条裁掉
4. 大文件确认是否该走 Release 附件而不是进仓库
5. `.gitignore` 只写明确路径，不用 `*.png` 这类通配误伤正式资产
