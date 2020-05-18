# Face Detection Snap
Forked from: https://github.com/ZekeMedley/tensorflow-face-detection
Original repo: https://github.com/yeephycho/tensorflow-face-detection

This fork of the repos above adds support for running these scripts on an Ubuntu Core Kiosk.

## Building
Before you build the project, make sure you have the required depenencies installed (snapcraft and lxd).
```
snap install snapcraft --classic
snap install lxd
sudo lxd init
# Accept all defaults
```
You can build this project as you would any snap, by running `snapcraft` from the root of the repository. However, I did experience issures running out of memory (because the multipass vm was capped at 2G). So I built using LXD.
```
snapcraft --use-lxd
```

## Running
After building the snap, you can install, configure and run it with the following commands
```
snap install --dangerous ./face-detection_0.1_amd64.snap
snap connect face-dection:camera
face-dectection.camera
```

## About the model
A mobilenet SSD(single shot multibox detector) based face detector with pretrained model provided, powered by tensorflow [object detection api](https://github.com/tensorflow/models/tree/master/research/object_detection), trained by [WIDERFACE dataset](http://mmlab.ie.cuhk.edu.hk/projects/WIDERFace/).

## Features
Speed, run 60fps on a nvidia GTX1080 GPU.

Memory, requires less than 364Mb GPU memory for single inference.

Robust, adapt to different poses, this feature is credit to [WIDERFACE dataset](http://mmlab.ie.cuhk.edu.hk/projects/WIDERFace/), I manually cleaned the dataset to balance the precision and recall trade off.

Parallel, multiple process video processing, can inference multiple input simultaneously, I tested to process 4 videos on a single GPU card at the same time, the speed is still competitive, and there's still room to accommodate more processes.

### Further
The model released by this repo. has already been merged into Deep Video Analytics / Visual Data Network.

Please click the following link for more applications.

[1] https://www.deepvideoanalytics.com
[2] https://github.com/VisualDataNetwork/root

## License
Usage of the code and model by yeephycho is under the license of Apache 2.0.

The code is based on GOOGLE tensorflow object detection api. Please refer to the license of tensorflow.

Dataset is based on WIDERFACE dataset. Please refer to the license to the WIDERFACE license.
