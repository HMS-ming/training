# 从零开始的 GitHub 学习

> 使用 GitHub 可以完成版本管理和团队协作。下面是新手到入门的一条完整路径。

---

## 🚀 第一步：GitHub 是什么？

- **远程存储（remote）**：把代码和文档放到云端，不怕本机损坏，方便部署项目
- **团队协作**：多人分工、代码合并、任务拆分、规范流程
- **版本回退**：改错了可以随时回到之前的任意提交版本

---

## 🐯 第二步：注册登录

1. 访问 [GitHub 官网](https://github.com/)
2. 点击 **Sign up** 注册
3. 验证邮箱、设置密码
4. 进入邮箱点击激活链接

---

## 🍁 第三步：创建仓库（Repository）

仓库就是一个云端代码文件夹。

1. 登录 GitHub
2. 右上角点击 **+ → New repository**
3. 填写仓库名（如 `hello-world`）
4. 勾选 **Add a README file**
5. 点击 **Create repository**

---

## 🎂 第四步：认识基础工具

1. **VS Code**：代码编辑器
   - 下载：[VS Code 官网](https://code.visualstudio.com/)
2. **Git**：版本管理工具，安装后建议先验证
   - 下载：[Git 官网](https://git-scm.com/downloads)
   - 验证安装：运行 `git --version`
3. **GitHub CLI**（可选）：用命令行直接管理 GitHub

安装后，先配置你的身份：

```bash
git config --global user.name "你的名字"
git config --global user.email "你的邮箱"
```

---

## 🆎 第五步：把仓库下载到本地

1. 进入你的仓库主页，点击 **Clone**（或 **Code**）复制链接
2. 在命令行运行：

```bash
git clone https://github.com/你的用户名/仓库名.git
```

3. 用 VS Code 打开这个文件夹，就可以开始改代码了。

> 更完整的 VS Code + Git 可视化操作可参考：[CSDN 教程](https://blog.csdn.net/Er_Studying_Bai/article/details/128088429)

---

## 🛰️ 第六步：修改代码并提交

1. 打开 `README.md`
2. 写一段项目说明（**别写姓名、班级、学号等个人信息**，仓库是公开的），例如：

```markdown
# 我的第一个项目

这是我放在 GitHub 上的第一个项目，用来练习 C 语言。
```

3. 保存文件
4. 提交并推送：

```bash
git add .
git commit -m "第一次提交"
git push
```

回到 GitHub 仓库主页，就能看到提交已同步成功。

---

## 💎 进阶：日常更新流程

1. 更新或新增文件
2. 提交：`git commit -m "本次改了什么"`（**提交信息一定要写清楚**）
3. 推送：`git push`
4. **注意**：提交后要确认是否真的推送成功、状态是否干净（可用 `git status` 检查）

---

## 🏁 学习验证

- [ ] 注册 GitHub 账户
- [ ] 创建仓库
- [ ] 掌握基础（VS Code + Git）
- [ ] 把仓库克隆到本地
- [ ] 更新并提交文件
- [ ] 推送回 GitHub

完成后，你就可以在 GitHub 上建立自己的仓库，留下属于你的第一篇代码了！