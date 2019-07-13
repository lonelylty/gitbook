Let’s Encrypt free Certificate

```
wget https://dl.eff.org/certbot-auto

chmod a+x certbot-auto # executable authority

./certbot-auto certonly  -d "*.xxx.com" -d "xxx.com" --manual --preferred-challenges dns-01  --server https://acme-v02.api.letsencrypt.org/directory

dig  -t txt _acme-challenge.xxx.com @8.8.8.8

openssl x509 -in  /etc/letsencrypt/live/xxx.com/cert.pem -noout -text

certbot-auto renew #Valid for 90 days

```


 —— [origin](https://www.hi-linux.com/posts/6968.html)