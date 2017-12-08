Install TensorFlow on Ubuntu
=======
> Version 1.0

**Environment**
- GPU: NVIDIA Titan X Pascal
- OS: Ubuntu 16.04

### Install the required packages
Open a terminal by pressing **Ctrl + Alt + T**. 
```
$ sudo apt-get update
$ sudo apt-get -y upgrade
$ sudo apt-get install build-essential
```

### Blacklist the nouveau driver 
Enter *tty* console by pressing **Ctrl + Alt + F1**. 
```
$ echo -e "blacklist nouveau\nblacklist lbm-nouveau\noptions nouveau modeset=0\nalias nouveau off\nalias lbm-nouveau off\n" | sudo tee /etc/modprobe.d/blacklist-nouveau.conf
$ echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf
$ sudo update-initramfs -u
```

### Install the NVIDIA display driver
```
$ sudo services lightdm stop
$ sudo apt-get purge nvidia*
$ sudo add-apt-repository ppa:graphics-drivers/ppa
$ sudo apt-get update
$ sudo apt-get install nvidia-367
$ sudo reboot
```

### Install the CUDA toolkit
```
$ cd ~/Downloads
$ sudo sh cuda_8.0.61_375.26_linux.run
```
Your log may be similar to this:
```
Do you accept the previously read EULA? (accept/decline/quit): accept
Install NVIDIA Accelerated Graphics Driver for Linux-x86_64 375.26? ((y)es/(n)o/(q)uit): n
Install the CUDA 8.0 Toolkit? ((y)es/(n)o/(q)uit): y
Enter Toolkit Location [ default is /usr/local/cuda-8.0 ]:
Do you want to install a symbolic link at /usr/local/cuda? ((y)es/(n)o/(q)uit): y
Install the CUDA 8.0 Samples? ((y)es/(n)o/(q)uit): y
Enter CUDA Samples Location [ default is /home/user ]: 
```
This will install CUDA into: */usr/local/cuda*

### Install the CuDNN toolkit
```
$ cd ~/Downloads
$ tar -xzvf cudnn-8.0-linux-x64-v6.0.tgz
$ sudo cp cuda/include/cudnn.h /usr/local/cuda/include
$ sudo cp cuda/lib64/libcudnn* /usr/local/cuda/lib64
$ sudo chmod a+r /usr/local/cuda/include/cudnn.h /usr/local/cuda/lib64/libcudnn*
```

### Set up the development environment 
We set up the development environment by editting *.bashrc* file.
```
$ sudo gedit ~/.bashrc
```
Then add the following lines to *.bashrc* file,
```
export PATH=/usr/local/cuda-8.0/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH=/usr/local/cuda-8.0/lib64${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}
```
Then executes the modified file,
```
$ source ~/.bashrc
```

### (Optional) Verify NVIDIA driver installation

```
$ nvidia-smi
```
You should be able to see something similar to this,
```
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 378.13                 Driver Version: 378.13                    |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  TITAN Xp            Off  | 0000:01:00.0      On |                  N/A |
| 22%   48C    P5    27W / 250W |    169MiB / 12205MiB |      1%      Default |
+-------------------------------+----------------------+----------------------+

+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID  Type  Process name                               Usage      |
|=============================================================================|
|    0      2421    G   /usr/lib/xorg/Xorg                             105MiB |
|    0     10062    G   compiz                                          63MiB |
+-----------------------------------------------------------------------------+
```

### (Optional) Verify CUDA Toolkit installation
```
$ nvcc -V
```
You should be able to see something similar to this,
```
nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2016 NVIDIA Corporation
Built on Tue_Jan_10_13:22:03_CST_2017
Cuda compilation tools, release 8.0, V8.0.61
```

### Test TensorFlow installation
```
$ python test_tf.py
```





