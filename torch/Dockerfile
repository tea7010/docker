FROM nvidia/cuda:10.0-cudnn7-devel-ubuntu18.04

RUN apt update && apt install -y --no-install-recommends \
	vim \
	git \
	python3-pip

WORKDIR /workspace 
RUN chmod -R a+w /workspace

RUN pip3 install setuptools
RUN git clone https://github.com/tea7010/docker_setup.git
RUN pip3 install -r ./docker_setup/torch/requirements.txt

RUN jupyter lab --generate-config && \
	sed -i -e "s/#c.NotebookApp.ip = 'localhost'/c.NotebookApp.ip = '0.0.0.0'/" /root/.jupyter/jupyter_notebook_config.py && \
	sed -i -e "s/#c.NotebookApp.allow_remote_access = False/c.NotebookApp.allow_remote_access = True/" /root/.jupyter/jupyter_notebook_config.py

EXPOSE 8888
