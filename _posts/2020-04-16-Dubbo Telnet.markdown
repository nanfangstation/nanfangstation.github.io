---
layout:     post
title:      "Dubbo Telnet"
subtitle:   "昨夜西风凋碧树，独上高楼，望尽天涯路。"
date:       2020-04-16
author:     "Lydia"
header-img: "img/post-bg-dubbo.jpeg"
catalog: true
tags:
    - Dubbo
---

## 背景

开发经常需要测试dubbo服务接口，除了dubbo admin控制台的入口外，我们还可以通过telnet命令来实现。

>  从 `2.0.5` 版本开始，dubbo 开始支持通过 telnet 命令来进行服务治理。

```
telnet localhost 20880
Trying localhost...
Connected to localhost.
Escape character is '^]'.
```

## 命令

### ls

```
ls
com.xxx.service.CarAuditService
com.xxx.service.CarStageService
com.xxx.service.CarService
com.xxx.service.AssetCarService
```

### cd

```
cd com.xxx.service.CarService
Used the com.xxx.service.CarService as default.
You can cancel default service by command: cd /
```

### invoke

```
dubbo>invoke listCar({"class":"com.xxx.entity.CarPageReq","includeCarIds":[132586]})
Use default service com.xxx.service.CarService.
{"code":10000,"data":{"items":[{"color":"紫色","colorId":10,"status":3}],"pageNum":1,"pageSize":1,"total":1},"msg":"Success","traceId":"18f94fb98cea4b22aaf7b0e44bccca40"}
elapsed: 23 ms.
```

### ps

- `ps` 显示服务端口列表
```
ps 
20880
```

- `ps -l` 显示服务地址列表
```
dubbo>ps -l
dubbo://IP1:20880
```

- `ps 20880` 显示端口上的连接信息
```
/IP1:57550
/IP2:53550
/IP3:33910
/IP4:37654
```

- `ps -l 20880`
```  
dubbo>ps -l 20880
/IP1:57550 -> /IP5:20880
/IP2:53550 -> /IP5:20880
/IP3:33910 -> /IP5:20880
/IP4:37654 -> /IP5:20880
```

### pwd

显示当前缺省服务

```
dubbo>pwd
/
```

### trace

1. `trace XxxService` 跟踪 1 次服务任意方法的调用情况
2. `trace XxxService xxxMethod` 跟踪 1 次服务方法的调用情况

### count

1. `count XxxService` 统计 1 次服务任意方法的调用情况
2. `count XxxService xxxMethod` 统计 1 次服务方法的调用情况