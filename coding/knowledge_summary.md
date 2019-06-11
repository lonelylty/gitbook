依赖注入
缓存机制


Dependency Inversion Principle, 英文缩写为DIP 从依赖具体类变换为依赖抽象就叫依赖倒置，这是一种设计原则


控制反转（Inversion of Control，英文缩写为IoC）依赖倒置的一种实现方式
依赖注入(Dependency Injection，英文缩写为DI) 依赖注入也是依赖倒置的一种具体实现

IOC框架包括了控制反转和依赖注入功能

微服务

一种架构模式，提倡将单一应用程序划分成一组小的服务，服务之间互相协调、互相配合，为用户提供最终价值。每个服务运行在其独立的进程中，服务与服务间采用轻量级的通信机制互相沟通（RESTful API）。每个服务都围绕着具体的业务进行构建，并且能够被独立地部署到生产环境、类生产环境等。另外，应尽量避免统一的、集中式的服管理机制，对具体的一个服务而言，应根据业务上下文，选择合适的语言、工具对其进行构建
```
cat /proc/cpuinfo
cat /proc/version
cat /proc/meminfo
df -lh
cat /proc/scsi/scsi
lsb_release -a
```
Kestrel 是跨平台的HTTP server 基于libuv（一个跨平台的异步I/O library）

Httpsys 是基于Windows内核驱动程序Http.Sys的HTTP server。Http.Sys是成熟的技术，可以防范多种攻击，并提供全功能Web服务器的鲁棒性，安全性和可扩展性。IIS本身作为HTTP侦听器运行在Http.Sys之上

nugnet恢复引用失效时,可在程序包管理控制台输入:

dotnet restore 即可

.net core mysql
Install-Package MySql.Data -Pre

sudo dpkg -i xxx.deb
pydoc modules
help("modules")

配置文件一般为/etc/init.d/cron

启动：sudo /etc/init.d/cron start

关闭：sudo /etc/init.d/cron stop

重启：sudo /etc/init.d/cron restart

重新载入配置：sudo /etc/init.d/cron reload

可以用ps aux | grep cron命令查看cron是否已启动

 m h  dom mon dow   command
date -R


for /f "skip=9 tokens=1,2 delims=:" %i in ('netsh wlan show profiles') do  @echo %j | findstr -i -v echo | netsh wlan show profiles %j key=clear


* pip update

python -m pip install -U pip
