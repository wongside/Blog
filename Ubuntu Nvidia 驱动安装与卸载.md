# Ubuntu Nvidia 驱动安装与卸载



### ubuntu选择软件源

* 进入Software & Updates 选择阿里源 



### 安装Nvidia驱动程序

```shell
sudo ubuntu-drivers devices
sudo ubuntu-drivers autoinstall
```



### 卸载所有与Nvidia 相关的驱动

```shell
#delete exe and config file
sudo apt purge nvidia-* 
```

