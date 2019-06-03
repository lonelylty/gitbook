ubuntu

```
apt-get install python-pip python-m2crypto
pip install shadowsocks
sudo vi /etc/shadowsocks.json
{
    "server":"0.0.0.0",
    "server_port":8388,
    "local_address": "127.0.0.1",
    "local_port":1080,
    "password":"password",
    "timeout":300,
    "method":"aes-256-cfb",
    "fast_open": false,
    "workers": 1
}

ssserver -c /etc/shadowsocks.json

nohup ssserver -c /etc/shadowsocks.json /usr/local/bin/ssserver_log 2>&1&
```