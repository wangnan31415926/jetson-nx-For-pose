# jetson-nx-For-pose
Use jetson nx for pose detections

<img src="https://user-images.githubusercontent.com/4212806/67125332-71a64580-f1a9-11e9-8ee1-e759a38de215.gif" height=256/>

### Step 1 - Install Dependencies
1.Install PyTorch=v1.7.0 and Torchvision=v0.8.0 To do this on NVIDIA Jetson nx. we recommend following [this guide](https://forums.developer.nvidia.com/t/72048)
    
    
    sudo apt-get install python3-pip
    sudo apt-get install python3-setuptools
    pip3 install Cython
    pip3 install numpy torch-1.7.0-cp36-cp36m-linux_aarch64.whl
    
    
    sudo apt-get install libjpeg-dev zlib1g-dev
    git clone --branch v0.8.0 https://github.com/pytorch/vision torchvision
    cd torchvision
    sudo python3 setup.py install 
    

2. Install [torch2trt](https://github.com/NVIDIA-AI-IOT/torch2trt)

    ```python
    git clone https://github.com/NVIDIA-AI-IOT/torch2trt
    cd torch2trt
    sudo python3 setup.py install --plugins
    ```

3. Install other miscellaneous packages

    ```python
    sudo pip3 install tqdm cython pycocotools
    sudo apt-get install python3-matplotlib
    ```
    
### Step 2 - Install trt_pose

```python
git clone https://github.com/NVIDIA-AI-IOT/trt_pose
cd trt_pose
sudo python3 setup.py install
```

### Step 3 - Run the example notebook

We provide a couple of human pose estimation models pre-trained on the MSCOCO dataset.  The throughput in FPS is shown for each platform
#### You need install [jetcam](http://github.com/NVIDIA-AI-IOT/jetcam) 
| Model | Jetson Nano | Jetson Xavier | Weights |
|-------|-------------|---------------|---------|
| resnet18_baseline_att_224x224_A | 22 | 251 | [download (81MB)](https://drive.google.com/open?id=1XYDdCUdiF2xxx4rznmLb62SdOUZuoNbd) |
| densenet121_baseline_att_256x256_B | 12 | 101 | [download (84MB)](https://drive.google.com/open?id=13FkJkx7evQ1WwP54UmdiDXWyFMY1OxDU) |

To run the live Jupyter Notebook demo on real-time camera input, follow these steps
 
1. Download the model weights using the link in the above table.  

2. Place the downloaded weights in the [tasks/human_pose](tasks/human_pose) directory

3. Open and follow the [live_demo.ipynb](tasks/human_pose/live_demo.ipynb) notebook

    > You may need to modify the notebook, depending on which model you use

## See als
- [torch2trt](http://github.com/NVIDIA-AI-IOT/torch2trt) - An easy to use PyTorch to TensorRT converter

- [JetBot](http://github.com/NVIDIA-AI-IOT/jetbot) - An educational AI robot based on NVIDIA Jetson Nano
- [JetRacer](http://github.com/NVIDIA-AI-IOT/jetracer) - An educational AI racecar using NVIDIA Jetson Nano
- [JetCam](http://github.com/NVIDIA-AI-IOT/jetcam) - An easy to use Python camera interface for NVIDIA Jetson
