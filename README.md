# math-travel

本科数学笔记：高等代数 / 数学分析 / 复分析 / 解析几何。用 XeLaTeX + `ctex` 排版。

📄 **最新 PDF**：[Releases](https://github.com/Mifansans/math-travel/releases/latest)

## 结构

    main.tex                  导言区（宏包、定理环境、记号）与 \include
    chapters/*.tex            分科正文
    diary/                    独立编译的日记，按月 \input{entries/YYYY-MM}
    images/                   插图
    .github/workflows/        每次推送编译 PDF，打 tag 时发 Release

## 构建

需要 TeX Live（含 `ctex`、`fandol` 字体）与 `latexmk`：

```bash
latexmk -xelatex main.tex          # 主书 → main.pdf
cd diary && latexmk -xelatex diary.tex
```

## 约定

- 定理、引理、定义等环境共用编号，按节递增。
- 交叉引用一律 `\label` + `\ref`，不手写编号。
- 正文中文，公式用 `$...$` 或 `\[...\]`。
- 成品 PDF 不进版本库：推送后由 Actions 编译，README 的链接指向最新 Release。

## License

文字内容采用 [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/)：可自由阅读、转载、改编，需署名且不得用于商业用途。

发现错误欢迎开 Issue。
