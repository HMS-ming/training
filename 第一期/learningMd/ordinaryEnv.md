# Python 虚拟环境（venv）

> 虚拟环境的原理是**隔离**：每个项目各自独立的、互不干扰的依赖环境。

例如：项目 A 需要库 v1.0，项目 B 需要 v2.0——用虚拟环境可以让两者各用各的，互不冲突。

---

## 何时需要

- 多个项目对同一库的版本要求不同
- 不想把依赖装进系统全局环境
- 部署时希望环境干净、可复现（配合 `requirements.txt` 更好）

---

## 基础用法（Windows / Linux）

```bash
# 创建环境（会在当前目录生成 myenv 文件夹）
python -m venv myenv

# 进入环境
# Windows (PowerShell)：
myenv\Scripts\Activate.ps1
# Linux / macOS：
source ./myenv/bin/activate

# 退出环境
deactivate
```

---

## 进阶建议

- 安装项目依赖后用 `pip freeze > requirements.txt` 导出依赖清单，方便复现环境
- 新机器搭建时用 `pip install -r requirements.txt` 一键重建

> 相比 venv，需要管理 CUDA / 多版本 Python 等重依赖时，建议改用 Miniconda，见同目录 [`MinicondaUse.md`](MinicondaUse.md)。