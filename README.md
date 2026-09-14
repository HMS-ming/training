<div align="center">
# ☀️ 追光空间站 · 培训手册
### *LightChaser Space Station · Training Guide*
---
🌌 *这里，不只是知识的传递，更是火种的传承。*
💡 *Every page carries light, passed down from one generation of seekers to the next.*
---
在这份文档里，你将：
 学习 **3D视觉、电子信息与前沿技术** 的核心内容
 继承 **前辈的经验与智慧**
 书写 **属于你自己的逐光篇章**
🚀 让我们一同启程，在知识的星海中逐光前行！
</div>

---

## 📑 目录

培训分**季**进行，每一期都可按需扩展新的学习主题与交付任务。

### 第一期（进行中 · 面向大一新生，零基础可入）

> 定位：从零开始、手把手入门嵌入式 / 视觉 / 电子信息。无 0 章、共 **9 章**。
>
> 🔴**核心必学（本次培训重点，需交付成果）**：`1 C/C++` → `2 大模型(DeepSeek / IDE / Skill)` → `3 Git`
>
> 🟢**进阶选学（自主探索，视兴趣深入）**：`4 Python` → `5 Linux` → `6 嵌入式` → `7 ROS` → `8 机器学习` → `9 图像处理`

- [`第一期/第一期.md`](第一期/第一期.md) —— 培训总纲（目录 + 学习建议）
- [`第一期/第一期教程.md`](第一期/第一期教程.md) —— 教程索引：9 章学习路线表 + 验收清单
- [`第一期/教程/`](第一期/教程/) —— 各章独立教程文档（`01~09`）
- [`第一期/learningMd/`](第一期/learningMd/) —— 工具入门文档
  - [`Git.md`](第一期/learningMd/Git.md) —— GitHub 从零开始
  - [`MinicondaUse.md`](第一期/learningMd/MinicondaUse.md) —— Miniconda 环境管理
  - [`cv_conda.md`](第一期/learningMd/cv_conda.md) —— conda 建 OpenCV 图像处理环境
  - [`ordinaryEnv.md`](第一期/learningMd/ordinaryEnv.md) —— venv 虚拟环境管理

## 🚩 怎么用这份手册

1. **先看总纲** [`第一期.md`](第一期/第一期.md)，了解有哪些方向，确定自己想深入的方向。
2. **跟随教程** 从 [`第一期教程.md`](第一期/第一期教程.md)（教程索引）定位到第 1 章 C/C++ 入手，再沿"下一章"依序推进，而不是只看不练。
3. **工具不会就查** `learningMd/` 里的入门文档都是"照着做"式的命令清单。
4. **完成即交付** 每章末尾按验收标准把成果提交到 Git（如 push 到你 fork 的仓库），才算完成一个任务。
5. **有疑惑大胆问** 用它推荐的方式向 ChatGPT / 学长提问，学会"提问"本身也是本手册的必修课。

## 🏗️ 目录结构说明
- 每**一期**独立一个文件夹，内含：总纲（`xx期.md`）、实操教程（`xx期教程.md`）、工具文档（`learningMd/`）。
- 修改前统一做**带时间戳的版本备份**（`backup_时间戳/`），并写 `CHANGELOG.txt` 说明改动，方便回退。