# math-travel · 数学笔记

中文数学笔记，XeLaTeX + `ctex` 排版。2026-11 重启后的空骨架，正文由作者手写。

## 构建

```
latexmk -xelatex main.tex            # 主书 → main.pdf
cd diary; latexmk -xelatex diary.tex # 日记 → diary.pdf
latexmk -C                           # 清理（注意会连 pdf 一起删）
```

改完 `.tex` 至少编译一次，`main.log` 里不能有以 `!` 开头的错误。

## 结构

| 文件 | 作用 |
| --- | --- |
| `main.tex` | 导言区（宏包、定理环境、记号）+ `\include` |
| `chapters/advanced-algebra.tex` | 高等代数 |
| `chapters/analysis.tex` | 数学分析 |
| `chapters/complex-analysis.tex` | 复分析 |
| `chapters/geometry.tex` | 解析几何 |
| `diary/diary.tex` | 独立编译的日记，按月 `\input{entries/YYYY-MM}` |
| `images/` | 插图 |

## 写作约定

- 定理环境共用编号（按 section）：`theorem` `lemma` `corollary` `definition` `example` `proposition` `remark`。
- 记号：`\K \Z \Q \R \C`、`\rank`。
- 节用 `\subsection`，内部细分用 `\subsubsection*`；交叉引用一律 `\label` + `\ref`。
- 正文中文，公式 `$...$` / `\[...\]`。
- 新增宏包前先确认必要，不要重复加载。

## 其他

- 扫描件、草稿放仓库外（如 `D:\math-scratch\`），不提交。
- 成品 PDF 由 CI 编译并发 Release，不进 git。

## 读文件规则（省 token）

- 先 `grep` 定位标题/关键词拿行号，再用 read 的 `offset`/`limit` 只读那一节，不要整章通读。
- 不要读 `main.pdf`、`*.xdv`、`*.log`、`*.aux`、`*.toc`、`*.fls`。
