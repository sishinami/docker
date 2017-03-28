# anaconda(python3.5) + Mecab
mkdir python-mecab-anaconda
cd !*
wget https://raw.githubusercontent.com/sishinami/docker/master/python-mecab-anaconda/Dockerfile
docker build -t "sishinami/python-mecab-anaconda" .
docker run -it --name conda-mecab -v sishinami/python-mecab-anaconda:latest /bin/bash

