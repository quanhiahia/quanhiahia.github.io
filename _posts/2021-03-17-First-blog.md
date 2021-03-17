---
layout: post
title: "Ubuntu 20.04에 CUDA cuDNN Pytorch"
date: 2021-03-17
---

> ## 1. Verify the NVIDIA driver version 
> ```
> $ nvidia-smi
> ```
> ![](/_img/1.png) <br />
> 
> Before all, install GCC 
> ```   
> $ sudo apt update
> $ sudo apt install build-essential
> ```
> Check if GCC is installed
> ```
> $ gcc --version
> ```
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
> Unchoose the driver option and choose install <br />
> ![](/_img/4.png)   
> Add the path in the end of the bashrc file (https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#post-installation-actions)
> ```
> $ export PATH=/usr/local/cuda-11.2/bin${PATH:+:${PATH}}
> $ export LD_LIBRARY_PATH=/usr/local/cuda-11.2/lib64\${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
> ```
> After the following command in terminal
> ```
> source ~/.bashrc
> ```
> Check if the CUDA is sucessfully installed
> ```
> nvcc --version
> ```
> 
> ![](/_img/5.png) <br />
> 
> Try the sample code in CUDA (https://docs.nvidia.com/cuda/cuda-samples/index.html#asyncapi)<br />
> Compile
> ```
> $ cd /usr/local/cuda-11.2/samples/0_Simple/matrixMul
> $ make
> ```
> 
> Run 
> ```
> $ ./matrixMul
> ``` 
> 
> ![](/_img/6.png) 
> 
> ## 3. Install cuDNN
> Here choose to use the Deb installation. (https://developer.nvidia.com/rdp/cudnn-archive)
> ![](/_img/7.png) 
>  
> Navigate to the dicrectory contraining the  cuDNN Debian file
> 
> ``` 
> sudo dpkg -i libcudnn8_x.x.x-1+cudax.x_amd64.deb
> sudo dpkg -i libcudnn8-dev_8.x.x.x-1+cudax.x_amd64.deb
> sudo dpkg -i libcudnn8-samples_8.x.x.x-1+cudax.x_amd64.deb
> ``` 
> 
> Verify the installation
> > 1. copy the cuDNN samples to a writable path
> > ``` 
> > $cp -r /usr/src/cudnn_samples_v8/ $HOME
> > ``` 
> > 2. Go to the writable path
> > ``` 
> > $ cd  $HOME/cudnn_samples_v8/mnistCUDNN
> > ``` 
> > 3. Compile the sample
> > ``` 
> > $ sudo make clean && make
> > ``` 
> > 4. Run the sample
> > ``` 
> > $ ./mnistCUDNN
> > ``` 
> > if the cuDNN is properly installed, we will see 
> > ``` 
> > Test Passed!
> > ``` 
