FROM --platform=linux/arm64 ubuntu:20.04@sha256:64162ac111b666daf1305de1888eb67a3033f62000f5ff781fe529aff8f88b09

ENV TZ=Asia/Kolkata

RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN apt-get update

WORKDIR /

# Install v4l2
RUN apt install -y v4l-utils

# Install CV2
RUN apt install -y cmake
RUN apt install -y git
# RUN apt install -y libgtk2.0-dev
RUN apt install -y pkg-config 
RUN apt install -y libavcodec-dev 
RUN apt install -y libavformat-dev 
RUN apt install -y libswscale-dev
# RUN apt install -y python-dev 
RUN apt install -y python3-numpy 
# RUN apt install -y python3 
# RUN apt install -y python3-pip 
RUN apt install -y wget 
# RUN apt install -y python3.8-dev
RUN apt install -y python3-dev
# RUN pip3 install numpy
RUN apt autoremove -y python2

RUN mkdir motionapp 

WORKDIR /motionapp

RUN wget https://github.com/opencv/opencv/archive/refs/tags/4.5.5.tar.gz

RUN tar -xf 4.5.5.tar.gz

RUN mv opencv-4.5.5 opencv
# RUN git clone https://github.com/opencv/opencv.git

# Install Gstreamer
RUN apt install -y libgstreamer1.0-dev
RUN apt install -y libgstreamer-plugins-base1.0-dev
RUN apt install -y libgstreamer-plugins-bad1.0-dev
# RUN apt install -y gstreamer1.0-plugins-base
RUN apt install -y gstreamer1.0-plugins-good
RUN apt install -y gstreamer1.0-plugins-bad
RUN apt install -y gstreamer1.0-plugins-ugly
RUN apt install -y gstreamer1.0-tools

WORKDIR /motionapp/opencv

# RUN python3 -c "from distutils.sysconfig import get_python_inc; print(get_python_inc())" 
# RUN python3 -c "from distutils.sysconfig import get_python_lib; print(get_python_lib())"
# RUN python3 -c "import numpy as np;print(np.get_include())"


