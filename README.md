# GAU-Lab-Report
### 甘肃农业大学本科生实验报告 LaTeX 模板，基于 XeLaTeX，支持变量集中管理。

[![LaTeX](https://img.shields.io/badge/LaTeX-XeLaTeX-blue)](https://www.latex-project.org/)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)
[![OverLeaf](https://img.shields.io/badge/OverLeaf-Compatible-success)](https://www.overleaf.com/)
[![CTeX](https://img.shields.io/badge/CTeX-2.0%2B-orange)](http://www.ctex.org/)

> 告别 Word 文档的排版折磨。

## 特性

- **高保真版式** —— 精准还原封面、装订线、页眉上下双线、右侧批阅意见栏，边框坐标逐像素实测复刻
- **变量集中管理（核心亮点）** —— 所有个人信息、课程信息集中在 `information.tex`，填一次即可让封面、页眉、信息栏自动同步，无需在多处重复粘贴
- **一键编译** —— 内置 `latexmkrc` 直接出 PDF
- **OverLeaf 友好** —— 上传即用，无需本地安装 TeX
- **章节可插拔** —— `sections/` 下自由增删，`main.tex` 一行 `\input` 接入

## 快速开始

### 方式一：OverLeaf 在线编辑（推荐）

1. 在 OverLeaf 中 **New Project → Upload Project**，上传本仓库的 `.zip` 压缩包
2. 左上角 **Menu → Compiler**，**务必选择 `XeLaTeX`**
3. 点击 **Recompile** 即可生成 PDF

### 方式二：OverLeaf 链接直达
直接点击下方链接，即可在 Overleaf 中一键克隆（Copy Project）本模板：

 **[点击这里在 Overleaf 中打开](https://cn.overleaf.com/project/6ad83cfcc639ee8038cba7ba/share#13627223a9643ee83332ac0a2a27f196a0cccffc6ac21a7f)**

> **注意**：打开链接后，点击页面左上角的 `Copy Project` 即可生成你自己的副本，然后请确保在 `Menu -> Compiler` 中选择 **XeLaTeX**。


### 方式三：本地编译

推荐使用 `latexmk`（已在 `latexmkrc` 中配置好 XeLaTeX）：

```bash
latexmk main.tex
```

或直接使用 `xelatex` 编译两次（生成目录 / 交叉引用）：

```bash
xelatex main.tex
xelatex main.tex
```

> 模板首行已声明 `% !TeX program = xelatex`，绝大多数编辑器会自动识别编译器。

## 如何填写你的信息？

### 第一步：修改 `information.tex`（核心）

这是本模板最关键的文件，所有可变内容都在这里。打开后你会看到：

```tex
% ==================== 课 程 信 息 ====================
\newcommand{\infoExpNo}{实验三}             % 实验编号
\newcommand{\infoExpTitle}{结构化软件设计}    % 实验题目
\newcommand{\infoCourse}{软件工程与项目管理}  % 课程名称
\newcommand{\infoExperimentTime}{2026-09-01} % 实验日期
\newcommand{\infoTeacher}{张老师}           % 指导教师
\newcommand{\infoHours}{16}                % 总学时
\newcommand{\infoGroup}{3}                 % 小组编号

% ==================== 个 人 信 息 ====================
\newcommand{\infoName}{李四}                % 姓名
\newcommand{\infoStudentId}{20240001}       % 学号
\newcommand{\infoCollege}{信息科学技术学院}  % 学院
\newcommand{\infoClass}{24计算机二班}        % 班级全称（封面用）
\newcommand{\infoStudentCount}{60}          % 班级人数
\newcommand{\infoYearStart}{26}             % 学年起始（20xx 的 xx）
\newcommand{\infoYearEnd}{27}               % 学年结束
\newcommand{\infoSemester}{1}               % 学期
\newcommand{\infoMajor}{计算机}             % 专业
\newcommand{\infoGrade}{24}                 % 年级
\newcommand{\infoClassNo}{2}                % 班级序号
\newcommand{\infoScore}{}                   % 成绩（留空，由教师填写）
```

把「李四」「20240001」等换成你自己的真实信息，编译后**封面、页眉、第 2 页信息栏会自动同步更新**，无需改动其他文件。

### 第二步：在 `sections/` 中写正文

在各个 `.tex` 文件中填写实验内容，把 `%补充实际内容即可` 注释替换为正文：

```tex
\ExpSection{一、实验目的}

在这里写实验目的……支持 LaTeX 任意语法：列表、代码块、图片、公式……
```

### 第三步：编译

```bash
latexmk main.tex
```

生成 `main.pdf`，收工。

## 目录结构


```text
├── main.tex                            # 主控文件：组织封面与各章节
├── information.tex                     # ⭐ 信息配置文件：姓名、学号、学院等全在这里填
├── preamble.tex                        # 宏包、版面参数与页面边框样式定义
├── cover.tex                           # 第 1 页：封面
├── latexmkrc                           # 编译配置文件（强制 XeLaTeX）
├── sections/                           # 正文目录
│   ├── 01-mubiao.tex                   # 一、实验目的
│   ├── 02-yiqi.tex                     # 二、实验仪器设备
│   ├── 03-neirong.tex                  # 三、实验内容及步骤
│   ├── 04-guocheng.tex                 # 四、实验过程
│   └── 05-zongjie.tex                  # 五、实验总结
└── media/                              # 图片目录
    └── The_format_requires/
        └── gyau-logo.png               # 校徽图片
```

## 常用命令

| 命令 | 说明 | 示例 |
| :--- | :--- | :--- |
| `\ExpSection{标题}` | 生成实验报告小节标题（粗体四号） | `\ExpSection{一、实验目的}` |

> 插图请使用标准 LaTeX 语法 `\includegraphics[]{...}`，图片放入 `media/` 目录即可。

## 版式说明

| 页码 | 内容 | 版式特征 |
|:----:|------|----------|
| **第 1 页** | 封面 | 校徽 + 「本科生实验报告」大标题 + 信息表格 + 「教务处制」 |
| **第 2 页** | 信息栏 + 题目 + 正文 | 页眉校徽 + 学院名 + 上下双线 + 左侧装订线 + 右侧批阅意见栏 + 三行信息栏 |
| **第 3 页+** | 续写正文 | 同第 2 页边框，去掉信息栏，顶部双线上移至页眉下方 |

## 环境依赖

| 项目 | 要求 |
|------|------|
| TeX 发行版 | TeX Live 2020+ / MikTeX / MacTeX |
| 编译引擎 | **XeLaTeX**（必须，不支持 pdfLaTeX） |
| 宏包 | `geometry` `graphicx` `eso-pic` `tikz` `enumitem` `array` `ctex` |
| 字体 | `fontset=fandol`（发行版自带，免安装） |

## 注意事项

1. **必须使用 XeLaTeX 编译** —— 不支持 pdfLaTeX（中文与字体处理依赖 `ctex` 与 `xeCJK`）。
2. **加载顺序勿动** —— `information.tex` 必须在 `preamble.tex` 之前 `\input`（`main.tex` 已按此顺序写好，请勿调换），否则封面 / 页眉引用的 `\infoXxx` 宏会未定义。
3. **字体依赖** —— 默认使用 `Fandol` 字体集（TeX Live 发行版自带），无需额外安装。
4. **图片格式** —— 推荐使用 `.png` 或 `.pdf` 格式，XeLaTeX 不支持 `.eps`。
5. **替换校徽** —— 请将新图片命名为 `gyau-logo.png` 放入 `media/The_format_requires/` 目录，或修改 `cover.tex` 与 `preamble.tex` 中的图片路径。
6. **带圈数字** —— ①②③… 已通过 `\xeCJKDeclareCharClass` 归入中文字体，可直接使用。

## 开源协议

本项目采用 **MIT License** 开源。
