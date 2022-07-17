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
