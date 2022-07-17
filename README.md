# supervisored_lightbus

## 项目截图
![screenshot](/screenshot.png)

## 目的

主要是备份一下lightbus相对应的supervisored的配置文件等等

	[program:lightbus]
	command=lightbus run
	directory=/var/services/homes/lemonhall/lightbus
	redirect_stderr=true
	stdout_logfile=/tmp/
	stderr_logfile=/tmp/
	environment=LIGHTBUS_CONFIG="/var/services/homes/lemonhall/lightbus/lightbus.yaml"

核心其实就是这一段配置

# supervisored_lightbus

* source lightbus/bin/activate

在虚拟环境下启动 supervisord
* (lightbus) lemonhall@nas16t:~/lightbus$ supervisord -c supervisord.conf


* environment=LIGHTBUS_CONFIG="/var/services/homes/lemonhall/lightbus/lightbus.yaml"
现在看下来这个参数没有用
必须在启动钱配置好

* 结果发现，这个也不是最关键的，最关键的竟然是 source ~/.bashrc


	export PATH=/var/services/homes/lemonhall/.local/bin:$PATH
	export LIGHTBUS_CONFIG="/var/services/homes/lemonhall/lightbus/lightbus.yaml"


* 那我们把env改一下试试


environment=PATH="/var/services/homes/lemonhall/.local/bin:$PATH",LIGHTBUS_CONFIG="/var/services/homes/lemonhall/lightbus/lightbus.yaml"


* 前台运行来测试一下

supervisord -n -c supervisord.conf

成功了

* 接下来测一下python的缓冲区的buffred的问题
