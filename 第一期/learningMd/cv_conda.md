# 使用 conda 创建 OpenCV（Linux）环境

> 在 Linux 下用 conda 搭一个带 OpenCV 的图像处理环境。

```bash
# 创建并激活环境
conda create --name cvenv python=3.10
conda activate cvenv

# 安装 OpenCV 及相关图像库
conda install -c conda-forge opencv pillow scikit-image matplotlib

# 可选：深度视觉需要的框架
# conda install pytorch torchvision torchaudio -c pytorch
# conda install tensorflow

# 进入 Python 交互环境验证
python
```

```python
import cv2
import numpy as np

# 打印 OpenCV 版本
print(f"OpenCV version: {cv2.__version__}")

# 创建一个三通道空白图，验证 NumPy 与 OpenCV 是否正常联动
blank_image = np.zeros((100, 200, 3), dtype=np.uint8)
print(f"Successfully created a blank image with shape: {blank_image.shape}")
```

> 如果只做基础的图像读取/显示，也可以直接用 `pip install opencv-python`，无需 conda（见进度总纲的图像处理一章）。