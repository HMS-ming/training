# 5. 🟢 Python 基础 🐍
**🌐 方向：公共基础（机器学习 / 图像处理 / 脚本都会用到）**

> ✨ [← 返回教程索引](../第一期教程.md)

**目标：** 熟悉 Python 语法，能看懂、能改、能写小脚本，为第 8/9 章（图像 / 机器学习）打底。
**预计：** 1~2 周。学完第 1 章 C 再来会觉得轻松很多——语法更友好、写得更快。
**前置：** 第 1 章（有了编程思维）＋ 第 4 章（懂的用命令行）。

---

## 5.1 Python 是"更省事"的编程语言

和第 1 章的 C 比，Python 有四个"省事"：
- **不用编译**：写完直接运行，报错就在那一行告诉你。
- **不写类型**：不用声明 `int/float`，写数字就自动是数字。
- **不操心内存**：早就不需要手动 malloc/free（第 1 章那个），自动管理。
- **现成库多**：要做图像、机器学习、爬虫，`pip install` 一条命令就有一套现成工具。

> 一句话：**C 让你懂原理（所以当地基），Python 让你出活快（所以当工具）。**

## 5.2 装环境（二选一）

- **推荐：Miniconda 环境**（可以不同项目用不同版本，防打架）——步骤见 [`learningMd/MinicondaUse.md`](../learningMd/MinicondaUse.md)。
- **省事：直接装 Python**：到 python.org 下载安装，勾选"Add to PATH"，装完在终端敲 `python --version` 看到版本号即成功。
- 别忘记给 VS Code 装 **Python 扩展**，这样写代码才有提示 / 高亮。

## 5.3 第一个程序：Hello World

新建文件 `hello.py`，写一行，然后在终端运行：

```bash
print("Hello, LightChaser!")
```

```bash
python hello.py      # 运行它
```

**应该看到：** `Hello, LightChaser!`
> 和 C 比：不用 include、不用 main、不用分号。所以我说"更省事"。

## 5.4 变量、类型、输入输出

```python
name = input("你的名字：")     # 从键盘读一串文字
age = 20                     # 数字自动就是数字，不用写 int
height = 1.75                # 小数

print(f"你好，{name}！你 {age} 岁。")   # f-string：f 大括号里放变量，超好用
print("你的身高是", height, "米")      # 也支持逗号拼
```

- `input()` 读进来的一定是**字符串**，想当数字用得转：`int(input("…"))`
- `f"..."` 是格式化字符串，是 Python 打印变量的首选写法。

## 5.5 条件、循环（和第 1 章对照着看）

```python
score = int(input("请输入分数："))

if score >= 60:
    print("及格了！")
elif score >= 90:         # Python 的"else if"写作 elif
    print("优秀！")
else:
    print("没及格，加油")

for i in range(1, 6):     # 循环 1~5（range 到 6 但不含 6）
    print(i)
```

> ⚠️ 和 C 最大的不同：**Python 用"缩进"表示层级，不是大括号 `{}`**。该退格没退格就报错 `IndentationError`。这是新手最常见的坑。

## 5.6 列表（装一列数据）、字典（装"键值对"）

```python
# 列表 list ≈ C 的数组，但能存不同类型，还能长能短
fruits = ["苹果", "香蕉", "菠萝"]
print(fruits[0])           # 苹果（下标也是从 0 开始）
fruits.append("西瓜")      # 末尾加一个
for f in fruits:
    print(f"我喜欢 {f}")

# 字典 dict = 一个"名字: 值"的搭对
stu = {"name": "小明", "age": 20, "gender": "男"}
print(stu["name"])         # 小明
stu["hobby"] = "编程"      # 加一对
```

做图像 / 机器学习时，**列表装样本、字典装属性**就是最常见的用法。

## 5.7 函数 + 导入"别人的代码"（库）

```python
def add(a, b):            # 定义函数 def
    return a + b

print(add(3, 4))          # 7
```

```python
import math               # 导入标准库 math
print(math.sqrt(9))       # 3.0

import random
print(random.randint(1, 100))    # 1~100 随机整数
```

## 5.8 读写文件（很常用）

```python
# 写
with open("note.txt", "w", encoding="utf-8") as f:
    f.write("第一天打卡\n")

# 读
with open("note.txt", "r", encoding="utf-8") as f:
    print(f.read())
```

> `with ... as` 自动负责关闭文件，不用手动关，养成习惯。

## 5.9 装第三方库：pip（后面章节全靠这个）

```bash
pip install numpy            # 科学计算
pip install opencv-python    # 图像（第 8 章）
pip install scikit-learn     # 机器学习（第 9 章）
pip list                     # 看你已经装了哪些
```

> 想一次装一批，写成 `requirements.txt`，然后 `pip install -r requirements.txt`。物理装错环境？回看 5.2 用 conda 装隔离环境。

## 5.10 让 DeepSeek 当你的 Python 老师

- 把报错整段贴给它 → 立刻定位。
- "这份代码逐行解释" → 秒懂。
- "帮我把这个功能用 Python 实现" → 抄下来改改就能跑。
- 学完这一章，第 8/9 章就是"用 Python 调库"了，那时会频繁用 AI。

## 5.11 动手练习清单

- [ ] 跑通 Hello World
- [ ] 写一个"输入分数 → 判断及格与否"的程序
- [ ] 用 `for` 循环打印九九乘法表
- [ ] 建一个 `stu` 字典存自己的信息，打印出来
- [ ] 定义一个函数，统计一个列表里偶数的个数
- [ ] 用 `open()` 把今天的打卡写进文件，再读出来
- [ ] 用 `pip install numpy` 装好，`import numpy` 不报错

## 5.12 本章验收（交付）

- 上面练习全部跑通，能解释 `for`、`if`、`def`、`import` 分别干嘛
- 用 Python 写过至少一个"读输入 → 处理 → 输出/存文件"的小程序
- 把代码 + 结果提交到你的 Git 仓库（复用第 3 章）

---

## 🎬 推荐视频（B 站）

- [小甲鱼 · Python 零基础入门](https://www.bilibili.com/video/BV1xs411Q799/) · 1078万播放 · 风格幽默，适合零基础
- 想要更系统、跟练多的：B 站搜"黑马程序员 Python 600集"（600多集大合集，按播放量排序第一的就是）

> 给新生：学 Python 不要"看完才动手"，边看边敲，跑通一个小功能就是一次胜利。

---

*上一章：[4. Linux 基础](04_Linux基础.md) · 下一章：[6. 嵌入式基础](06_嵌入式基础.md) →*