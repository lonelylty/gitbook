sudo docker run --detach \ 
    --hostname gitlab.example.com \
    --publish 443:443 \
    --publish 1226:80 \
    --publish 23:22 \
    --name gitlab \
    --restart always \
    --volume /srv/gitlab/config:/etc/gitlab \
    --volume /srv/gitlab/logs:/var/log/gitlab \
    --volume /srv/gitlab/data:/var/opt/gitlab \
    gitlab/gitlab-ce:latest

--detach   设置容器后台运行
--hostname 设置容器的hostname
--publish  暴露 https、http和ssh端口
--name     容器名称
--restart always  每次启动容器就重启GitLab
--volume 设置GitLab数据挂载点
/srv/gitlab/data    应用程序数据
/srv/gitlab/logs    GitLab的log
/srv/gitlab/config  GitLab的配置文件


如果按照上面做还是出现Permission denied错误，那么可以检查一下selinux状态，开启的情况下会导致一些服务安装、使用不成功
setenforce 0

docker run --detach \
或
sudo docker run -i \ 

    --hostname localhost \
    --env GITLAB_OMNIBUS_CONFIG="external_url 'http://localhost'; gitlab_rails['gitlab_shell_ssh_portv']='10022';" \
    --publish 10443:443 \
    --publish 10080:80 \
    --publish 10022:22 \
    --publish 18080:8080 \
    -u 0 \
    --name gitlab \
    --restart always \
    --volume /srv/gitlab/config:/etc/gitlab \
    --volume /srv/gitlab/logs:/var/log/gitlab \
    --volume /srv/gitlab/data:/var/opt/gitlab \
    --volume /srv/gitlab/logs/reconfigure:/var/log/gitlab/reconfigure \
    gitlab/gitlab-ce:latest update-permissions


sudo docker run -i \
    --hostname localhost \
    --env GITLAB_OMNIBUS_CONFIG="external_url 'http://localhost';" \
    --publish 10443:443 \
    --publish 10080:80 \
    --publish 10022:22 \
    --publish 18080:8080 \
    -u 0 \
    --name gitlab \
    --restart always \
    --volume /srv/gitlab/config:/etc/gitlab \
    --volume /srv/gitlab/logs:/var/log/gitlab \
    --volume /srv/gitlab/data:/var/opt/gitlab \
    --volume /srv/gitlab/logs/reconfigure:/var/log/gitlab/reconfigure \
    gitlab/gitlab-ce:latest

netstat -ntlp

docker exec -it gitlab /bin/bash

vi /etc/gitlab/gitlab.rb

unicorn['worker_processes'] = 3
unicorn['worker_timeout'] = 60
unicorn['port'] = 8888
gitlab_workhorse['auth_backend'] = "http://localhost:8888"
gitlab_rails['webhook_timeout'] = 90
gitlab_rails['git_timeout']=90

gitlab-ctl reconfigure
gitlab-ctl restart
gitlab-ctl status

http://www.adocker.cn/archives/2777

交互方式
docker run -it --name 容器名称 镜像 /bin/bash

守护进程
docker run -d  --name 容器名称 镜像

/etc/docker/daemon.json

"registry-mirrors": ["https://docker.mirrors.ustc.edu.cn"]

docker save gitlab/gitlab-ce:latest > /usr/gitlab_docker.tar.gz
docker load < /usr/gitlab_docker.tar.gz