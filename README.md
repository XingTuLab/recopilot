<div align="center">
<h1>ReCopilot: A Reverse Engineering Copilot for Boosting Binary Analysis with Decompiler</h1>
<p>
<a href="https://www.python.org/downloads/"><img src="https://img.shields.io/badge/python-3.8+-blue.svg" alt="Python 3.8+"></a>
<a href="https://hex-rays.com/ida-pro/"><img src="https://img.shields.io/badge/IDA%20Pro-9.0+-orange.svg" alt="IDA Pro"></a>
<a href="https://tqgpt.qianxin.com/recopilot/"><img src="https://img.shields.io/badge/🌐-Website-black.svg" alt="Website"></a>
<a href="https://arxiv.org/abs/2505.16366"><img src="https://img.shields.io/badge/arXiv-2505.16366-b31b1b.svg" alt="arXiv"></a>
<a href="LICENSE"><img src="https://img.shields.io/badge/license-GPLv3-blue.svg" alt="License"></a>
<br>
<a href="README_zh.md">[简体中文]</a>
<a href="README.md">[English]</a>
</p>
</div>

ReCopilot is developed by the XingTu Lab of QI-ANXIN Technology Research Institute. It is an AI-powered binary program analysis assistant that leverages artificial intelligence to enhance reverse engineering workflows. It features powerful binary code reasoning capabilities and homologous code search functionality. ReCopilot can intelligently recover function names, variable names, and type information, generate code documentation, and provide semantic-based binary code homology search.

![demo](demo.gif)

## Features

**ReCopilot Binary Code Reasoning and Analysis**

- **Symbol and Type Recovery**: Intelligently infer stripped function names, variable names, and other semantic symbols using large language models. Supports source-level variable type and struct definition recovery.
- **Semantic Analysis and Code Documentation**: Automated binary code semantic analysis with context-based function behavior inference, assisting code comprehension through function documentation and inline comments.
- **Decompilation Enhancement**: Use large language models to enhance decompilation results and improve pseudocode readability.
- **Result Review and Application**: Supports manual review of model predictions, allowing modifications or selective application of results. Predicted symbol information and types (including struct types) can be applied to binary code with automatic propagation.
- **General Model Support**: Supports dynamic model switching to leverage the performance of rapidly evolving advanced large language models.

**SimAI Binary Code Homology Search**

- **Function-level Binary Code Homology Search**: Search for homologous functions of binary functions based on semantics. Search results include source code, pseudocode, project name, version number, similarity score, and other information.
- **Automated Batch Search**: Supports automated batch searching of multiple functions in the current binary file.
- **Search Result Details Inspection and Application**: Search results contain fine-grained information of homologous functions, such as function names, parameter types, and parameter names, for users to selectively apply to the analyzed binary code.

## Installation

### 1. Environment Requirements

- IDA Pro 9.0+
- Python 3.8～3.13

### 2. Install Plugin

Place the plugin files in the IDA Pro plugins directory:

```bash
$IDA_INSTALL_DIR/plugins/
    |--recopilot
            |--recopilot.py
            |--ida-plugin.json
            ...
```

### 3. Install Dependencies

Use the command `pip install -r requirements.txt` in the `recopilot` directory to install the required Python libraries.

> **Note**: Please ensure installation to the IDAPython environment. Use `$IDA_INSTALL_DIR/idapyswitch` to check the Python environment currently used by IDA.

### 4. Verify Installation

Open IDA Pro and load a binary file. Observe the Output window. If the following output appears, the plugin installation was successful:

```plaintext
==== ReCopilot Plugin Init ====
[👏] ReCopilot init success
```

### 5. Basic Configuration

Open IDA Pro → Edit → ReCopilot-Settings dialog. In the ReCopilot Settings tab, configure the ReCopilot reasoning model API:

```
Model Name: recopilot-v0.1-beta-dpo
Base URL: https://tqgpt.qianxin.com/recopilot/v1
API Key: Obtain Token from Personal Center on our website
```

In the SimAI Settings tab, configure the search model API:

```
Base URL: https://tqgpt.qianxin.com/simai/analyze
API Key: Same as above
```

Obtain API Key from Personal Center on our website (**ENGLISH VERSION IS ONLINE**): [https://tqgpt.qianxin.com/recopilot/](https://tqgpt.qianxin.com/recopilot/)

For more configuration options and usage details, please visit our [Documentation](https://tqgpt.qianxin.com/recopilot/).

## License and Data Privacy Policy

This repository is licensed under the GPLv3 License.

ReCopilot does not collect any usage data by default. Data collection is only enabled when you manually turn on the "Feedback Enable" option in the plugin settings. When enabled, collected data includes system information, model interactions, and analysis results to help improve our models and plugin performance. We are committed to protecting your privacy and have implemented strict data protection measures.

For detailed information about our data collection practices, please read our [Privacy Policy](PRIVACY_POLICY/PRIVACY_POLICY.md).

## Citation

If you find our work helpful, feel free to give us a cite.

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
