# PYD Analyzer

**中文** | [English](#introduction)

---

## 简介

PYD Analyzer 是一款针对 Cython 编译的 Python 扩展模块（.pyd / .so）的逆向分析工具。它能够解析 IDA Pro 导出的 C 伪代码，自动识别原始 Python 函数、简化编译器生成的样板代码，并生成可读的分析报告。

## 功能

- 从 IDA 伪代码中识别原始 Python 函数名、源文件及行号
- 识别 Python C API 调用并添加注释
- 提取并解析模块常量池（字符串、整数）
- 构建 Python 函数间的调用关系图
- 自动去除引用计数、异常处理、IDA 注释等样板代码
- 识别 Cython 内部辅助函数（`__Pyx_*`）

## 使用方法

### 1. 准备输入文件

在 IDA Pro 中打开 .pyd 文件，使用 Hex-Rays 反编译后，导出全部伪代码为 `.c` 文件。

### 2. 运行工具

| 文件 | 说明 |
|------|------|
| `pyd_analyzer_zh.exe` | 中文界面 |
| `pyd_analyzer_en.exe` | English UI |

工具启动后会显示交互式菜单：

```
========================================
   PYD 逆向分析工具 - 交互式控制台
========================================

  [1] 完整分析 - 分析整个伪代码文件并生成报告
  [2] 提取函数 - 选择并提取单个Python函数
  [3] 函数列表 - 列出文件中所有Python函数
  [4] 常量池   - 查看文件的常量池
  [0] 退出
```

### 3. 分析报告内容

完整分析报告包含以下部分：

- **模块统计** — 函数总数、Python 函数数、Helper 函数数、常量数
- **Python 函数列表** — 按源文件分组，含行号信息
- **调用关系** — Python 函数之间的调用链
- **常量池** — 所有提取到的字符串和整数常量
- **简化后的伪代码** — 去除样板代码、添加 API 注释后的可读代码
- **Helper 函数列表** — 已识别的 Cython 内部函数

## 系统要求

- Windows 10 / 11（x64）
- 输入文件：IDA Pro + Hex-Rays 导出的 C 伪代码

## 常见问题

**Q: 支持哪些 Python 版本编译的 pyd？**
A: 主要针对 Python 3.x + Cython 编译的模块优化，理论上支持所有使用标准 Python C API 的扩展。

**Q: 分析结果不完整？**
A: 确保在 IDA 中导出的是完整的伪代码文件（包含所有函数），而非单个函数的反编译结果。

---

**[中文](#简介)** | English

---

## Introduction

PYD Analyzer is a reverse engineering tool for Cython-compiled Python extension modules (.pyd / .so). It parses C pseudocode exported from IDA Pro, automatically identifies original Python functions, simplifies compiler-generated boilerplate, and produces readable analysis reports.

## Features

- Recover original Python function names, source files, and line numbers from IDA pseudocode
- Annotate Python C API calls with descriptions
- Extract and resolve module constant pools (strings, integers)
- Build call graphs between Python functions
- Strip reference counting, exception handling, IDA comments, and other boilerplate
- Identify Cython internal helper functions (`__Pyx_*`)

## Usage

### 1. Prepare Input

Open the .pyd file in IDA Pro, decompile with Hex-Rays, and export all pseudocode to a `.c` file.

### 2. Run the Tool

| File | Description |
|------|-------------|
| `pyd_analyzer_zh.exe` | Chinese UI |
| `pyd_analyzer_en.exe` | English UI |

An interactive menu will appear:

```
========================================
    PYD Reverse Analysis Tool - CLI
========================================

  [1] Full Analysis  - Analyze entire pseudocode file
  [2] Extract Func   - Extract a single Python function
  [3] Function List  - List all Python functions
  [4] Constant Pool  - View the constant pool
  [0] Exit
```

### 3. Report Contents

A full analysis report includes:

- **Module Statistics** — Total functions, Python functions, helpers, constants
- **Python Function List** — Grouped by source file with line numbers
- **Call Relations** — Call chains between Python functions
- **Constant Pool** — All extracted string and integer constants
- **Simplified Pseudocode** — Cleaned code with API annotations
- **Helper Functions** — Identified Cython internal functions

## Requirements

- Windows 10 / 11 (x64)
- Input: C pseudocode exported from IDA Pro + Hex-Rays

## FAQ

**Q: Which Python versions are supported?**
A: Optimized for Python 3.x + Cython compiled modules. Should work with any extension using the standard Python C API.

**Q: Incomplete results?**
A: Make sure you exported the complete pseudocode file from IDA (all functions), not just a single function's decompilation.
