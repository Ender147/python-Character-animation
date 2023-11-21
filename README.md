# python-Character-animation
基于python实现的字符动画流程
# 实现流程
<img width="362" alt="image" src="https://github.com/Ender147/python-Character-animation/assets/57763467/b28155ab-0dde-4cbf-a820-06f714a73369">

# ffmpeg
FFmpeg是一套可以用来记录、转换数字音频、视频，并能将其转化为流的开源计算机程序。采用LGPL或GPL许可证。它提供了录制、转换以及流化音视频的完整解决方案。
下载链接：https://ffmpeg.org/

## ffmpeg把视频文件以每秒25帧的速度分割jpg帧图像序列命令
ffmpeg -i loli.mp4 -r 25 -qscale:v 2 out/%04d.jpg
生成结果如下：
<img width="624" alt="image" src="https://github.com/Ender147/python-Character-animation/assets/57763467/6d1047a7-b770-44f0-ba3d-c8b56b389303">

## 把生成的所有jpg帧图像和python脚本文件放到同一个文件夹内，在cmd终端运行python脚本，把jpg帧图像转换成以有色字符组成的png图像
例如：
<img width="598" alt="image" src="https://github.com/Ender147/python-Character-animation/assets/57763467/484750ce-b99d-40d9-8a61-a37bccaea96a">


## 使用ffmpeg把生成的所有png图像序列整合成视频
命令：ffmpeg -f image2 -i %d.png -vf fps=25 -vcodec libx264 -profile:v high444 -refs 16 -crf 0 -preset ultrafast out.mp4

最后使用剪辑软件把视频的原有音频合并进去，大功告成。

