## 创建项目
`
django-admin startproject 项目名称   // 创建一个名为项目名称的项目
`
&emsp;&emsp;执行完上述命令后，当前文件夹下会多出一个名为项目名称的文件夹，文件夹中有一个同名文件夹（以下简称同名二级文件夹）和一个manage.py文件
同名二级文件夹下有这样一些内容:
_init_.py
asgi.py
settings.py
urls.py
wsgi.py
<font color='red'>注意：自动创建的文件没有views.py,因此在根路由文件urls.py下使用
`
from . import views
`
可能会出现报错
如需使用需自行手动创建</font>
### settings.py中的一些个设置
允许内网访问：`ALLOWED_HOSTS = ['*',]`
更改语言与时区
```
LANGUAGE_CODE = 'zh-Hans' `
TIME_ZONE = 'Asia/Shanghai'
```

## 启动项目
`
   python manage.py runserver 0.0.0.0:8000
`
&emsp;&emsp;0.0.0.0为本机IP，8000为端口号，<font color='red'>注意一定要在项目文件夹目录下运行该命令。</font>该命令运行后，即可通过浏览器访问该项目。访问地址127.0.0.1:8000/目录
## 终止项目
&emsp;&emsp;只需在命令行下输入ctrl+c(win)或ctrl+z(macOS)

## 应用
### 应用和项目的关系
&emsp;&emsp; 一般而言，一个应用对应项目中的一个功能，故一个项目一般有很多个应用
### 应用的创建
1. 项目目录下命令行输入`python manage.py startapp XXXX`
2. 在项目总settings.py的INSTALLED_APPS中加入一项`'项目名称'`
3. 如有子路由文件urls.py（需自行创建），需要在根路由urls.py下的urlpatterns下加入
   `path('应用路径/',include('应用名称.urls')),`

## import相关
| 序号  | 函数| 依赖的包| 
| --- | :--- | :---: | 
| 1  | url| `django.conf.urls.url` | 
| 2 | path| `django.urls.path` |
| 3 | re_path| `django.urls.re_path` |
| 4 | httpResponse | `django.http.httpresponse` |
| 5 | include| `django.urls.include`

## 杂项
1. path函数中的变量，其调用的函数可调用
2. 调用当前目录的views中的函数(urls.py)
```
urlpatterns=[
    url(r'^$',views.process),
]
```

