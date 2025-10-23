# CLAUDE.md

本文件为 Claude Code (claude.ai/code) 在此代码仓库中工作时提供指导。

## 仓库概览

这是一个研究生（徐欣东）的个人求职资料仓库，包含：
- 多种格式的简历文件（LaTeX、Word、PDF）
- 用于简历文档处理的 Python 工具
- 量化金融面试准备的 LeetCode 练习题
- 量化金融学习资料

## 目录结构

```
.
├── resume.tex                    # 主要的 LaTeX 简历源文件
├── CV-*.docx/pdf                 # 各种格式的简历文件
├── Quant/                        # 量化金融面试准备材料
│   ├── leetcode/                 # LeetCode 问题解答（Python）
│   └── *.pdf                     # 量化面试指南
└── stage 2024/                   # 简历处理工具和模板
    ├── translate_cv.py           # 英译中简历翻译器
    ├── create_word_cv.py         # Word 文档简历生成器
    └── read_docx.py              # Word 文档内容读取器
```

## 简历文件使用方法

### LaTeX 简历 (resume.tex)

这是主要的英文简历模板，使用自定义 LaTeX 格式。

**编译 LaTeX 简历：**
```bash
pdflatex resume.tex
```

**模板结构：**
- 使用自定义命令：`\resumeSubheading`、`\resumeProjectHeading`、`\resumeItem`
- 主要章节：教育背景、工作经验、项目经历、技术技能、领导力
- ATS 友好格式（使用 `\pdfgentounicode=1`）

### Word 文档处理

仓库在 `stage 2024/` 目录中包含三个用于简历文档处理的 Python 工具：

**读取 Word 文档内容：**
```bash
cd "stage 2024"
python read_docx.py
```

**将简历从英文翻译为中文：**
```bash
cd "stage 2024"
python translate_cv.py
```
- 使用基于字典的翻译方法，依赖 `python-docx` 库
- 保留格式（粗体、斜体、下划线、对齐方式）
- 输入：`CV-XU-Xindong-en.docx`
- 输出：`CV-XU-Xindong-cn.docx`

**生成格式化的中文简历：**
```bash
cd "stage 2024"
python create_word_cv.py
```
- 从 `CV-XU-Xindong-cn.docx.txt` 读取内容
- 输出格式化的 Word 文档

**所需依赖：**
```bash
pip install python-docx
```

## LeetCode 练习 (Quant/)

`Quant/leetcode/` 目录包含量化金融面试中常见的动态规划问题的 Python 解答：

- `1.py` - 爬楼梯（斐波那契数列）
- `62.py`、`63.py`、`64.py` - 网格路径问题
- `300.py` - 最长递增子序列
- `740.py`、`746.py` - 打家劫舍变体
- `712.py` - 两个字符串的最小 ASCII 删除和
- `1027.py` - 最长等差数列
- `coinflip.py` - 概率计算问题

**运行任意解答：**
```bash
python Quant/leetcode/<problem_number>.py
```

## 架构说明

### 简历处理流程

Word 文档处理工具形成一个处理流程：
1. **read_docx.py** - 检查文档结构和格式
2. **translate_cv.py** - 翻译内容的同时保留样式
3. **create_word_cv.py** - 从文本生成格式化的输出

所有工具都使用 `python-docx` 库，并保留以下格式：
- 段落格式（对齐方式、缩进、间距）
- 文本格式（粗体、斜体、下划线、字号）
- 表格结构

### LaTeX 简历架构

LaTeX 模板使用层次化的命令结构：
- `\resumeSubHeadingListStart/End` - 章节容器
- `\resumeSubheading{title}{date}{subtitle}{location}` - 用于工作经历/教育背景
- `\resumeProjectHeading{name}{date}` - 用于项目经历
- `\resumeItemListStart/End` - 项目符号列表容器
- `\resumeItem{text}` - 单个项目符号要点

## 关键约定

1. **文件命名**：简历文件遵循 `CV-XU-Xindong-{language}-{date}.{ext}` 模式
2. **中文翻译**：使用简单的字典翻译，需要人工审核以确保准确性
3. **LaTeX 工作流程**：编辑 `resume.tex`，使用 `pdflatex` 编译
4. **Python 脚本**：设计为在其所在目录中运行
