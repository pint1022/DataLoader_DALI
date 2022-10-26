# # build cmd: docker build -t centaurusinfra/swin-transform-ss-cityscapes --build-arg CACHEBUST=$(date +%s) .
# # From centaurusinfra/swin-transform-ss-cityscapes
# FROM pytorch/pytorch:latest

# RUN curl -fsSL https://deb.nodesource.com/setup_18.x | bash -
# RUN apt-get install -y nodejs

# RUN /opt/conda/bin/conda install -y opencv Cython tensorflow pandas scikit-learn matplotlib seaborn jupyter jupyterlab && \
#     /opt/conda/bin/conda install -c conda-forge tensorboardx && \
#     /opt/conda/bin/conda clean -ya




# RUN mkdir -p /home/me && chmod 1777 /home/me

# ENV HOME /home/me

FROM pytorch/pytorch:1.12.0-cuda11.3-cudnn8-devel
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A4B469963BF863CC

RUN apt-get update && apt-get install -y git vim 
RUN apt-get install -y cuda-toolkit-11-4


RUN pip install scipy dataset pytorch-ignite matplotlib seaborn
RUN mkdir /root/{data,logs,scripts}

RUN apt-get install -y nodejs
RUN pip3 install jupyter matplotlib
RUN pip3 install jupyter_http_over_ws ipykernel nbformat
RUN jupyter serverextension enable --py jupyter_http_over_ws

RUN pip3 install jupyterlab==3.4.7
# RUN jupyter --version
# RUN jupyter labextension install jupyterlab_tensorboard
RUN pip3 install jupyter_tensorboard torchvision scikit-image
# # tensorboard
# EXPOSE 6006
# jupyter notebook
RUN pip install --extra-index-url https://developer.download.nvidia.com/compute/redist --upgrade nvidia-dali-cuda110
RUN pip install -U scikit-learn scipy
# RUN apt-get update && DEBIAN_FRONTEND="noninteractive" TZ="America/San_Francisco" apt-get install -y tzdata

# RUN apt update
# RUN apt install -y software-properties-common
# RUN add-apt-repository ppa:deadsnakes/ppa
# RUN apt install -y python3.9
EXPOSE 8888
WORKDIR /root/scripts

# COPY start.sh /

# CMD ["/start.sh"]


# ENV CU_HOOK_DEBUG=1

COPY test/*.py ./ 
COPY test/git-lfs-linux-amd64-v3.2.0.tar.gz ./ 
RUN tar -zxvf ./git-lfs-linux-amd64-v3.2.0.tar.gz 
RUN cd git-lfs-3.2.0
RUN bash git-lfs-3.2.0/install.sh
