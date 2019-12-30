### Docker images dockerfile
#### Ubuntu-python-django文件夹
以ubuntu镜像为基础，修改了apt源为清华源，安装了python3.6、pip3（v19）、django2.2及MySQL-clinet相关配置

#### python3.6-django文件夹
以python:3.6-alpine为基础  
安装了Django + DRF + MySql关联  
已经安装的pip库：  
```
aliyun-python-sdk-core        2.13.13
aliyun-python-sdk-core-v3     2.13.11
aliyun-python-sdk-kms         2.8.0
certifi                       2019.11.28
chardet                       3.0.4
coreapi                       2.3.3
coreschema                    0.0.4
crcmod                        1.7
defusedxml                    0.6.0
Django                        2.2
django-crontab                0.7.1
django-filter                 2.2.0
djangorestframework           3.11.0
djangorestframework-simplejwt 4.4.0
djangorestframework-xml       1.4.0
drf-writable-nested           0.5.4
idna                          2.8
itypes                        1.1.0
Jinja2                        2.10.3
jmespath                      0.9.4
Markdown                      3.1.1
MarkupSafe                    1.1.1
mysqlclient                   1.4.6
oss2                          2.9.1
pip                           19.3.1
pycryptodome                  3.9.4
PyJWT                         1.7.1
pytz                          2019.3
requests                      2.22.0
setuptools                    42.0.2
sqlparse                      0.3.0
uritemplate                   3.0.1
urllib3                       1.25.7
uWSGI                         2.0.18
wheel                         0.33.6
```
**其中pycryptodome比较特殊，在windows下使用；在Linux下可能需要替换为crypto**