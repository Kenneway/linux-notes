按变量的生存周期来划分，Linux变量可分为两类，它们的修改方法如下：
（1）永久的：需要修改配置文件，变量永久生效。
    常见的配置文件包括：
    （1-1）/etc/profile：对所有用户生效；此文件为系统的每个用户设置环境信息,当用户第一次登录时,该文件被执行；并从/etc/profile.d目录的配置文件中搜集shell的设置
        例如：编辑/etc/profile文件，添加CLASSPATH变量
        # vi /etc/profile
        添加一行：
	export CLASSPATH=./JAVA_HOME/lib;$JAVA_HOME/jre/lib
	修改后需要执行重新登录才能生效，也可以执行命令source /etc/profile来生效

    （1-2）/etc/bashrc：对所有用户生效；为每一个运行bash shell的用户执行此文件.当bash shell被打开时,该文件被读取
        编辑方法如上，不再赘述

    （1-3）~/.bash_profile：仅会对当前用户有效；每个用户都可使用该文件输入专用于自己使用的shell信息,当用户登录时,该文件仅仅执行一次
        例如：编辑guok用户目录(/home/guok)下的.bash_profile
        $ vi /home/guok/.bash.profile
        添加如下内容：
        export CLASSPATH=./JAVA_HOME/lib;$JAVA_HOME/jre/lib
	修改后需要执行重新登录才能生效，也可以执行命令source /etc/profile来生效

    （1-4）~/.bashrc：仅会对当前用户有效；该文件包含专用于你的bash shell的bash信息,当登录时以及每次打开新的shell时,该该文件被读取
        编辑方法如上，不再赘述

        另外，~/.bashrc等中设定的变量(局部)只能继承/etc/profile中的变量,他们是"父子"关系

    综述，对上述文件修改，添加你需要的变量，在启动一个shell（终端，terminal）时，你所定义的变量均会生效的。

（2）临时的：使用export命令声明即可，变量只在当前的shell(BASH)或其子shell(BASH)下是有效的,在关闭shell后失效，再打开新shell时就没有这个变量，需要使用的话还需要重新定义
	在shell的命令行下直接使用[export 变量名=变量值] 定义变量

环境变量的查看
（1）使用echo命令查看单个环境变量。例如：
echo $PATH
（2）使用env查看所有环境变量。例如：
env
（3）使用set查看所有本地定义的环境变量。例如：
set
另外，unset可以删除指定的环境变量。

常用的环境变量
PATH 决定了shell将到哪些目录中寻找命令或程序
HOME 当前用户主目录
HISTSIZE　历史记录数
LOGNAME 当前用户的登录名
HOSTNAME　指主机的名称
SHELL 当前用户Shell类型
LANGUGE 　语言相关的环境变量，多语言可以修改此环境变量
MAIL　当前用户的邮件存放目录
PS1　基本提示符，对于root用户是#，对于普通用户是$
