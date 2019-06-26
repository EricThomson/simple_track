## When you get your camera
### 1. Make sure camera works    
Install spinnaker, and run spinview and run camera in continuous mode just to ensure it works. Explore the camera, transport layer, and stream parameters in the dropdown menu corresponding to your camera on the left. These are all features that are accessible via the API so make sure you are familiar with the range of options available and some of the terminology associated with your particular setup (e.g., transport layer = TL in the code). toggle the Recording window (red filled circle) and record some video.

## 2. Set up Python environment    
Create environment and install things (note this assumes conda).

    conda create --name st
    conda activate st
    conda config --add channels conda-forge
    conda install opencv
    conda update pip
    conda install scipy matplotlib spyder -y

Install spinnaker sdk:
https://www.flir.com/products/spinnaker-sdk/

Download and install the python spinnaker wrapper (pyspin). Go to spinnaker folder, then pip install the wheel:

    cd <folder with wheel>
    pip install spinnaker_python-1.23.0.27-cp37-cp37m-win_amd64.whl
Note if you get errors when you try to run from the conda prompt: https://stackoverflow.com/questions/55787461/package-works-fine-from-ide-fails-to-find-mkl-intel-thread-dll-from-conda-promp

Note on installing opencv:
  https://github.com/conda-forge/opencv-feedstock

Make sure PySpin will import (might need to import numpy first because weirdness).

## Working with opencv
From point grey:
https://www.ptgrey.com/KB/10861
OpenCV is an open-source computer vision library that allows you to perform image processing on FLIR machine vision cameras. This application note provides information on how to install and use OpenCV in Visual Studio. OpenCV does not support machine vision standards such as USB3 Vision and GigE Vision, therefore it is not recommended to grab images using OpenCV functions. Instead, we recommend using the Spinnaker SDK to grab images and convert them to OpenCV images, and then do your OpenCV magic...
