# 树莓派安装 Ubuntu Server 20 及网络配置

### 安装

第一种方法，推荐使用该方法。直接使用树莓派官网提供的Raspberry Pi Imager安装。

第二种方法，到树莓派官网下载系统镜像，然后使用Win32 Disk Imager安装。

两种方法的操作比较简单，选择好系统和磁盘直接点击下一步即可。

* 树莓派系统和工具 [下载页面](https://www.raspberrypi.org/downloads/)

*  Win32 Disk Imager [下载页面](https://sourceforge.net/projects/win32diskimager/)

###### Ubuntu Server 20 默认用户名和密码

* 用户名:`ubuntu`
* 密码: `ubuntu`

###  网络配置

在没有显示器的情况下，树莓派可以通过网线连接，然后在路由器上查看树莓派的IP，然后使用ssh连接到树莓派。

如果没有网线可以在SD卡中配置WIFI名和密码，通过WIFI连接。

#### WIFI配置方法

打开SD卡根目录下的network-config文件，

在文件最后添加

```yaml
wifis:
  wlan0:
    dhcp4: true
    optional: true
    access-points:
      "WIFI名称":
        password: "WIFI密码"
```

待树莓派启动后，等待一两分钟，然后**重启树莓派**就能连接到WIFI了。

**该配置只在树莓派安装系统后第一次修改有效**



#### 查看树莓派IP地址

* 可以直接登录路由器查看

* 或者使用`arp`命令查看

  ```shell
  arp -a | findstr b8-27-eb # Windows 树莓派3
  arp -a | findstr dc-a6-32 # Windows 树莓派4
  arp -na | grep -i "b8:27:eb" # Linux 树莓派3
  arp -na | grep -i "dc:a6:32" # Linux 树莓派4
  ```

* 进入系统后, 查看树莓派IP地址

```shell
ip a
```

#### 进入系统后连接WIFI

第一步, 查看无线网卡名称

```shell
ls /sys/class/net
```

第二步, 修改网络配置

```shell
sudo nano /etc/netplan/50-cloud-init.yaml
#将下面的内容添加到文件末尾
    wifis:
        wlan0:
            optional: true
            access-points:
                "SSID-NAME-HERE":
                    password: "PASSWORD-HERE"
            dhcp4: true
```

第三步, 应用网络配置

```shell
sudo netplan apply
```

#### 配置静态IP

第一步, 禁用cloud-init自动IP

```shell
sudo nano /etc/cloud/cloud.cfg.d/subiquity-disable-cloudinit-networking.cfg
# 在其后添加
network: {config: disabled}
```

第二步, 修改配置,如下所示

```shell
    wifis:
        wlan0:
            addresses: [192.168.1.200/24]
            gateway4: 192.168.1.1
            nameservers:
                addresses: [114.114.114.114, 114.114.115.115]
            access-points:
                "wifi name":
                    password: "password"
            optional: true
```

第三步, 应用更改

```shell
sudo netplan apply
```

#### 参考链接

安装系统: https://ubuntu.com/tutorials/how-to-install-ubuntu-on-your-raspberry-pi#4-boot-ubuntu-server

连接WIFI: https://linuxconfig.org/ubuntu-20-04-connect-to-wifi-from-command-line

配置静态IP: https://www.linuxtechi.com/assign-static-ip-address-ubuntu-20-04-lts/