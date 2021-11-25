# shell学习

* shell比较快
* Linux上都有，换平台也能使用
* 系统默认的都是bash

### bash的功能

兼容于sh，并在此基础上做了加强

* 历史记录，在`~/.bash_history`,只记录了上一次登录的命令，当前的缓存在内存中
* 命令补全，使用tab键补全，可以安装`bash-completion`可以进行参数和选项的补全
* 命令别名，`alias`可以查看bash环境中的别名
* 任务管理，控制程序的前台后台执行
* 程序化脚本，即shell脚本
* 通配符，`? * `等等

### type查看是否为bash中的命令

```shell
type cd # 查看cd命令是否是bash内置的
```

type可以用于查找命令

* `\`让命令可以在下一行继续输入
* `ctrl + u` ` ctrl + k ` `ctrl + a` ` ctrl + e`分别为向前删除，向后删除，移动到最前面，移动到最后

### 变量

* 环境变量通常是大写字母，例如 PATH， MAIL ， HOME
* echo $variable 可以输出变量的值，例如，echo $PATH
* 更好的使用变量的方式是，echo ${variable}
* myname=side 设置变量，变量的规则见书上319页
* export 可以将自己定义的变量变成环境变量
* unset 可以取消变量 
* cd /lib/modules/$(uname -r)/kernel 进入到目前内核模块的目录
* 每个Linux都能够有多个内核
* `反单引号里的命令会被先执行，其输出作为命令的输入 ``

