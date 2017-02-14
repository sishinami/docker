# memo書き 後で docker file へ
docker run --name pio-first -it ubuntu:16.04

wget https://raw.githubusercontent.com/sishinami/vimrc/master/.vimrc ~/


### ref http://predictionio.incubator.apache.org/install/install-linux/

apt-get update
apt-get install -y  default-jdk   wget git vim postgresql-9.5

## インストールマニュアルのダウンロード先が消えているのでミラーへ変更
## ref https://www.apache.org/dyn/closer.cgi/incubator/predictionio/0.10.0-incubating/apache-predictionio-0.10.0-incubating.tar.gz

wget http://ftp.jaist.ac.jp/pub/apache/incubator/predictionio/0.10.0-incubating/apache-predictionio-0.10.0-incubating.tar.gz

tar zxvf apache-predictionio-0.10.0-incubating.tar.gz
cd apache-predictionio-0.10.0-incubating

## make に 時間かかります 30分くらい
./make-distribution.sh


tar zxvf PredictionIO-0.10.0-incubating.tar.gz

## 時間かかるので commit
exit
docker commit  pio-first pio-make-end
docker rm  pio-first
docker run --name pio-make-end -it  pio-make-end /bin/bash


### ref http://predictionio.incubator.apache.org/install/install-linux/


# PredictionIO の 外部ソフトウェア入れ
mkdir PredictionIO-0.10.0-incubating/vendors

#
wget http://d3kbcqa49mib13.cloudfront.net/spark-1.5.1-bin-hadoop2.6.tgz
tar zxvfC spark-1.5.1-bin-hadoop2.6.tgz PredictionIO-0.10.0-incubating/vendors
wget https://download.elasticsearch.org/elasticsearch/elasticsearch/elasticsearch-1.4.4.tar.gz
tar zxvfC elasticsearch-1.4.4.tar.gz PredictionIO-0.10.0-incubating/vendors
wget http://archive.apache.org/dist/hbase/hbase-1.0.0/hbase-1.0.0-bin.tar.gz
tar zxvfC hbase-1.0.0-bin.tar.gz PredictionIO-0.10.0-incubating/vendors

# Postgre 設定
apt-get install postgresql-9.4
/etc/init.d/postgresql start
su - postgres
createdb pio

# PIO_HOME の設定
vi ~/.bashrc
PIO_HOME=/usr/local/src/apache-predictionio-0.10.0-incubating/PredictionIO-0.10.0-incubating/


# この中に ScalaSparkの PATHを入れる必要あり
vi PredictionIO-0.10.0-incubating/conf/pio-env.sh

# ローカルホスト以外に建てるなら こちらを確認
vi PredictionIO-0.10.0-incubating/vendors/elasticsearch-1.4.4/config/elasticsearch.yml

# HBASEの設定で インストール先の名称確認
vi PredictionIO-0.10.0-incubating/vendors/hbase-1.0.0/conf/hbase-site.xml

apt-get install postgresql-9.4
/etc/init.d/postgresql start

# JAVA_HOME設定
export JAVA_HOME=/usr/lib/jvm/java-8-oracle/jre

# PIO開始
 PredictionIO-0.10.0-incubating/bin/pio-start-all



