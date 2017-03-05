FROM open-ocr:build

# Get OpenCV libraries.
RUN apt-get -q -y install \
  libopencv-core2.4v5 \
  libopencv-core-dev \
  libboost-all-dev \
  libopencv-flann2.4v5 libopencv-flann-dev \
  libopencv-imgproc2.4v5 libopencv-imgproc-dev \
  libopencv-photo2.4v5 libopencv-photo-dev \
  libopencv-video2.4v5 libopencv-video-dev \
  libopencv-features2d2.4v5 libopencv-features2d-dev \
  libopencv-objdetect2.4v5 libopencv-objdetect-dev \
  libopencv-calib3d2.4v5 libopencv-calib3d-dev \
  libopencv-ml2.4v5 libopencv-ml-dev \
  libopencv-contrib2.4v5 libopencv-contrib-dev \
  libopencv-highgui2.4v5 libopencv-highgui-dev

# Install & build DetectText
RUN cd /opt && git clone https://github.com/tleyden/DetectText.git
RUN cd /opt/DetectText && g++ -o DetectText TextDetection.cpp FeaturesMain.cpp -lopencv_core -lopencv_highgui -lopencv_imgproc -I/opt/DetectText
RUN cd /opt/DetectText && cp DetectText /usr/local/bin

# build open-ocr-preprocessor binary and copy it to /usr/bin
RUN cd $GOPATH/src/github.com/tleyden/open-ocr/cli-preprocessor && go build -v -o open-ocr-preprocessor && cp open-ocr-preprocessor /usr/bin
