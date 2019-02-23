# Google Colab Tutorial

Colab is a Google’s free cloud service which will let you run your deep learning or machine learning models in cloud.

### Creating New Colab Notebook

* Open your Google Drive
* Create a new notebook via Right click > More > Colaboratory

### GPU Setting

Edit > Notebook settings or Runtime>Change runtime type and select GPU as Hardware accelerator

### RAM Info
```
!cat /proc/meminfo
```

### CPU Info

```
!cat /proc/cpuinfo
```

### Install Libraries

!pip install or !apt-get install

```
!pip3 install tensorflow==1.8
!pip3 install keras
!pip3 install torch torchvision
!apt-get install python-numpy python-scipy
```
### Install OpenCV for c/c++

```
!apt-get install -qq gcc-5 g++-5 -y
!ln -s /usr/bin/gcc-5 
!ln -s /usr/bin/g++-5 

!sudo apt-get update
!sudo apt-get upgrade

#Install Dependencies
!sudo apt-get install -y build-essential 
!sudo apt-get install -y cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
#The following command is needed to process images:
!sudo apt-get install -y python-dev python-numpy libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev
#To process videos:
!sudo apt-get install -y libavcodec-dev libavformat-dev libswscale-dev libv4l-dev
!sudo apt-get install -y libxvidcore-dev libx264-dev
#For GUI:
!sudo apt-get install -y libgtk-3-dev
#For optimization:
!sudo apt-get install -y libatlas-base-dev gfortran pylint
!wget https://github.com/opencv/opencv/archive/3.4.0.zip -O opencv-3.4.0.zip
!sudo apt-get install unzip
!unzip opencv-3.4.0.zip
%cd opencv-3.4.0
!mkdir build
%cd build
!cmake -D WITH_TBB=ON -D WITH_OPENMP=ON -D WITH_IPP=ON -D CMAKE_BUILD_TYPE=RELEASE -D BUILD_EXAMPLES=OFF -D WITH_NVCUVID=ON -D WITH_CUDA=OFF -D BUILD_DOCS=OFF -D BUILD_PERF_TESTS=OFF -D BUILD_TESTS=OFF -D WITH_CSTRIPES=ON -D WITH_OPENCL=ON CMAKE_INSTALL_PREFIX=/usr/local/ ..
!make -j`nproc`
!sudo make install

```
### Cloning Github Repo to Google Colab

```
!git clone https://github.com/ildoonet/tf-pose-estimation.git
```
### Mount your Google Drive

```
from google.colab import drive
drive.mount('/content/drive/')
```

### Check your Folder Data

```
!ls Drive/test
```

### Upload code from your system

```
from google.colab import files
uploaded = files.upload()
```
### Make zip file of your Data

```
from google.colab import files
import zipfile
import sys
foldername = 'your folder or filename'
zipfile.ZipFile('Drive/'+foldername + '.zip', 'w', zipfile.ZIP_DEFLATED)
```

### Downloading the data from the colab

```
from google.colab import files
files.download('Drive/test.zip')
```
