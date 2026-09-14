# 3. 🔴 Git 基础 📘

> ✨ [← 返回教程索引](../第一期教程.md)

**目标：** 注册 GitHub，学会用 Git 管理代码版本并与团队协作。
**预计：** 1 天左右。这是整个培训的"交付手段"——前两章的成果都要靠 Git 提交。

---

## 3.0 Git 是什么（先懂概念）

Git 好比**给代码玩"存档"**：你在写第 1 章的 C 程序时，随时能用 Git 存一个"存档点"，存下的每个版本都能回退、能对比、能分享给别人。

- **仓库（repository）**：一个项目 + 它的所有历史记录。
- **提交（commit）**：一次"存档"。
- **推送（push）/ 拉取（pull）**：把本地版本"上传/下载"到网上（GitHub）。

> 一句话：**改了代码 → `git add`（放进暂存区）→ `git commit`（存一个存档）→ `git push`（传到 GitHub）。**

---

## 3.1 准备：注册 GitHub + 安装 Git

1. 注册并登录 [GitHub](https://github.com/)。
2. 在电脑上安装 Git（`git-scm.com` 下载，Windows 一路 Next 即可）。
3. 打开终端验证：`git --version`，能看到版本号即成功。

## 3.2 首次身份配置（**不做会报错**）

第一次用 Git，先告诉它"你是谁"，否则 `commit` 会报错：

```bash
git config --global user.name "你的名字"
git config --global user.email "你的邮箱@example.com"
```

（邮箱用你注册 GitHub 的那个即可。设置后只管一次，以后不用再配。）

## 3.3 第一个仓库：把第 1 章代码提交并推送

1. 在 GitHub 右上角 **+ → New repository**，命名 `my-c-practice`，勾选 **Add a README file**，创建。
2. 把仓库 **Clone** 到本地（记住那串 `https://github.com/你的用户名/my-c-practice.git`）：
   ```bash
   git clone https://github.com/你的用户名/my-c-practice.git
   cd my-c-practice
   ```
3. 把你在第 1 章写的 `c_practice` 文件夹整个复制进 `my-c-practice/`。
4. 修改仓库里的 `README.md`，写下你的名字和一句话简介（比如"我正在写一个计算器"）。
5. 提交并推送：
   ```bash
   git add .                     # ① 把所有改动放进"暂存区"
   git commit -m "第一次提交：C 语言练习"   # ② 存一个存档
   git push                      # ③ 上传到 GitHub
   ```
6. 刷新 GitHub 页面，看到代码上传成功，第一份"存档"就做好了。

## 3.4 三个必须懂的小阶段

| 阶段 | 一句人话 | 常用命令 |
|------|---------|----------|
| 工作区（Working） | 你正在改的文件 | `git status` 看改了啥 |
| 暂存区（Staging） | 准备存进存档的改动 | `git add 文件名` |
| 本地仓库（Local）→ 远程（Remote） | 存档→ 上传 | `git commit` / `git push` |

练习时的正常节奏：改代码 → `git status` 看变化 → `git add .` → `git commit` →（要上传就）`git push`。

## 3.5 最常用命令速查

```bash
git status              # 当前改了哪些文件
git log --oneline       # 看提交历史（一次一行）
git diff                # 看具体改了哪些内容
git add .               # 把所有改动放进暂存区
git commit -m "说明"    # 存一个存档
git push                # 上传到 GitHub
git pull                # 从 GitHub 拉取最新（多人协作时用）
```

## 3.6 常见报错与解决（三大坑）

- **`fatal: not a git repository`（找不到仓库）** → 你不在一个 Git 仓库里。先进到 `my-c-practice` 目录，或先 `git init`。
- **`Please tell me who you are`（不知道怎么署名）** → 没做 3.2 的身份配置，补上 `user.name` / `user.email` 即可。
- **`remote: Permission to ... denied`（push 被拒）** → 你 push 到了一个你没权限的仓库。确认是在**自己的仓库**里；如果是别人/团队的仓库，需要管理员给你权限，或用你自己的 fork。
  - 另：用 HTTPS 推送时，GitHub 现在**不认密码**，要用**个人访问令牌（Personal Access Token）**当密码，或用 SSH 方式。

> 记住一句口诀：**先看 `git status`，再决定下一步**——它能告诉你现在在哪、缺哪步。

## 3.7 动手练习与自检

- [ ] `git --version` 有输出（Git 装好了）
- [ ] 完成 3.2 身份配置
- [ ] `my-c-practice` 仓库能看到第 1 章的 C 代码（已 push 到 GitHub）
- [ ] 修改一行代码 → 再 `commit` 一次 → `git log --oneline` 能看到至少 **2 条**提交记录
- [ ] 换一台设备（或重新 clone）能把这个仓库拉下来（证明真的"存了档"）

> 从此刻起：**每完成一个练习就提交一次**。到学期末，你的提交历史 + 仓库链接就是你最硬核的成长档案，也是本次培训的交付物。

---

## ✅ 本章验收（交付物）

- 你的 GitHub 仓库里，有第 1 章练习的代码 + 多次提交记录
- 能把仓库链接（`https://github.com/你的用户名/my-c-practice`）发给学长 / 放进团队仓库

---

*上一章：[2. 大模型基础](02_大模型基础.md) · 下一章：[4. Linux 基础](04_Linux基础.md) →*