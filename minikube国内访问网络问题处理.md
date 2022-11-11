# [minikube国内访问网络问题处理](https://www.cnblogs.com/wswind/p/14420803.html)

minikube所需的镜像在拉取时，要求网络能够访问`k8s.gcr.io`。而此地址属于著名的404公司，在国内是无法访问的。
新版本的minikube已经在命令行中，充分考虑到了国内用户的网络情况，并提供了相应的命令行参数。不过网上大多博客的说明没有更新，在处理镜像拉取时，会让初学者浪费大量的时间处理网络问题。
具体说明可以通过`minikube start --help`命令查看，节选如下：

```bash
--image-mirror-country='': Country code of the image mirror to be used. Leave empty to use the global one. For
Chinese mainland users, set it to cn.
--image-repository='': Alternative image repository to pull docker images from. This can be used when you have
limited access to gcr.io. Set it to "auto" to let minikube decide one for you. For Chinese mainland users, you may use
local gcr.io mirrors such as registry.cn-hangzhou.aliyuncs.com/google_containers
```

上面的帮助说明中，已经把国内用户需要填什么都说清楚了，可以说很良心了。在国内不借助代理的情况下，minikube正确的打开方式应该是：

```bash
minikube start --driver=docker --image-mirror-country=cn
```

作者：王帅

出处：https://www.cnblogs.com/wswind/p/14420803.html

版权：本作品采用「[知识共享署名-非商业性使用-相同方式共享 4.0 国际许可协议](http://creativecommons.org/licenses/by-nc-sa/4.0/)」许可协议进行许可。



转载需注明本文出处：https://www.cnblogs.com/wswind/p/14420803.html