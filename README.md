## Charles设置

#### 一、添加SSL证书

![1](https://github.com/lifirepot/Nos-s-Android7.0-Charles/blob/main/Screencap/CharlesCert/1.png)

![2](https://github.com/lifirepot/Nos-s-Android7.0-Charles/blob/main/Screencap/CharlesCert/2.png)

![3](https://github.com/lifirepot/Nos-s-Android7.0-Charles/blob/main/Screencap/CharlesCert/3.png)

![4](https://github.com/lifirepot/Nos-s-Android7.0-Charles/blob/main/Screencap/CharlesCert/4.png)

![5](https://github.com/lifirepot/Nos-s-Android7.0-Charles/blob/main/Screencap/CharlesCert/5.png)

#### 二、代理设置

![1](https://github.com/lifirepot/Nos-s-Android7.0-Charles/blob/main/Screencap/ProxySettings/1.png)

![2](https://github.com/lifirepot/Nos-s-Android7.0-Charles/blob/main/Screencap/ProxySettings/2.png)

#### 三、SSL代理设置

![1](https://github.com/lifirepot/Nos-s-Android7.0-Charles/blob/main/Screencap/SSLProsey/1.png)

![2](https://github.com/lifirepot/Nos-s-Android7.0-Charles/blob/main/Screencap/SSLProsey/2.png)

## 夜神模拟器设置

#### 一、推送证书到根目录

##### 	1、导出证书

![1](https://github.com/lifirepot/Nos-s-Android7.0-Charles/blob/main/Screencap/NoxCert/1.png)

![2](https://github.com/lifirepot/Nos-s-Android7.0-Charles/blob/main/Screencap/NoxCert/2.png)

##### 	2、转换证书格式

![1](https://github.com/lifirepot/Nos-s-Android7.0-Charles/blob/main/Screencap/ProxySettings/4.png)

```
openssl x509 -inform PEM -subject_hash_old -in noxzhengsuh.pem //查看证书哈希值
ren noxzhengsuh.pem 证书哈希值.0 //将.pem的证书转成.0的文件格式
```

![2](https://github.com/lifirepot/Nos-s-Android7.0-Charles/blob/main/Screencap/ProxySettings/5.png)

##### 3、使用模拟器ADB

###### 需要进入\Nox\bin路径的cmd窗口

找到桌面上的夜神模拟器快捷启动图表，鼠标右键--打开文件所在的位置，就会进入*\Nox\bin，在文件地址栏输入cmd回车打开窗口

![3](https://github.com/lifirepot/Nos-s-Android7.0-Charles/blob/main/Screencap/NoxCert/6.png)

![4](https://github.com/lifirepot/Nos-s-Android7.0-Charles/blob/main/Screencap/NoxCert/7.png)

![5](https://github.com/lifirepot/Nos-s-Android7.0-Charles/blob/main/Screencap/NoxCert/8.png)

###### 连接设备

```
nox_adb.exe devices
D:\Nox\bin>nox_adb.exe devinox_adb.exe devicesces
List of devices attached
127.0.0.1:****** device
```

![6](https://github.com/lifirepot/Nos-s-Android7.0-Charles/blob/main/Screencap/NoxCert/9.png)

###### 开通写入权限

```
cd /system/etc/security //进入目标目录
chmod 777 cacerts //赋予777权限
mount -o remount,rw /system //如果提示 Read-only file system,使用这一行代码，将系统文件夹挂载为可读写。然后再用chmod赋予777权限
exit //退出shell  如果使用su提权，输入两次exit
```

###### 推送证书到目录

```
adb push C:\*\zhengshu\2c44aefb.0 /system/etc/security/cacerts 
//将证书文件目录修改成自己的
```

![7](https://github.com/lifirepot/Nos-s-Android7.0-Charles/blob/main/Screencap/NoxCert/10.png)

#### 二、模拟器网络设置

![1](https://github.com/lifirepot/Nos-s-Android7.0-Charles/blob/main/Screencap/NoxCert/11.png)

模拟器-设置-网络-高级-代理[手动]

模拟器-设置-网络-高级-代理服务器主机[主机IP]

```
ipconfig //查询主机ip
//win+r，输入cmd回车打开窗口
```

模拟器-设置-网络-高级-代理服务器端口[端口号]

​	端口号默认8888

​	在Charles-Proxy Settings-Http Proxy中查询

## 参考链接

完成以上步骤就可以对我们模拟器进行抓包啦！！！撒花！！！！！！！

以下是参考链接，链接中的大大如认为被侵权可以联系小短手删除，在此致谢！！！

以下排名不分先后顺序

#### [1]https://www.52pojie.cn/thread-1679128-1-1.html

原文章提供了多种Android7.0以后系统不在信任用户的证书的解决办法，致谢Anekys大大！！！！

#### [2]https://zhuanlan.zhihu.com/p/565327085

原文章提供了大致思路和解决办法，致谢奇奇大大！！！！

#### [2]https://support.yeshen.com/zh-CN/qt/ml

夜神模拟器官方ADB使用文档页面
