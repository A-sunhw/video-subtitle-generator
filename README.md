### 项目介绍

Video-subtitle-generator (vsg) 是一款将视频中的语音提取为外挂字幕文件(srt格式)的软件。 

- 支持中文、英文、韩文、日文、越南语、俄语、西班牙语、葡萄语等语言的字幕生成
- large 模型错词率（WER）如下：

<img src="https://github.com/YaoFANGUK/video-subtitle-generator/blob/main/design/language-breakdown.svg?raw=true" alt="demo">

### DEMO

<img src="https://github.com/YaoFANGUK/video-subtitle-generator/blob/main/design/demo.gif?raw=true" alt="demo">


## 源码使用说明

> 运行要求：需要Nvidia GPU显卡（显存大于1G可使用base模型，大于5G可使用medium模型，大于10G可使用large模型）

#### 1. 下载安装Miniconda或Anaconda

#### 2. 安装依赖文件

安装依赖：

```shell
pip install -r requirements.txt
```

#### 3. 运行程序

- 运行命令行版本(CLI)，也可以用spyder等直接运行

```SHELL
python backend/main.py
```


- 代码调用：

```shell
    # 1.指定音视频文件路径
    wav_path = './test/test.flv'
    # 2. 新建字幕提取器
    sg = SubtitleGenerator(wav_path)
    # 3. 运行字幕生成
    ret = sg.run()
```

#### 4. 模型文件设置（默认base）

修改videffmpeg 不是内部或外部命令,也不是可运行的程序本目录下settings.ini中的Mode，取值为：base, medium, large，即可使用对应的识别模型
模型越大识别效果越好

|  Mode  | 要求显存  | 速度 |
| :----: | :-------: | :--: |
|  base  | 大于1 GB  | ~16x |
| medium | 大于5 GB  | ~2x  |
| large  | 大于10 GB |  1x  |

#### 5. 可能出现的错误

5.1 ffmpeg 不是内部或外部命令,也不是可运行的程序

​	pip install ffmpeg-python，另外再下载ffmpeg并设置相应路径

​	https://zhuanlan.zhihu.com/p/396244853	
