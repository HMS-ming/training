# 7. 🟢 ROS 基础 🤖
**🧭 方向：电控（机器人控制）**

> ✨ [← 返回教程索引](../第一期教程.md)

**目标：** 认识 ROS（机器人操作系统），跑通内置的 turtle 小乌龟例子，并自己写一个"发布/订阅"的小程序，理解机器人通信的基本套路。
**前置：** 第 1 章 C/Python 基础 ＋ 第 4 章 Linux（必须，ROS 跑在 Linux 上）。
**预计：** 1~2 周（环境安装可能占去一两天，别急）。

---

## 7.1 ROS 是什么

ROS 不是操作系统，而是一个**机器人软件框架**：它让机器人身上每个模块（摄像头、底盘、舵机、导航）用统一的"话题"互相发消息，像"微信群"一样协作。

- **节点（Node）**：一个独立运行的程序（比如"摄像头节点"）。
- **话题（Topic）**：节点之间通信的"频道"，一个节点发、多个节点订阅。
- **消息（Message）**：话题里发的数据格式。
- **主节点（roscore / ROS2 的 daemon）**：负责帮节点互相找到对方。

## 7.2 装环境（最重要的一步）

- 推荐 **Ubuntu** 系统（可装在双系统 / 虚拟机 / 或 WSL2）。
- 版本：经典选 **ROS1 Noetic**（教程多、问得多）；追求新推荐 **ROS2 Humble**。
- 安装脚本网上按官方教程一步步来，装完先跑通 `roscore` 或 `ros2 --version`。
- ⚠️ 环境安装报错很常见，**把报错贴给 DeepSeek**（核心必学第 2 章练过的技能），一般都能解决。

## 7.3 跑通第一个例子：小乌龟

ROS 自带的 turtle 例子是最佳入门：

```bash
# ROS1
roscore &
rosrun turtlesim turtlesim_node
rosrun turtlesim turtle_teleop_key   # 用键盘控制小乌龟移动
```
看！小乌龟能跟着你的方向键移动。这说明"一个节点发布速度指令，另一个节点接收并让乌龟动"已经跑通。

## 7.4 自己写一个发布/订阅节点

我们用 Python 写两个节点，一个发布数字、一个接收打印：

```python
# talker.py —— 发布端
# （在 ROS1: rospy；ROS2: rclpy，API 略有不同，这里以 ROS2 示意）
import rclpy
from rclpy.node import Node
from std_msgs.msg import Int32

rclpy.init()
node = Node("talker")
pub = node.create_publisher(Int32, "count", 10)

import time
n = 0
while rclpy.ok():
    n += 1
    pub.publish(Int32(data=n))      # 往话题 count 发一个整数
    print(f"发布 {n}")
    time.sleep(1)
```

```python
# listener.py —— 订阅端
import rclpy
from rclpy.node import Node
from std_msgs.msg import Int32

def cb(msg):
    print(f"收到 {msg.data}")

rclpy.init()
node = Node("listener")
sub = node.create_subscription(Int32, "count", cb, 10)
rclpy.spin(node)
```
运行两个终端各跑一个节点，你会看到数据从发射端→话题→接收端。这就是 ROS 通信的最小单元，理解它，机器人各个模块怎么协作就懂了。

## 7.5 动手练习清单

- [ ] 跑通小乌龟例子（键盘控制乌龟移动）
- [ ] 自己各写一个 talker / listener，能互发消息
- [ ] 改一版：把消息从数字改成字符串（比如发一句"Hello LightChaser"）
- [ ] 用 `rostopic` / `rqt_graph` 看看节点和话题的关系图
- [ ] 记录环境安装踩过的坑到你的 `debug 笔记`

## 7.6 本章验收（交付）

- 小乌龟例子跑通
- talker/listener 程序运行成功，把运行截图 + 代码提交到你的 Git 仓库

---

## 🎬 推荐视频（B 站）

- [古月居 · ROS 2 入门 21 讲](https://www.bilibili.com/video/BV16B4y1Q7jQ/) · 82.9万播放 · 21集 · 入门路径讲解清晰
- [鱼香 ROS · 动手学 ROS 2](https://www.bilibili.com/video/BV1gr4y1Q7j5/) · 65.5万播放 · 偏实操，配合代码跟练

---

*上一章：[6. 嵌入式基础](06_嵌入式基础.md) · 下一章：[8. 图像处理基础](08_图像处理基础.md) →*