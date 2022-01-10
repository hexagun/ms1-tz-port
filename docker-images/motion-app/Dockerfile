FROM --platform=linux/arm64 ubuntu:20.04

ENV TZ=Asia/Kolkata

RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN apt-get update && apt install nano -y

RUN apt-get install -y v4l-utils

RUN apt-get install -y libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev \
    libgstreamer-plugins-bad1.0-dev gstreamer1.0-plugins-base gstreamer1.0-plugins-good \
    gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-tools 

WORKDIR /

RUN apt install -y \
    build-essential \
    cmake \
    git \
    libgtk2.0-dev \
    pkg-config 
    
RUN apt install -y libavcodec-dev 

RUN apt install -y libavformat-dev 

RUN apt install -y libswscale-dev

RUN apt install -y python-dev 

RUN apt install -y python-numpy 

RUN apt install -y python3 

RUN apt install -y python3-pip 

RUN apt install -y wget 

RUN apt install python3.8-dev

RUN apt install python3-dev

RUN pip install numpy

RUN mkdir ws 

WORKDIR /ws

RUN git clone https://github.com/opencv/opencv.git

WORKDIR /ws/opencv

RUN mkdir build && cd build && \
    cmake -DWITH_GSTREAMER=ON \
    -DCMAKE_INSTALL_PREFIX=/usr/local \
    -DPYTHON3_EXECUTABLE=/usr/bin/python3 \
    -DPYTHON3_INCLUDE_DIR=/usr/include/python3.8/ \
    -DBUILD_NEW_PYTHON_SUPPORT=ON \
    -DBUILD_opencv_python3=ON \
    -DPYTHON_DEFAULT_EXECUTABLE=/usr/bin/python3 \
    -DPYTHON3_LIBRARY=/usr/lib/aarch64-linux-gnu/libpython3.8.so .. 

WORKDIR /ws/opencv/build 

RUN pwd

RUN make -j6

RUN make install

RUN ldconfig 

WORKDIR /ws

RUN mkdir images

WORKDIR /usr/local/lib/python3.8/site-packages/cv2/python-3.8/

RUN wget https://raw.githubusercontent.com/hexagun/DEV/main/testcam/testcam.py

RUN pwd

RUN ls -l

RUN python3 testcam.py