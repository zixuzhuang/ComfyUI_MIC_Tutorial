# ComfyUI 环境部署与安装

请在 Linux 环境下进行配置和部署

## 1. Python 镜像配置

推荐使用 SJTU 的 pypi 和 conda 源以加速下载过程，上海地区默认可以跑满带宽

```
pip config set global.index-url https://mirror.sjtu.edu.cn/pypi/web/simple
```

编辑 ~/.condarc

```
default_channels:
  - https://mirror.sjtu.edu.cn/anaconda/pkgs/r
  - https://mirror.sjtu.edu.cn/anaconda/pkgs/main
custom_channels:
  conda-forge: https://mirror.sjtu.edu.cn/anaconda/cloud/
  pytorch: https://mirror.sjtu.edu.cn/anaconda/cloud/
channels:
  - defaults
```

参考链接：

[pypi/web/simple] https://mirror.sjtu.edu.cn/docs/pypi/web/simple

[anaconda] https://mirror.sjtu.edu.cn/docs/anaconda

## 2. Python 环境配置

推荐创建一个虚拟环境，使用 python3.10 和 CUDA11.8

```
conda create --name comfytest
conda activate comfytest
conda install python==3.10
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
```

## 3. ComfyUI 安装

```
git clone https://github.com/comfyanonymous/ComfyUI.git
cd ComfyUI
pip install -r requirements
```

参考链接：

[ComfyUI] https://github.com/comfyanonymous/ComfyUI

## 4. 常用插件下载

ComfyUI 支持插件节点，所有插件都以 git 项目的形式保留在"./custom_nodes"目录下，这里下载一些常用的节点

```
git clone https://github.com/ltdrdata/ComfyUI-Manager.git
git clone https://github.com/Fannovel16/comfyui_controlnet_aux.git
git clone https://github.com/cubiq/ComfyUI_IPAdapter_plus.git
git clone https://github.com/pythongosssss/ComfyUI-Custom-Scripts.git
git clone https://github.com/ltdrdata/ComfyUI-Impact-Pack.git
git clone https://github.com/Nuked88/ComfyUI-N-Nodes.git
git clone https://github.com/Kosinkadink/ComfyUI-VideoHelperSuite.git
```

## 5. 启动 ComfyUI

内网机器可以使用 vscode 做临时端口转发

```
CUDA_VISIBLE_DEVICES=0 python main.py --gpu-only --force-fp16 --listen '0.0.0.0' --port 1234
```
