---
title: 零基础Vultr搭建SSR服务器翻墙
author: 阿航
date: 2021-1-17 12:57:00 +0800
categories: [服务器]
tags: VPN

---



1.首先去[Vultr官网](https://www.vultr.com/)注册一个账号；

<img src="https://github.com/lvxinghang/lvxinghang.github.io/raw/main/assets/img/Vultr/image-20210121131001604.png" style="zoom:80%;" />

2.注册成功后登录；登陆后首先点击左侧的Billing充值10美元(最低充值10美元)，选择支付宝支付；

<img src="https://github.com/lvxinghang/lvxinghang.github.io/raw/main/assets/img/Vultr/image-20210121131819354.png" alt="image-20210121131819354" style="zoom:80%;" />

3.付款成功后右上角会显示余额；点+按钮，然后点击`Deploy New Server`去购买服务器；

<img src="https://github.com/lvxinghang/lvxinghang.github.io/raw/main/assets/img/Vultr/image-20210121132418808.png" alt="image-20210121132418808" style="zoom:80%;" />

4.选择`Cloud Compute`；

<img src="https://github.com/lvxinghang/lvxinghang.github.io/raw/main/assets/img/Vultr/image-20210121133544376.png" alt="image-20210121133544376" style="zoom:80%;" />

​	日本的服务器相对较快，由于日本的服务器IP不稳定(容易被墙)且目前只有5美元/月，比较贵所以我们选择美国的服务器`New York`；

<img src="https://github.com/lvxinghang/lvxinghang.github.io/raw/main/assets/img/Vultr/image-20210121133440779.png" alt="image-20210121133440779" style="zoom:80%;" />

​	系统选择`CentOS 7 x64`；

<img src="https://github.com/lvxinghang/lvxinghang.github.io/raw/main/assets/img/Vultr/image-20210121133605251.png" alt="image-20210121133605251" style="zoom:80%;" />

​	价格选`$3.50/mo `(2.5的不支持iPv4网络)；

<img src="https://github.com/lvxinghang/lvxinghang.github.io/raw/main/assets/img/Vultr/image-20210121133625129.png" alt="image-20210121133625129" style="zoom:80%;" />

​	最后把`Enable IPv6`和`Enable Private Networking`勾上；最后购买就行了；

<img src="https://github.com/lvxinghang/lvxinghang.github.io/raw/main/assets/img/Vultr/image-20210121133704832.png" alt="image-20210121133704832" style="zoom:80%;" />

5.购买后会自动安装，安装完成后会看到如下图的效果；然后点`Server Details`看服务器的详细信息；

<img src="https://github.com/lvxinghang/lvxinghang.github.io/raw/main/assets/img/Vultr/image-20210121134629839.png" alt="image-20210121134629839" style="zoom:80%;" />

​	然后拷贝服务器的`IP地址`，`用户名Username`以及`密码Password`留作备用；

<img src="https://github.com/lvxinghang/lvxinghang.github.io/raw/main/assets/img/Vultr/image-20210121134900735.png" alt="image-20210121134900735" style="zoom:80%;" />

​	先ping一下自己的服务器，看是否ping的通；

​	`windows + R`键打开运行窗口，输入`cmd`打开控制台，输入`ping + ip地址`;

​	如果有数据返回说明该ip没有问题；

<img src="https://github.com/lvxinghang/lvxinghang.github.io/raw/main/assets/img/Vultr/image-20210121140141973.png" alt="image-20210121140141973" style="zoom:80%;" />

​	如果ping不通说明分配的ip已经被墙了，此时可以将该服务器删掉再按照上面的操作重新创建一个服务器；

<img src="https://github.com/lvxinghang/lvxinghang.github.io/raw/main/assets/img/Vultr/image-20210121135632423.png" alt="image-20210121135632423" style="zoom:80%;" />

6.接下来检测一下服务器的速度怎么样，[Ping全国检测](http://ping.chinaz.com/)；平均225.8ms，速度一般般，但是相对于美国服务器来说也不错了；追求速度的话可以买日本服务器，但是相对贵一点，美国服务器日常使用够用了；

<img src="https://github.com/lvxinghang/lvxinghang.github.io/raw/main/assets/img/Vultr/image-20210121140549096.png" alt="image-20210121140549096" style="zoom:80%;" />

​	检查SSH是否连接的上(因为现在墙搞了个TCP阻断，有时候国内SSH连接不上)，[检查网址](http://port.ping.pe/)；

​	输入`ip地址:端口号`；

<img src="https://github.com/lvxinghang/lvxinghang.github.io/raw/main/assets/img/Vultr/image-20210121141538458.png" alt="image-20210121141538458" style="zoom:80%;" />

​	如果中国的全是绿的，那就说明没有问题；

<img src="https://github.com/lvxinghang/lvxinghang.github.io/raw/main/assets/img/Vultr/image-20210121141729535.png" alt="image-20210121141729535" style="zoom:80%;" />

如果是红色的，那就连不上SSH，建议换个IP；

7.安装Xshell连接服务器；[Xshell下载地址](https://pan.baidu.com/s/1Oz9kkdWRc9BGwHo3K2Yh_A )；提取码:qwer

<img src="https://github.com/lvxinghang/lvxinghang.github.io/raw/main/assets/img/Vultr/image-20210121143445539.png" alt="image-20210121143445539" style="zoom:80%;" />

​	点击文件-新建；然后在主机栏输入IP地址；

<img src="https://github.com/lvxinghang/lvxinghang.github.io/raw/main/assets/img/Vultr/image-20210121143757981.png" alt="image-20210121143757981" style="zoom:80%;" />

​	然后输入用户名和密码；连接；

<img src="https://github.com/lvxinghang/lvxinghang.github.io/raw/main/assets/img/Vultr/image-20210121144115517.png" alt="image-20210121144115517" style="zoom:80%;" />

8.出现`[root@vultr ~]`说明连接成功了。连接成功后安装SSR；

<img src="https://github.com/lvxinghang/lvxinghang.github.io/raw/main/assets/img/Vultr/image-20210121144500427.png" alt="image-20210121144500427" style="zoom:80%;" />

输入以下命令：

```
wget --no-check-certificate https://freed.ga/github/shadowsocksR.sh; bash shadowsocksR.sh
```

如果提示`wget :command not found`,则执行下面命令，然后再执行上述命令：

```lua
yum install wget -y
```

​	后面会提示输入Shadowsocks的连接密码，如果选择默认密码直接按回车键。也可以自己设置密码，但一定要记住，后面连接时会用到；

​	然后就是设置端口号，直接默认回车就行；后面按照提示操作就行了；

​	安装成功的话会显示配置的信息；把这些信息都复制到记事本保存下来，等会儿连接要用到；

<img src="https://github.com/lvxinghang/lvxinghang.github.io/raw/main/assets/img/Vultr/image-20210121151853810.png" alt="image-20210121151853810" style="zoom: 67%;" />

9.安装BBR加速内核，可以改善服务器的网络传输速度。

​	输入下面的命令：

```
wget --no-check-certificate -O tcp.sh https://github.com/cx9208/Linux-NetSpeed/raw/master/tcp.sh && chmod +x tcp.sh && ./tcp.sh
```

输入相应的数字安装；我们要安装BBRplus版，所以选择2；

<img src="https://github.com/lvxinghang/lvxinghang.github.io/raw/main/assets/img/Vultr/image-20210121152253594.png" alt="image-20210121152253594" style="zoom:80%;" />

安装完后会提示你是否重启，输入y然后回车；

<img src="https://github.com/lvxinghang/lvxinghang.github.io/raw/main/assets/img/Vultr/image-20210121152734088.png" alt="image-20210121152734088" style="zoom:80%;" />

重启后输入数字7开启BBR Plus加速。到这里所有配置已经全部完成了，终于要大功告成了，但是还有最后一步连接。

10.最后通过ShadowsocksR连接；[下载ShadowsocksR](https://tlanyan.me/shadowsockr-shadowsocksr-shadowsocksrr-clients/);

​	下载解压后双击`ShadowsocksR-dotnet2.0.exe`运行;

<img src="https://github.com/lvxinghang/lvxinghang.github.io/raw/main/assets/img/Vultr/image-20210121153525691.png" alt="image-20210121153525691" style="zoom:80%;" />

​	然后选择服务器--编辑服务器；

<img src="https://github.com/lvxinghang/lvxinghang.github.io/raw/main/assets/img/Vultr/image-20210121154114625.png" alt="image-20210121154114625" style="zoom:80%;" />

​	系统代理模式选择PAC模式；说下两者的不同，PAC模式：部分网站走代理，一般是那些被墙的网站；全局模式：所有的网站都通过代理访问；

<img src="https://github.com/lvxinghang/lvxinghang.github.io/raw/main/assets/img/Vultr/image-20210121154358535.png" alt="image-20210121154358535" style="zoom:80%;" />

​	将刚刚保存到记事本的信息各个对应填上去；没有的选项就不填；

<img src="https://github.com/lvxinghang/lvxinghang.github.io/raw/main/assets/img/Vultr/image-20210121154229576.png" alt="image-20210121154229576" style="zoom:80%;" />

​	最后点击确定就可以愉快的访问外网了；

<img src="https://github.com/lvxinghang/lvxinghang.github.io/raw/main/assets/img/Vultr/image-20210121154749166.png" alt="image-20210121154749166" style="zoom: 50%;" />