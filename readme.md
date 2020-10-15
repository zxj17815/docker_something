### Docker images dockerfile
#### Ubuntu-python-django文件夹
以ubuntu镜像为基础，修改了apt源为清华源，安装了python3.6、pip3（v19）、django2.2及MySQL-clinet相关配置  
version=1.1 改为PyMySQL进行连接，但是因为django2.2版本不支持<1.3.13的mysqlclient库，所以兼容设置，修改django的init文件：  
```python
# django 项目管理文件夹的__init__.py
import pymysql 
pymysql.version_info = (1, 3, 13, "final", 0) 
pymysql.install_as_MySQLdb()
```   

#### python3.6-django文件夹
以python:3.6-alpine为基础  
安装了Django + DRF + uWSGI + MySql连接  
version=1.1 改为PyMySQL进行连接，但是因为django2.2版本不支持<1.3.13的mysqlclient库，所以兼容设置，修改django的init文件：  
```python
# django 项目管理文件夹的__init__.py
import pymysql 
pymysql.version_info = (1, 3, 13, "final", 0) 
pymysql.install_as_MySQLdb()
```     
  
Docker pull:
```
docker push zxj17815/alpine-django2.2:tagname
```
已经安装的pip库：  
```
certifi                       2019.11.28
chardet                       3.0.4
coreapi                       2.3.3
coreschema                    0.0.4
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
Markdown                      3.1.1
MarkupSafe                    1.1.1
pip                           19.3.1
PyJWT                         1.7.1
PyMySQL                       0.9.3
pytz                          2019.3
requests                      2.22.0
setuptools                    42.0.2
sqlparse                      0.3.0
uritemplate                   3.0.1
urllib3                       1.25.7
uWSGI                         2.0.18
wheel                         0.33.6
```
*其中pycryptodome比较特殊，由于创建镜像时在windows下使用；在Linux下可能需要替换为crypto*  
   
**tips：运行时请暴露端口和共享本地项目文件夹如下：**
```shell
docker run --name django2.2 -i -t -p 8899:8899 -v D:/work:/data zxj17815/alpine-django2.2:v2
```
#### nginx
文件夹内为使用docker的nginx配置文件

#### Mysql
Mysql5.7的docker镜像和简单的mysalAdmin管理站点，Docker Compose 编写  
在文件同级目录内使用Compose直接启动
```shell
docker-compose up
```

#### Redis
Redis的docker镜像和简单的redisAdmin管理站点，Docker Compose 编写  
在文件同级目录内使用Compose直接启动
```shell
docker-compose up
```