<div align="center">
<h1>ReCopilot: A Reverse Engineering Copilot for Boosting Binary Analysis with Decompiler</h1>
<p>
<a href="https://www.python.org/downloads/"><img src="https://img.shields.io/badge/python-3.8+-blue.svg" alt="Python 3.8+"></a>
<a href="https://hex-rays.com/ida-pro/"><img src="https://img.shields.io/badge/IDA%20Pro-9.0+-orange.svg" alt="IDA Pro"></a>
<a href="https://tqgpt.qianxin.com/recopilot/"><img src="https://img.shields.io/badge/🌐-Website-green.svg" alt="Website"></a>
<a href="https://arxiv.org/abs/2505.16366"><img src="https://img.shields.io/badge/arXiv-2505.16366-b31b1b.svg" alt="arXiv"></a>
<a href="LICENSE"><img src="https://img.shields.io/badge/license-GPLv3-blue.svg" alt="License"></a>
<br>
<a href="README_zh.md">[简体中文]</a>
<a href="README.md">[English]</a>
</p>
</div>

ReCopilot 由奇安信技术研究院星图实验室研发，是一个基于人工智能的二进制程序分析辅助系统，利用人工智能增强逆向工程工作流程。它具备强大的二进制代码推理能力和同源代码搜索功能。ReCopilot 可以智能恢复函数名、变量名和类型信息，生成代码文档，并提供基于语义的二进制代码同源搜索。

![demo](demo.gif)

## 功能特性

**ReCopilot 二进制代码推理分析**

- **符号与类型恢复**：基于大语言模型智能推断剥离的函数名、变量名等语义符号，支持源代码级的变量类型和结构体定义恢复。
- **语义分析和代码文档**：自动化二进制代码语义分析，执行基于上下文的函数行为推理，以函数文档和内联注释的形式辅助代码理解。
- **反编译增强**：使用大语言模型增强反编译结果，提升伪代码可读性。
- **结果审查和应用**：支持人工审查模型预测结果，对结果进行修改或选择性应用。预测的符号信息和类型（包括结构体类型）可以应用到二进制代码中并自动执行传播。
- **通用模型支持**：支持动态切换模型，以利用快速发展的先进大语言模型的能力。

**SimAI 二进制代码同源搜索**

- **函数级二进制代码同源搜索**：基于语义搜索二进制函数的同源函数，搜索结果包含同源函数的源代码、伪代码、项目名、版本号、相似度分数等信息。
- **自动化批量搜索**：支持对当前二进制文件中的多个函数进行自动化批量搜索。
- **搜索结果详情审查与应用**：搜索结果包含同源函数的细粒度信息，如函数名、参数类型、参数名等，供用户选择性应用到被分析的二进制代码中。

## 安装指南

### 1. 环境要求

- IDA Pro 9.0+
- Python 3.8～3.13

### 2. 安装插件

将插件文件放置到 IDA Pro 插件目录：

```bash
$IDA_INSTALL_DIR/plugins/
    |--recopilot
            |--recopilot.py
            |--ida-plugin.json
            ...
```

### 3. 安装依赖

在 `recopilot` 目录下使用命令 `pip install -r requirements.txt` 安装所需的 Python 库。

> **注意**：请确保安装到 IDAPython 环境中。使用 `$IDA_INSTALL_DIR/idapyswitch` 检查 IDA 当前使用的 Python 环境。

### 4. 验证安装

打开 IDA Pro 并加载一个二进制文件。观察 Output 窗口，如果出现以下输出，则表示插件安装成功：

```plaintext
==== ReCopilot Plugin Init ====
[👏] ReCopilot init success
```

### 5. 基础配置

打开 IDA Pro → Edit → ReCopilot-Settings 对话框。在 ReCopilot Settings 标签页中，配置 ReCopilot 推理模型 API：

```
Model Name: recopilot-v0.1-beta-dpo
Base URL: https://tqgpt.qianxin.com/recopilot/v1
API Key: 从官网个人中心获取 Token
```

在 SimAI Settings 标签页中，配置搜索模型 API：

```
Base URL: https://tqgpt.qianxin.com/simai/analyze
API Key: 同上
```

更多配置选项和使用详情，请访问我们的[帮助文档](https://tqgpt.qianxin.com/recopilot/)。

## 许可证与数据隐私政策

本仓库使用 GPLv3 许可证。

ReCopilot 默认不会收集任何使用数据。只有当您在插件设置中手动开启 "Feedback Enable" 选项时，才会启用数据收集。启用后，收集的数据包括系统信息、模型交互和分析结果，用于帮助改进我们的模型和插件性能。我们致力于保护您的隐私，并实施了严格的数据保护措施。

有关数据收集实践的详细信息，请阅读我们的[隐私政策](PRIVACY_POLICY/PRIVACY_POLICY_zh.md)。

## 引用

如果您在研究或项目中使用了 ReCopilot，欢迎引用我们的技术报告：

```bibtex
@misc{ReCopilot2025,
      title={ReCopilot: Reverse Engineering Copilot in Binary Analysis}, 
      author={Guoqiang Chen and Huiqi Sun and Daguang Liu and Zhiqi Wang and Qiang Wang and Bin Yin and Lu Liu and Lingyun Ying},
      year={2025},
      eprint={2505.16366},
      archivePrefix={arXiv},
      primaryClass={cs.CR},
      url={https://arxiv.org/abs/2505.16366}, 
}
```
