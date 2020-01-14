FROM ubuntu:latest
MAINTAINER iceiceice <hades922@outlook.com>
LABEL version="1.1"
LABEL description="This is an image of Ubuntu(deb=mirrors.tuna.tsinghua.edu.cn) + Django (DRF,MySql(pymysql))"
RUN mv /etc/apt/sources.list /etc/apt/sources.list.bak
RUN echo "deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic main restricted universe multiverse" >>/etc/apt/sources.list
RUN echo "deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-updates main restricted universe multiverse" >>/etc/apt/sources.list
RUN echo "deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-backports main restricted universe multiverse" >>/etc/apt/sources.list
RUN echo "deb http://mirrors.tuna.tsinghua.edu.cn/ubuntu/ bionic-security main restricted universe multiverse" >>/etc/apt/sources.list
RUN apt-get update
RUN apt-get install python3.6 -y
RUN apt-get install python3-pip -y
RUN pip3 install -i https://pypi.tuna.tsinghua.edu.cn/simple pip -U
RUN rm -rf /usr/bin/pip3
COPY pip3 /usr/bin/pip3
RUN pip3 config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
RUN pip3 install django==2.2
RUN pip3 install django-crontab
RUN pip3 install djangorestframework
RUN pip3 install markdown
RUN pip3 install django-filter
RUN pip3 install pymysql
RUN pip3 install djangorestframework_simplejwt
RUN pip3 install requests
RUN pip3 install djangorestframework-xml
RUN pip3 install drf-writable-nested
RUN pip3 install coreapi