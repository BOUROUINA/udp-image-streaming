# UDP Live Image Streaming

This project is inspired by https://www.cs.utexas.edu/~teammco/misc/udp_video/ , where images are grabbed from camera on one machine and transfered to another machine via UDP, resulting in negligible latency.

Parameters such as stream size or quality can be adjusted in `config.h` before re-compile the program.

## Grabbing

The code grabs video stream from OpenCV's default input video device. To change input source, simply change the argument passed to CV::VideoCapture() accordingly.

## Encoding

To avoid latency altogether there is no video codec involved during this process. Every frame is individually encoded to `jpeg` format by OpenCV to drastically reduce the bandwidth consumption.

If passing raw image is preferred, consider changing `jpeg` to `bmp`.

## Demo

Run the following command to see stream your camera through localhost:
```
cmake . && make
./server 10000 &
./client localhost 10000
```

You should see two windows, one the original grabbed image (before encoding) and one received stream image (after encoding/decoding).

## Acknowledgement and Copyright
This project includes some code from [Practical C++ Sockets](http://cs.ecs.baylor.edu/~donahoo/practical/CSockets/practical/) and requires [OpenCV 3](http://opencv.org/).

This project is puslished under GPLv3.