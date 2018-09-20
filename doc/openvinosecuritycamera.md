# OpenVino security camera application
[OpenVino](https://software.intel.com/en-us/openvino-toolkit) is a vision inference and neural network optimization toolkit. We've created a docker image that demonstrates a security camera application using OpenVino.

Install Ubuntu 16.04 x64 on an Intel Skylake (6th generation) or newer processor.

Install [Docker CE for Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu)

Start xhost
```bash
xhost +local:root
```
Run container
```bash
sudo docker run -it --privileged --env="DISPLAY=:0" --env="QT_X11_NO_MITSHM=1" --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" -v /dev/dri:/dev/dri -v /dev:/dev --network=host --device /dev/video0 nuiwos/repository01:openvinosecuritycamera bash
```
Run security camera application
```bash
./run_openvino_security_camera_on_cpu.sh
```