FROM nvidia/cuda:10.0-runtime-ubuntu18.04

RUN apt update
RUN apt install -y --no-install-recommends \
	vim \
	git \
	python3-pip

WORKDIR /workspace 
RUN chmod -R a+w /workspace

RUN pip3 install setuptools
RUN git clone https://github.com/tea7010/docker_setup.git
RUN pip3 install -r ./docker_setup/torch/requirements.txt
