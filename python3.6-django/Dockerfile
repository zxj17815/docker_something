FROM python:3.6-alpine
MAINTAINER iceiceice <hades922@outlook.com>
LABEL version="1.0"
LABEL description="This is an image of python:3.6-alpine(base) + Django + DRF + MySql"
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.tuna.tsinghua.edu.cn/g' /etc/apk/repositories
RUN pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
RUN apk add --no-cache mariadb-connector-c-dev pcre-dev;\
    apk add --no-cache --virtual .build-deps \
        build-base \
        mariadb-dev gcc make libc-dev linux-headers;\
    pip install mysqlclient;\
    pip install pycryptodome;\
    pip install uwsgi;\
    apk del .build-deps
RUN pip install django==2.2
RUN pip install django-crontab
RUN pip install djangorestframework
RUN pip install markdown
RUN pip install django-filter
RUN pip install djangorestframework_simplejwt
RUN pip install requests
RUN pip install djangorestframework-xml
RUN pip install drf-writable-nested
RUN pip install coreapi
RUN pip install oss2
RUN apk add --no-cache bash \
        bash-doc \
        bash-completion \
        && rm -rf /var/cache/apk/* 
CMD ["/bin/bash"]