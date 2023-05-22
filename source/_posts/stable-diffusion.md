---
title: stable diffusion
date: 2023-05-09 17:54:42
tags:
	- ai绘画
	- statble-diffusion
categories: project 
---


从今天开始正式学习stable-diffusion


# stable diffusion
当下ai绘画主流产品：MidJourney ，stable-diffusion， DALL·E

   产品          | 特点 | 共同点
   ---           | ---  | ---
MidJourney       |  收费 | 三款产品都是可以根据text形式prompt(提示词)来生成图片也可以根据图片来修改。
DALL-E           | openai 产品之一，著名的是其语言模型gpt-4 ，ofcourse，收费。| ^
stable-diffusion | 开源免费，适合商用  | ^

## Requisite
- 潜空间

- UNet神经网络

- 调度算法Scheduling

- 扩散diffusion

- 生成过程
![图像生成过程](stable-diffusion/image.jpg)

------------

# 使用

## env build
- 本地环境搭建webui

- 如何在服务器上通过接口调用服务

## use-case
- text2img

- text+img2img

# 应用--换装预览

## Thread
1. client
选择衣服，选择预览人物
2. server
根据所选衣服和预览人物，生成提示词，填入后调接口进行生成

## Details
1. 人物模型生成
2. 衣服模型提取
3. 生成提示词精准度
4. 提高生成速度

## implement

# ***reference***
- https://civitai.com/
- https://zhuanlan.zhihu.com/p/610094594?utm_id=0
- stable-diffusion wiki
- 好玩的AI社区：[这是stable-diffusion的一个样例, 还有例如chatgpt-4的体验空间](https://huggingface.co/spaces/stabilityai/stable-diffusion)


{% cq %}"Do one thing every day that scares you." --Eleanor Roosevelt{% endcq %}