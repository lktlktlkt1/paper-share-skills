# XMU Paper Share Skills

面向 Codex 的精简论文分享技能包：把 **arXiv 论文 TeX 源码**整理成
**厦门大学主题的中文 Beamer 讲解 PDF**。

这是 [yhbcode000/paper-share-skills](https://github.com/yhbcode000/paper-share-skills)
的个人 Fork，并与
[lktlktlkt1/xmu-slides-template](https://github.com/lktlktlkt1/xmu-slides-template)
配套使用。

## 当前范围

```text
arXiv 链接 / DOI / ID
        ↓
下载并解压 TeX 源码
        ↓
读取正文、公式、表格与原图
        ↓
生成 XMU 中文 Beamer
        ↓
XeLaTeX 编译与逐页检查
        ↓
最终讲解 PDF
```

本 Fork 保留两个技能：

| 技能 | 作用 |
|:---|:---|
| `paper-download-arxiv-paper-source` | 下载并安全解压 arXiv e-print 源码 |
| `paper-to-beamer` | 生成、编译并检查 XMU 中文 Beamer PDF |

不包含 MinerU、任意 PDF 解析、PPTX、配音、视频、封面、B 站上传或发布流程！详情请见原仓库。
如果 arXiv 只提供 PDF 而没有 TeX 源码，流程会明确停止。

## 安装到 Codex

### 方式一：随模板仓库一起克隆

```bash
git clone --recurse-submodules \
  https://github.com/lktlktlkt1/xmu-slides-template.git \
  ~/xmu-slides-template

mkdir -p ~/.codex/skills
cp -R ~/xmu-slides-template/skills/paper-download-arxiv-paper-source ~/.codex/skills/
cp -R ~/xmu-slides-template/skills/paper-to-beamer ~/.codex/skills/
```

### 方式二：直接安装本仓库

```bash
git clone https://github.com/lktlktlkt1/paper-share-skills.git \
  ~/paper-share-skills

mkdir -p ~/.codex/skills
cp -R ~/paper-share-skills/paper-download-arxiv-paper-source ~/.codex/skills/
cp -R ~/paper-share-skills/paper-to-beamer ~/.codex/skills/
```

复制后重新打开 Codex 或新建对话，使 Codex 重新发现技能。安装只需要做一次；
之后无需把 `SKILL.md` 内容粘贴到对话中。

## 使用

在任意新的 Codex 对话中发送：

```text
使用 $paper-to-beamer，把下面的 arXiv 论文制作成 XMU 风格的中文组会讲解 PDF，
最终 PDF 放到桌面：
https://arxiv.org/abs/2502.12110
```

也可以使用 arXiv DOI 或裸 ID：

```text
使用 $paper-to-beamer，制作中文讲解 PDF 并放到桌面：
https://doi.org/10.48550/arXiv.2502.12110
```

`paper-to-beamer` 会先调用 `paper-download-arxiv-paper-source`，无需分别下达两次命令。

## 依赖

- Python 3.9 或更高版本；
- TeX Live 或 MiKTeX；
- XeLaTeX 与 `latexmk`；
- Poppler 的 `pdftoppm`，用于逐页渲染检查；
- 可访问 arXiv 的网络。

模板优先从 `~/xmu-slides-template` 读取；如果该目录不存在，技能会使用仓库内置的
XMU 模板快照。

## 仓库结构

```text
.
├── paper-download-arxiv-paper-source/
│   ├── SKILL.md
│   └── scripts/download_source.py
├── paper-to-beamer/
│   ├── SKILL.md
│   ├── scripts/copy_template.py
│   └── templates/xmu/
├── LICENSE
└── README.md
```

## 更新

已直接克隆本仓库时：

```bash
git -C ~/paper-share-skills pull --ff-only
cp -R ~/paper-share-skills/paper-download-arxiv-paper-source ~/.codex/skills/
cp -R ~/paper-share-skills/paper-to-beamer ~/.codex/skills/
```

通过模板子模块使用时：

```bash
git -C ~/xmu-slides-template pull --ff-only
git -C ~/xmu-slides-template submodule update --init --recursive
```

## 许可与来源

保留原项目的 [LICENSE](LICENSE) 与许可补充条款。原始技能仓库由
[yhbcode000](https://github.com/yhbcode000) 创建；本 Fork 由
[lktlktlkt1](https://github.com/lktlktlkt1) 精简并改造为 XMU PDF 工作流。
