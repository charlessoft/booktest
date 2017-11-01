# docker基础镜像修整

## 原版

`python:2.7-alpine`

只要出现要build的包就无法正常运行。


## 整合build 相关包的镜像

`rcarmo/alpine-python:2.7`

安装都成功，进入container 也能看到numpy 安装成功，但是还是会出现

ImportError: Missing required dependencies ['numpy']

# 其他注意事项

## pip cache

需要使用参数
pip install --no-cache-dir --disable-pip-version-check