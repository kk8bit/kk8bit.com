---
layout: post
title: KayTool-ComfyUI工具包
category: Repository
permalink: /1990
---

- [项目地址](https://github.com/kk8bit/KayTool.git)

这是一个为 ComfyUI 开发的自定义节点实用工具包，在未来我会陆续为它增加功能


## 节点预览:

![preview_custom_save_image_node](https://s2.loli.net/2024/11/08/b1dZw9RAFiyxJzo.png)

## 当前功能：

### Color Adjustment 节点功能

- 支持对图片的曝光、对比度、色温、色调和饱和度进行调节
    - 曝光和对比度：范围为-100到+100
    - 色温：范围为-100到+100，负值增加蓝色，正值增加黄色
    - 色调：范围为-100到+100，负值增加绿色，正值增加洋红
    - 饱和度：范围为-100到+100

- 提供多种滤镜效果，通过选择列表调用 Instagram 的网红滤镜
    - 所有滤镜按序编号，并增加一个"None"选项以不应用滤镜

- 可自定义滤镜的强度
    - 强度范围为0到100（0表示不应用滤镜，100表示完全应用滤镜）

- 选择“应用所有滤镜”选项时，生成并返回所有滤镜效果的图像序列

- 在调节图像的曝光、对比度、色温、色调和饱和度后，再应用选定的滤镜

### Custom SaveImage 节点功能

- 选择保存图片的格式（PNG 或 JPG）
- 自定义 JPG 图片质量（0-100）
- 支持两种颜色配置文件（sRGB IEC61966-2.1 和 Adobe RGB (1998)）
    - 当选择 Adobe RGB 时，自动将图像转换为 Adobe RGB 色彩空间以确保色彩准确
- 选择是否保存元数据（包括工作流、作者、版权信息和自定义提示）
- 自定义元数据字段：
    - 作者
    - 版权信息
- 自动生成唯一文件名，以确保每个保存的图像有独立名称
- 自动创建输出文件夹 `output/Custom_Save_Image`，用于保存所有生成的图片
- 当保存为 PNG 格式时，元数据以 PNG 信息（PngInfo）存储；当保存为 JPG 格式时，元数据以 EXIF 形式存储

## 一些说明

- 要保存”JPG“格式，必须将"metadata“设置为"False"
- 当选择保存"metadata“(工作流信息)时，将自动切换为"PNG"格式，并忽略"JPG"格式的设置
- 如果你需要更小容量但不损失肉眼可见的画质，可以讲"JPG"图片质量设置为 40，更低的数值将肉眼可见色块

## 安装与使用

- 将本项目克隆到你的 `ComfyUI/custom_nodes`目录下，并确保将 sRGB Profile.icc 和AdobeRGB1998.icc 文件放在 resources 目录中
```bash
git clone https://github.com/kk8bit/KayTool.git
```
- 重启 ComfyUI 并在节点菜单中找到 "KayTool" 及其分支
- 在ComfyUI Manager中也可以搜索到KayTool工具包
- [项目地址](https://github.com/kk8bit/KayTool.git)