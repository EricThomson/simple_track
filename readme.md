# simple track
Demonstration of how to use Spinnaker Api with python for a (too) simple tracking app that uses thresholding and background subtraction. Note this is not meant to be a production-grade tracker, but just something to help get started with your Point Grey camera in Python.

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
    conda install scipy matplotlib

Install spinnaker sdk:
https://www.flir.com/products/spinnaker-sdk/

Download and install the python spinnaker wrapper (pyspin). Go to spinnaker folder, then pip install the wheel:

    cd <folder with wheel>
    pip install spinnaker_python-1.23.0.27-cp37-cp37m-win_amd64.whl
Note if you get errors when you try to run from the conda prompt: https://stackoverflow.com/questions/55787461/package-works-fine-from-ide-fails-to-find-mkl-intel-thread-dll-from-conda-promp

Note on installing opencv:
  https://github.com/conda-forge/opencv-feedstock

Make sure PySpin will import (might need to import numpy first because weirdness).

## 3. Use it
There are two modes you can test in the main function, `point_grey.py`. To just stream images (at command line):

    python point_grey.py 1  

To run the simple tracker:

    python point_grey.py 2
This will grab some background images and then subtract the background, do a gaussian smooth, threshold, and get a contour of the remaining binary blobs picking the biggest blob to track. There will be sliders for the threshold and width of the gaussian filter you can mess around with in real time.
