# webcam\_yad2k

## Introduction
This repository contains test\_yolo\_video.py hacked to use [yad2k](https://github.com/allanzelener/YAD2K) (Yet Another Darknet 2 Keras by _allanzelener_) with a webcam video input.
Original paper: [YOLO9000: Better, Faster, Stronger](https://arxiv.org/abs/1612.08242) by Joseph Redmond and Ali Farhadi.

## Installation
1. First, install yad2k following its instruction.
1. Clone this repository (webcam\_yad2k) somewhere.
```
git clone https://github.com/kmotohas/webcam_yad2k.git
```
1. Create a hard link of test\_yolo\_video.py into a directory of yad2k.
```
ln webcam_yad2k/test_yolo_video.py /path/to/yad2k/
```
Additionally, you might need to install OpenCV (cv2).

## Usage
Usage of test\_yolo\_video.py is mostly not different from test\_yolo.py of yad2k.
```
cd /path/to/yad2k
## Download Darknet model cfg and weights if you have not done it yet.
# wget http://pjreddie.com/media/files/yolo.weights
# wget https://raw.githubusercontent.com/pjreddie/darknet/master/cfg/yolo.cfg
## Convert the Darknet YOLO_v2 model to a Keras model using yad2k.py.
# ./yad2k.py yolo.cfg yolo.weights model_data/yolo.h5
./test_yolo.py model_data/yolo.h5  # --show_fps 0  # uncomment this if you don't like to show FPS on a corner of a video
```
Some other options is found in lines of argparse in test\_yolo\_video.py.
```
parser = argparse.ArgumentParser(
        description='Run a YOLO_v2 style detection model on test images..')
parser.add_argument(
        'model_path',
        help='path to h5 model file containing body'
        'of a YOLO_v2 model')
parser.add_argument(
        '-a',
        '--anchors_path',
        help='path to anchors file, defaults to yolo_anchors.txt',
        default='model_data/yolo_anchors.txt')
parser.add_argument(
        '-c',
        '--classes_path',
        help='path to classes file, defaults to coco_classes.txt',
        default='model_data/coco_classes.txt')
parser.add_argument(
        '-s',
        '--score_threshold',
        type=float,
        help='threshold for bounding box scores, default .3',
        default=.3)
parser.add_argument(
        '-iou',
        '--iou_threshold',
        type=float,
        help='threshold for non max suppression IOU, default .5',
        default=.5)
parser.add_argument(
        '-fps',
        '--show_fps',
        type=int,
        help='show fps on the top-left corner of a video, default 1 (True)',
        default=1)
```