RUN mkdir build && cd build && \
    cmake \
    -DBUILD_CUDA_STUBS=OFF \
    -DBUILD_DOCS=OFF \
    -DBUILD_EXAMPLES=OFF \
    -DBUILD_JASPER=OFF \
    -DBUILD_JAVA=OFF \
    -DBUILD_JPEG=OFF \
    -DBUILD_OPENEXR=OFF \
    -DBUILD_OPENJPEG=OFF \
    -DBUILD_PERF_TESTS=OFF \
    -DBUILD_PNG=OFF \
    -DBUILD_PROTOBUF=OFF \
    -DBUILD_TBB=OFF \
    -DBUILD_TESTS=OFF \
    -DBUILD_TIFF=OFF \
    -DBUILD_WEBP=OFF \
    -DBUILD_WITH_DEBUG_INFO=OFF \
    -DBUILD_WITH_DYNAMIC_IPP=OFF \
    -DBUILD_ZLIB=OFF \
    -DBUILD_opencv_apps=ON \
    -DBUILD_opencv_calib3d=OFF \
    -DBUILD_opencv_dnn=OFF \
    -DBUILD_opencv_highgui=ON \
    -DBUILD_opencv_js=OFF \
    -DBUILD_opencv_ml=OFF \
    -DBUILD_opencv_python_tests=OFF \
    -DBUILD_opencv_world=OFF \
    -DCV_DISABLE_OPTIMIZATION=OFF \
    -DENABLE_COVERAGE=OFF \
    -DENABLE_FAST_MATH=OFF \
    -DENABLE_FLAKES=OFF \
    -DENABLE_GNU_STL_DEBUG=OFF \
    -DENABLE_IMPL_COLLECTION=OFF \
    -DENABLE_INSTRUMENTATION=OFF \
    -DENABLE_LTO=OFF \
    -DINSTALL_C_EXAMPLES=OFF \
    -DINSTALL_PYTHON_EXAMPLES=OFF \
    -DINSTALL_TESTS=OFF \
    -DOPENCV_DNN_CUDA=OFF \
    -DOPENCV_DNN_OPENCL=OFF \
    -DOPENCV_DNN_PERF_CAFFE=OFF \
    -DOPENCV_GAPI_GSTREAMER=ON \
    -DOPECV_GENERATE_PKGCONFIG=OFF \
    -DPYTHON3_EXECUTABLE=/usr/bin/python3 \
    -DPYTHON3_INCLUDE_DIR=/usr/include/python3.8 \
    -DPYTHON3_LIBRARY=/usr/lib/aarch64-linux-gnu/libpython3.8.so \
    -DPYTHON3_PACKAGES_PATH=/usr/local/lib/python3.8/dist-packages \
    -DWITH_GDAL=OFF \
    -DWITH_GDCM=OFF \
    -DWITH_GPHOTO2=OFF \
    -DWITH_GSTREAMER=ON \
    -DWITH_GTK=OFF \
    -DWITH_GTK_2_X=OFF \
    -DWITH_HALIDE=OFF \
    -DWITH_HPX=OFF \
    -DWITH_JASPER=OFF \
    -DWITH_OPENGL=OFF \
    -DWITH_PROTOBUF=OFF \
    -DWITH_TIFF=OFF \
    -DWITH_V4L=ON \
    -DWITH_VULKAN=OFF \
    -DWITH_FFMPEG=OFF \
    ..

    # -DBUILD_PYTHON3=ON \
    # -DWITH_GSTREAMER=ON \
    # -DBUILD_JAVA=OFF \
    # -DWITH_LAPACK=OFF \
    # -DWITH_MATLAB=OFF \
    # -DWITH_GTK=OFF \
    # -DWITH_GPHOTO2=OFF \
    # -DWITH_CUBLASS=OFF \
    # -DWITH_CUDA=OFF \
    # -DWITH_EIGEN=OFFF \
    # -DWITH_VTK=OFF \
    # -DWITH_JASPER=OFF \
    # -DWITH_WEBP=OFF \
    # -DPYTHON3_EXECUTABLE=/usr/bin/python3 \
    # -DPYTHON3_INCLUDE_DIR=/usr/include/python3.8/ \
    # -DBUILD_NEW_PYTHON_SUPPORT=ON \
    # -DBUILD_opencv_python3=ON \
    # -DHAVE_opencv_python3=ON \
    # -DPYTHON3_DEFAULT_EXECUTABLE=/usr/bin/python3 \
    # -DPYTHON3_LIBRARY=/usr/lib/aarch64-linux-gnu/libpython3.8.so \
    # -DBUILD_PYTHON3=ON \
    # -DBUILD_OPENCV_PYTHON2=OFF \
    # -DBUILD_SHARED_LIBS=ON \
    # -DPYTHON3_LIBRARIES=/usr/lib/python3/dist-packages \
    # -DOPENCV_GENERATE_PKGCONFIG=ON \
    # # -DPYTHON3_NUMPY_INCLUDE_DIRS=/usr/local/lib/python3.8/dist-packages/numpy/core/include \
    # -DPYTHON3_NUMPY_INCLUDE_DIRS=$(python3 -c "import numpy as np;print(np.get_include())") \
    # -DWITH_FFMPEG=OFF \
    # -DWITH_V4L=ON \
    # ..


WORKDIR /motionapp/opencv/build 

RUN make -j6 && make install && ldconfig 

RUN pkg-config --modversion opencv4

WORKDIR /motionapp

# WORKDIR /usr/local/lib/python3.8/dist-packages/

CMD [ "wget", "https://raw.githubusercontent.com/hexagun/DEV/main/testcam/testcam.py", "&&",  \
    "ls", "&&", "python3", "testcam.py" ]

# RUN export PYTHONPATH=/usr/local/lib/python3.8/site-packages/cv2/python-3.8:$PYTHONPATH && \
# RUN python3 -c "import cv2; print(cv2.getBuildInformation())" 

# CMD [ "python3", "testcam.py" ]

# docker build --platform linux/arm64 -t  hexagun/motionapp:test .

# cmake -DWITH_GSTREAMER=ON -DBUILD_PYTON3=ON -DPYTHON3_EXECUTABLE=/usr/bin/python3 -DPYTHON3_INCLUDE_DIR=/usr/include/python3.8 -DPYTHON3_LIBRARY=/usr/lib/aarch64-linux-gnu/libpython3.8.so -DPYTHON3_PACKAGES_PATH=/usr/local/lib/python3.8/dist-packages/ -DWITH_GTK=OFF -DWITH_FFMPEG=OFF _DWITH_VULKAN=OFF -DWITH_OPENGL=OFF ..

