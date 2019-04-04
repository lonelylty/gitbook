(ubuntu)

	apt-get install supervisor
	
	supervisord
	
	ps -ef | grep supervisord
	
	kill -s SIGTERM PID

http://www.cnblogs.com/xishuai/p/ubuntu-install-supervisor.html