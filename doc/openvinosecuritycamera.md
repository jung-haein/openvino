# OpenVino security camera application
[OpenVino](https://software.intel.com/en-us/openvino-toolkit) is a vision inference and neural network optimization toolkit. We've created a docker image that demonstrates a security camera application using OpenVino.

Install Ubuntu 16.04 x64 on an Intel Skylake (6th generation) or newer processor.

Install [Docker CE for Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu)

Start xhost
```
xhost +local:root
```
Run container
```
sudo docker run -it --privileged --env="DISPLAY=:0" --env="QT_X11_NO_MITSHM=1" --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" -v /dev/dri:/dev/dri nuiwos/repository01:openvinosecuritycamera bash
```
Run security camera application
```
cd security_camera
./security_barrier_camera_sample -d "GPU" -d_va "GPU" -d_lpr "GPU" -i car_1.bmp -m vehicle-license-plate-detection-barrier-0007.xml -m_va vehicle-attributes-recognition-barrier-0039.xml -m_lpr license-plate-recognition-barrier-0001.xml
```