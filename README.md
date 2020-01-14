
# docker_openvino_ubuntu16.04LTS_xfce4_x11vnc

# "<>" indicate variables/names that you choose

STEP1 : Use "Dockerfile" to create docker container -

sudo docker build . -t <open_vino_with_vnc_xfce4>

STEP2 : Run docker container - 

sudo docker run -it -e DISPLAY=$DISPLAY -p 5900:5900  <open_vino_with_vnc_xfce4> x11vnc -forever -usepw -create

STEP3 : Log on to docker image using vnc - 

vncviewer
server - localhost:5900
password - 1234

STEP4 : Install, build and test demos after logging in Docker image - 

source /opt/intel/openvino/bin/setupvars.sh (if required)
cd /opt/intel/openvino/deployment_tools/demo
./demo_squeezenet_download_convert_run.sh
./demo_security_barrier_camera.sh

STEP5 : Commit the installed software in Docker by coming out of docker container and - 

sudo docker commit <d959ed0d49cb> <open_vino_with_vnc_xfce4_2>
sudo docker ps (gives container id i.e. <d959ed0d49cb>)

TADA!! : Docker image is ready for further use

