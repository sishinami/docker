FROM ubuntu:16.04
MAINTAINER sishinami

RUN apt-get update && apt-get -y upgrade
RUN apt-get -y install build-essential
RUN apt-get -y install git \
                       vim \
                       curl \
                       wget\
                       zlib1g-dev \
                       libssl-dev \
                       libreadline-dev \
                       libyaml-dev \
                       libxml2-dev \
                       libxslt-dev \
                       libncurses5-dev \
                       libncursesw5-dev \
                       libmecab-dev \
                       mecab \
                       mecab-ipadic \
                       mecab-ipadic-utf8 \
                       mecab-utils
                       

# pyenv のインストール
RUN git clone git://github.com/yyuu/pyenv.git /root/.pyenv
RUN git clone https://github.com/yyuu/pyenv-pip-rehash.git /root/.pyenv/plugins/pyenv-pip-rehash
ENV PYENV_ROOT /root/.pyenv
ENV PATH $PYENV_ROOT/bin:$PATH
RUN echo 'eval "$(pyenv init -)"' >> .bashrc

# anaconda のインストール
ENV ANACONDA_VER 4.3.1
RUN pyenv install anaconda3-$ANACONDA_VER
RUN pyenv global anaconda3-$ANACONDA_VER
ENV PATH $PYENV_ROOT/versions/anaconda3-$ANACONDA_VER/bin:$PATH

# ライブラリのアップデート
RUN conda update -y conda
RUN pip install --upgrade pip
RUN pip install mecab-python3
