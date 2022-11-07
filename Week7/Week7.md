## 文柯力-CV-Week#7

<div class="alert alert-success">
Github或者主页下载运行一个超分算法，获得结果试着训练一两个Epoch，给出超分结果
</div>     

选择模型：[EDSR-PyTorch](https://github.com/sanghyun-son/EDSR-PyTorch) <img src="https://camo.githubusercontent.com/4bc45421df57c3901ec5d21da412680df9b2d74fee7c297ab4e6764868e805fb/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f707974686f6e2d332e362b2d6f72616e67652e737667" alt="python version" data-canonical-src="https://img.shields.io/badge/python-3.6+-orange.svg" style="max-width: 100%;"> ![](https://img.shields.io/badge/homework-@wkl-yellow.svg?style=flat)


```
@InProceedings{Lim_2017_CVPR_Workshops,
  author = {Lim, Bee and Son, Sanghyun and Kim, Heewon and Nah, Seungjun and Lee, Kyoung Mu},
  title = {Enhanced Deep Residual Networks for Single Image Super-Resolution},
  booktitle = {The IEEE Conference on Computer Vision and Pattern Recognition (CVPR) Workshops},
  month = {July},
  year = {2017}
}
```

我们使用的数据集是[DIV2K](http://www.vision.ee.ethz.ch/%7Etimofter/publications/Agustsson-CVPRW-2017.pdf)，下载[链接🔗](https://cv.snu.ac.kr/research/EDSR/DIV2K.tar)。

>
>
>```bash
># for train
>python main.py --model EDSR --scale 2 --patch_size 96 --save edsr_baseline_x2 --reset 
>
># for test
>CUDA_VISIBLE_DEVICES=1 python main.py --data_test Demo --scale 4 --pre_train ../experiment/edsr_baseline_x2/model/model_latest.pt --test_only -->save_results
>```

下面截取一些 training 时的 **Log**

---
>```
>[Epoch 3]	Learning rate: 1.00e-4
>[1600/16000]	[L1: 4.4706]	2.3+1.5s
>[3200/16000]	[L1: 4.4269]	2.2+1.2s
>[4800/16000]	[L1: 4.4215]	2.2+1.2s
>[6400/16000]	[L1: 4.3603]	2.2+1.2s
>[8000/16000]	[L1: 4.3189]	2.3+1.2s
>[9600/16000]	[L1: 4.3030]	2.4+1.1s
>[11200/16000]	[L1: 4.2870]	2.6+0.9s
>[12800/16000]	[L1: 4.2929]	2.6+0.9s
>[14400/16000]	[L1: 4.2714]	2.6+0.9s
>[16000/16000]	[L1: 4.2578]	2.7+0.8s
>
>Evaluation:
>[DIV2K x2]	PSNR: 34.029 (Best: 34.029 @epoch 3)
>Forward: 2.14s
>
>Saving...
>Total: 2.56s
>
>[Epoch 4]	Learning rate: 1.00e-4
>[1600/16000]	[L1: 4.1744]	2.4+1.4s
>[3200/16000]	[L1: 4.1518]	2.4+1.0s
>[4800/16000]	[L1: 4.1185]	2.5+1.0s
>[6400/16000]	[L1: 4.1251]	2.5+1.0s
>[8000/16000]	[L1: 4.1394]	2.4+1.0s
>[9600/16000]	[L1: 4.1214]	2.5+1.0s
>[11200/16000]	[L1: 4.1149]	2.5+1.0s
>[12800/16000]	[L1: 4.1061]	2.4+1.0s
>[14400/16000]	[L1: 4.1054]	2.5+1.0s
>[16000/16000]	[L1: 4.0968]	2.4+1.0s
>
>Evaluation:
>[DIV2K x2]	PSNR: 34.266 (Best: 34.266 @epoch 4)
>Forward: 2.13s
>
>Saving...
>Total: 2.43s
>```
---
>```
>[Epoch 133]	Learning rate: 1.00e-4
>[1600/16000]	[L1: 3.5245]	2.5+1.3s
>[3200/16000]	[L1: 3.4206]	2.6+0.9s
>[4800/16000]	[L1: 3.3988]	2.7+0.8s
>[6400/16000]	[L1: 3.3818]	2.5+1.0s
>[8000/16000]	[L1: 3.3493]	2.5+1.0s
>[9600/16000]	[L1: 3.3763]	2.5+1.0s
>[11200/16000]	[L1: 3.3944]	2.5+1.0s
>[12800/16000]	[L1: 3.3929]	2.5+1.0s
>[14400/16000]	[L1: 3.3858]	2.5+1.0s
>[16000/16000]	[L1: 3.3972]	2.5+1.0s
>
>Evaluation:
>[DIV2K x2]	PSNR: 35.349 (Best: 35.444 @epoch 119)
>Forward: 2.12s
>
>Saving...
>Total: 2.36s
>
>[Epoch 134]	Learning rate: 1.00e-4
>[1600/16000]	[L1: 3.3487]	2.6+1.2s
>[3200/16000]	[L1: 3.4842]	2.6+0.9s
>[4800/16000]	[L1: 3.4571]	2.6+0.9s
>[6400/16000]	[L1: 3.4436]	2.6+0.9s
>[8000/16000]	[L1: 3.4697]	2.6+0.9s
>[9600/16000]	[L1: 3.4793]	2.6+0.9s
>[11200/16000]	[L1: 3.4532]	2.6+0.9s
>[12800/16000]	[L1: 3.4586]	2.6+0.9s
>[14400/16000]	[L1: 3.4524]	2.6+0.9s
>[16000/16000]	[L1: 3.4467]	2.6+0.9s
>
>Evaluation:
>[DIV2K x2]	PSNR: 35.456 (Best: 35.456 @epoch 134)
>Forward: 2.15s
>
>Saving...
>Total: 2.45s
>```
---

下面是测试结果，使用了作者给定的最终模型，使用了由AI绘制的图，其中**左图**是经过超分之后的图，右图是原始图片，在不经过放大的情况下，两者很不出肉眼差别。但是左边的图片内存占用为：`12Mb` 右图为：`1.3Mb`
<center>
<!-- <img src="../AI_x4_SR.png" alt="AI_x4" style="zoom:15%;" /> <img src="../AI-org.png" alt="AI_org" style="zoom:40%;" /> -->
<img src="AI_x4_SR.png" alt="AI_x4" width="200" /> <img src="AI-org.png" alt="AI_org" width="200"  />
</center>



