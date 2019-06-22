---
title: win10忘记密码登陆
date: 2019-06-21 13:10:36
tags:
---

> 在不输入密码的情况下，修改某一用户的密码为12345678

* 打开电脑发现忘记密码，然后反复重启，并且在出现windows图标的时候强制关机。

* 反复几次后，屏幕会出现 `Preparing Automatic Repair` ，系统自动修复后，点击`Asvanced options`

* 接着点击`Troubleshoot ` 然后`Advanced options ` ，就可以打开命令提示符

* 进入`X:\Windows\System32` 目录，X为系统盘符

* 接着输入以下命令

  ```shell
  copy sethc.exe sethc_bk.exe #备份Windows的粘滞键
  copy /y cmd.exe sethc.exe   #重命名cmd为粘滞键的程序名
  ```

* 重新启动电脑，然后按5次Shift，就可以打开cmd，以SYSTEM（windows中最高权限的）用户运行

* 在cmd中输入以下命令

  ```sh
  net user #查看由哪些用户
  net user [用户名] [新密码] #修改用户名的密码
  ```

* 退出后就可以用新的密码登陆

> ### 思路
>
> 重命名能在登陆界面使用的应用如粘滞键，轻松使用等应用为cmd，就可以以SYSTEM用户使用CMD，然后修改密码，重命名的方式有很多，比如通过U盘启动，重命名。