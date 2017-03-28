# anaconda(python3.5) + MeCab

探してもなかったので、python(anaconda) + MeCab のDockerfileです  
自然言語用処理に  


```
mkdir python-mecab-anaconda
cd !*
wget https://raw.githubusercontent.com/sishinami/docker/master/python-mecab-anaconda/Dockerfile
docker build -t "sishinami/python-mecab-anaconda" .
docker run -it --name conda-mecab -v sishinami/python-mecab-anaconda:latest /bin/bash
```
