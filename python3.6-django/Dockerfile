FROM python:3.6-alpine
LABEL version="1.1"
LABEL description="This is an image of python:3.6-alpine(base) + Django"
RUN pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
RUN pip install django==2.2
RUN pip install mysql-connector
RUN mkdir /data
RUN apk add --no-cache bash \
        bash-doc \
        bash-completion \
        && rm -rf /var/cache/apk/* 
CMD ["/bin/bash"]