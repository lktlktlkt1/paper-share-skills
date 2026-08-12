# 贡献指南

本 Fork 只维护 `arXiv TeX → XMU Beamer → PDF`。请不要在此仓库加入
MinerU、PPTX、配音、视频、封面或上传功能；这些能力应在独立分支或独立仓库中维护。

## 技能约定

- 每个技能目录必须包含 `SKILL.md`。
- YAML frontmatter 只包含 `name` 和 `description`。
- `name` 必须与技能目录名一致。
- 不提交个人绝对路径、凭据、Cookie、虚拟环境和编译缓存。
- 不重新引入 SUSTech、Bilibili 或旧推广文字。

## 提交前检查

```bash
python3 -m py_compile \
  paper-download-arxiv-paper-source/scripts/download_source.py \
  paper-to-beamer/scripts/copy_template.py

rg -n "SUSTech|sustech|哔哩哔哩|Bilibili" \
  paper-download-arxiv-paper-source paper-to-beamer

git status --short
```

还应使用 `skill-creator` 的 `quick_validate.py` 验证两个技能，并编译一次复制出的
XMU 示例模板。
