# simple track
Demonstration of how to use Spinnaker Api with python for a (too) simple tracking app that uses bg subtraction, thresholding, and smoothing in real time using OpenCV. Note this is not meant to be a production-grade tracker, but just something to help get started with your Point Grey camera using Python/OpenCV.

The main function is point_grey.py, and it has lots of lines commented out you can uncomment to show different aspects of the algorithm in action, and logging functionality where you can set the level to your comfort (e.g., warning, error, debug, etc) to see different levels of verbosity.

## When you get your camera
### 1. Make sure camera works    
Install spinnaker sdk:
https://www.flir.com/products/spinnaker-sdk/ .
Then run SpinView and run camera in continuous mode just to ensure it works. Explore the camera, transport layer, and stream parameters in the dropdown menu corresponding to your camera on the left. These are all features that are accessible via the API (e.g., note transport layer is denoted `TL` in the code).

## 2. Set up Python environment    
Create environment and install things (note this assumes conda).

    conda create --name st
    conda activate st
    conda config --add channels conda-forge
    conda install opencv
    conda update pip
    conda install scipy matplotlib


Install pyspin:

    cd spinnaker
    pip install spinnaker_python-1.23.0.27-cp37-cp37m-win_amd64.whl
Note if you get dll errors when you try to import PySpin: https://stackoverflow.com/questions/55787461/package-works-fine-from-ide-fails-to-find-mkl-intel-thread-dll-from-conda-promp

## 3. Use it
There are two modes you can test in the main function, `point_grey.py`. To just stream images (at command line):

    python point_grey.py 1  

To run the simple tracker:

    python point_grey.py 2
This will grab some background images and then subtract the background, do a gaussian smooth, threshold, and get a contour of the remaining binary blobs picking the biggest blob to track. There will be sliders for the threshold and width of the gaussian filter you can mess around with in real time.
