---
{"dg-publish":true,"permalink":"/nodes/test-second/","tags":"gardenEntry"}
---

 一、MySQL安装文件夹的data文件夹不完整或者被移动了

1.如果是Data文件夹里面的文件不完整，那么就先清空原来的Data文件夹，然后输入mysqld --initialize初始化Data，如果可能有报错，但是没反应可以到Data文件夹里的.err文件查看原因；

或者可以输入mysqld --initialize --console，在控制台就能看到报错信息。

2、如果是data文件夹的位置发生了变化，就要根据文件夹的新目录修改my.ini文件中basedir=?

和datadir=?这两个文件的存储位置了，另外，如果MySQL的文件夹也发生位置变化，比如加装了移动硬盘，重新分区；环境变量也需要跟着修改配置。

  

  

![](https://pic2.zhimg.com/80/v2-6848f89f5202a8011d0415321c4efce1_1440w.webp)

  

以上两个情况都初始化一下（mysqld --initialize）会比较保险。

安装服务的话输入 mysqld --install 服务名 如：mysqld --install MySQL80

删除服务的话输入 sc delete 服务名 如：sc delete MySQL80

总结可能会用到的命令：

mysqld --initialized -insecure：初始化MySQL，并且默认密码为空；  
mysqld --initialized --console：初始化MySQL；  
mysqld --install：安装MySQL服务；  
mysqld -remove：删除MySQL服务；  
mysql -u 用户名 -p：登录MySQL；  
alter user 'root'@'localhost'identified by '密码';：修改管理员用户的密码；

## 二、MySQL服务的可执行文件路径不正确

右键我的电脑—>管理—>服务—>找到自己mysql的服务—>右键属性打开

  

  

![](https://pic4.zhimg.com/80/v2-40630266d2e4f73ab8e41d12e9010333_1440w.webp)

  

  

如果路径有 -default的需要删掉

当前可执行文件的路径为：

```text
"F:\Program Files\mysql-8.0.30-winx64\bin\mysqld" -defaultPath="F:\Program Files\mysql-8.0.30-winx64\bin\mysqld" MySQL80
```

修改步骤：

  

  

![](https://pic3.zhimg.com/80/v2-f5b70c5e9823c3a946c136963fd1065a_1440w.webp)

  

按照路径找到自己的mysql服务注册表

  

  

![](https://pic1.zhimg.com/80/v2-7720155e0d3870431bf6a33f7e1666c0_1440w.webp)

  

修改ImagePath为