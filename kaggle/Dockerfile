FROM nvidia/cuda:10.0-cudnn7-devel-ubuntu18.04

# base
RUN apt update && apt install -y --no-install-recommends \
    vim \
    tmux \ 
    unzip \
    git

WORKDIR /workspace 
RUN chmod -R a+w /workspace

# Python
RUN apt install -y python3-pip
RUN pip3 install pip --upgrade 

COPY ./requirements.txt ./host/requirements.txt
RUN pip install setuptools
RUN pip install -r ./host/requirements.txt

# Jupyter lab
RUN jupyter lab --generate-config && \
    sed -i -e "s/#c.NotebookApp.ip = 'localhost'/c.NotebookApp.ip = '0.0.0.0'/" /root/.jupyter/jupyter_notebook_config.py && \
    sed -i -e "s/#c.NotebookApp.allow_remote_access = False/c.NotebookApp.allow_remote_access = True/" /root/.jupyter/jupyter_notebook_config.py

EXPOSE 8888

## Jupyter lab extension
RUN apt install -y npm
RUN pip install nodejs
RUN jupyter labextension install jupyterlab_vim

# kaggle
COPY ./kaggle.json /root/.kaggle/
RUN chmod 600 /root/.kaggle/kaggle.json

# Download/Unzip data
RUN kaggle competitions download -c understanding_cloud_organization -p ./dataset
RUN unzip ./dataset/train_images.zip -d ./dataset/train_images
RUN unzip ./dataset/test_images.zip -d ./dataset/test_images
RUN unzip ./dataset/train.csv.zip -d ./dataset/
