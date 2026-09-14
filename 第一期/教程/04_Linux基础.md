# 4. 🟢 Linux 基础 🐧
**🌐 方向：公共基础（嵌入式 / ROS / 服务器都会用到）**

> ✨ [← 返回教程索引](../第一期教程.md)

**目标：** 认识 Linux，会常用命令行，能做"装软件、看文件、跑程序"这几件事。
**定位：** 对大一新生，先"认识会用"，不要求一次学完；为第 6/7 章（嵌入式 / ROS）做准备。
**预计：** 1~2 周（每天 10 分钟练几个命令即可）。

---

## 4.1 先搞懂：Linux 是什么、为什么学

- **Linux = 一个免费开源的"操作系统"**，和 Windows、macOS 平级。你的手机安卓、大多数服务器、机器人的主控，底层都是 Linux。
- 为什么嵌入式 / ROS 方向必学？因为 **STM32 开发工具链、ROS、树莓派/工控机，很多只在 Linux 上跑**。
- 你操作它主要靠**终端（Terminal）**打命令，而不是点鼠标。听起来吓人，其实常用命令就那十来个，练熟就行。

## 4.2 准备一个 Linux 环境（三选一，推荐第一种）

1. **虚拟机（最推荐新手）**：装 VirtualBox 或 VMware，然后下载 Ubuntu 镜像装进去。Windows 里开一个"独立的电脑"，随便折腾不弄坏本机。
2. **双系统**：电脑上同时装 Windows + Ubuntu，开机选。性能最好，但装系统有风险，建议后面熟了再弄。
3. **云主机**：花几块钱/免费的云服务器，用 `ssh` 远程登录玩命令。

> 新手最容易卡在这步。**卡住了就把安装报错贴给 DeepSeek**（第 2 章练过的技能），一般 10 分钟能解决。

## 4.3 打开终端，学会"我是谁、我在哪"

Ubuntu 里按 `Ctrl+Alt+T` 打开终端。下面的命令挨个敲，观察输出：

```bash
pwd        # 我在哪个目录（Print Working Directory）
whoami     # 我是哪个用户
ls         # 当前目录里有什么（list）
ls -l      # 更详细地列出来（权限、大小、时间）
ls -a      # 连藏起来的文件也显示（. 开头的）
cd /home   # 去 /home 目录（change directory）
cd ~       # 回到自己的家目录
cd ..      # 回到上一级目录
```

> 记不住不要紧：`cd`、`ls`、`pwd` 三个先练熟，后面全是在这三个基础上转悠。

## 4.4 和文件夹 / 文件打交道（最常用）

```bash
mkdir myproj        # 新建文件夹（make directory）
cd myproj           # 进到这个文件夹
touch hello.txt     # 新建一个空文件 touch
nano hello.txt      # 用 nano 编辑器打开它，写点东西，Ctrl+O 保存、Ctrl+X 退出
cat hello.txt       # 把文件内容打印到屏幕（concatenate）
cp hello.txt copy.txt   # 复制（copy）
mv copy.txt a.txt   # 改名（move）
rm a.txt            # 删除（remove）⚠️ 真的删，垃圾桶都没有，删前想清楚
rm -r myproj2       # 递归删除整个文件夹，慎用！
```

> 快速记忆：**增 `mkdir/touch`、看 `ls/cat`、移 `cp/mv`、删 `rm`**。

## 4.5 权限：文件前面那串 `-rw-r--r--` 是啥

`ls -l` 输出的开头一列（如 `-rw-r--r--`）就是权限：

- 第 1 位 `-`/`d`：是普通文件还是文件夹（directory）
- 后 9 位分三组 = `所有者 / 同组 / 其他人`，每组 `rwx` = **读/写/执行**
- 改权限用 `chmod`：`chmod +x run.sh` 给脚本加"可执行"

```bash
chmod +x hello.py     # 让 hello.py 可以被直接执行
./hello.py            # 用 ./ 执行当前目录的程序
```

> 后面跑 ROS 脚本、启动机器人程序时，"权限不足"十有八九是这里，加个 `chmod +x` 就好。

## 4.6 装软件：包管理器 apt

Linux 装软件不用去网页下载，一条命令即可：

```bash
sudo apt update        # 先更新软件源列表（需要管理员权限 sudo）
sudo apt install -y build-essential   # 装编译工具链（含 gcc，呼应第 1 章）
sudo apt install -y git               # 装 git
sudo apt remove git    # 卸载
```

> `sudo` = 以管理员身份执行（要输密码）。`apt install 软件名` 基本够用。

## 4.7 跑程序 + 看懂报错（先养好这个习惯）

```bash
gcc hello.c -o hello   # 编译（第 1 章学过）
./hello                # 运行
echo $?                # 看上一个命令退出码：0 成功，非 0 出错
```

- **报错不可怕**，把整段红字复制下来贴给 DeepSeek，就能定位。
- 常用排查三连：`pwd`（路径对不对）→ `ls`（文件在不在）→ `sudo`（权限够不够）。

## 4.8 进阶必会：管道、重定向、进程（后面 ROS 用得上）

```bash
ls | grep hello        # 管道：把 ls 的输出再筛一遍，只留含 hello 的行
ls > list.txt          # 重定向：把输出存进文件（覆盖）
echo "hi" >> log.txt   # 追加写进文件（不覆盖）
ps aux                 # 查看正在运行的进程（进程=正在跑的程序）
kill 12345             # 结束进程号 12345
# 在 ROS/机器人里，进程经常要在后台跑，加个 & 放到后台：
ros2 run turtlesim turtlesim_node &
```

> 这几条先"见过"，第 7 章 ROS 用到了再回头细看。

## 4.9 动手练习清单

- [ ] 装好一个 Ubuntu 环境（虚拟机即可），能打开终端
- [ ] 用 `pwd`、`cd`、`ls`、`mkdir`、`touch`、`cat` 走一遍目录
- [ ] 用 `nano` 写一个文件并用 `cat` 读出来
- [ ] 用 `cp` / `mv` / `rm` 复制、改名、删除一个文件
- [ ] 用 `sudo apt install` 装一个软件（比如装 git）
- [ ] 用 `gcc` 编译第 1 章写的 hello.c 并在 Linux 上跑出来
- [ ] （进阶）用 `ls | grep` 筛选文件夹里的文件

## 4.10 本章验收（交付）

- 能说明白 `ls`、`cd`、`pwd`、`mkdir`、`chmod` 分别干嘛
- 在 Linux 上成功编译并运行过 C 程序（第 1 章回顾）
- 把常用命令速查记进你的 `学习笔记.md`，提交到 Git

> 别贪多，Linux 是"用熟"不是"背完"。后面 ROS 章节会强制用到，那时你会感谢现在打的基础。

---

## 🎬 推荐视频（B 站）

- [韩顺平 · Linux 从零入门](https://www.bilibili.com/video/BV1Sv411r7vd/) · 494万播放 · 153集 · 菜鸟教程经典，跟着过一遍常用命令
- 完整版更长、想系统补底层（系统管理 / Vim）的，B 站搜"Linux 基础 韩顺平 // 尚硅谷 Linux"按播放量排序挑一套

> 对新生：Linux 一开始会不习惯，别慌，先每天用 10 分钟练几个命令，慢慢就熟了。

---

*上一章：[3. Git 基础](03_Git基础.md) · 下一章：[5. Python 基础](05_Python基础.md) →*