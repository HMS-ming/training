# 使用 Miniconda 入门指南

> Miniconda 是一个轻量的 Python 环境管理工具，内置 `conda` 命令，可帮助你为不同项目创建互相隔离的 Python 环境。

---

## miniconda / conda 与 venv 的区别

| 对比项 | venv（内置虚拟环境） | Miniconda (conda) |
| --- | --- | --- |
| 隔离范围 | 仅隔离 Python 库 | 可管理 Python 解释器、C/C++ 库、CUDA 等系统级依赖 |
| 是否需安装 | Python 自带 | 需单独安装 |
| 适用场景 | 轻量、项目内即可 | 需要 GPU/多版本 Python 等更复杂的项目 |

> 同一项目里 venv 和 conda 通常二选一；涉及 OpenCV/CUDA/PyTorch 这类重依赖时，推荐用 conda。

---

## 安装 Miniconda（Linux）

```bash
# 下载安装脚本
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh

# 安装（一路确认即可）
bash Miniconda3-latest-Linux-x86_64.sh
```

> Windows 用户请到 [Miniconda 官网](https://docs.conda.io/en/latest/miniconda.html) 下载对应的 exe 安装包。安装后需重启终端让 `conda` 生效。

---

## 常用命令

```bash
# 确认是否成功安装
conda --version

# 查看已创建的环境
conda env list

# 创建环境（指定 Python 版本）
conda create --name condaEnv python=3.10

# 激活环境
conda activate condaEnv

# 在环境里安装需要的库
conda install numpy pandas matplotlib

# 关闭环境
conda deactivate
```

---

## 小结

- 建环境：`conda create -n <名> python=<版本>`
- 进入环境：`conda activate <名>`
- 装依赖：`conda install <包名>`
- 退出环境：`conda deactivate`

> 其他环境管理（venv）与图像处理环境（OpenCV）可分别参考同目录下的 [`ordinaryEnv.md`](ordinaryEnv.md)、[`cv_conda.md`](cv_conda.md)。