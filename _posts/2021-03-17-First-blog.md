---
layout: post
title: "Ubuntu 20.04에 CUDA cuDNN Pytorch"
date: 2021-03-17
---

> ## 1. Verify the NVIDIA driver version 
> ```
> $ nvidia-smi
> ```
> ![](/_img/1.png)
>   
> ## 2. Install CUDA 
> Get the installation command from CUDA official site 
> Choose Linux--x86_64--Ubuntu--20.04--runfile(local) 
> ```
> $ wget https://developer.download.nvidia.com/compute/cuda/11.2.2/local_installers/cuda_11.2.2_460.32.03_linux.run
> $ sudo sh cuda_11.2.2_460.32.03_linux.run
> ```
> Then there will be warning message from Nvidia. Just ignore it and choose continue
> ![](/_img/2.png)   
> And type "accepted"
> ![](/_img/3.png)   
> Unchoose the driver option and choose install
> ![](/_img/4.png)   
> ## 3. 
