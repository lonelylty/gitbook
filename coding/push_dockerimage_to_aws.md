***push docker images to Amazon ECR in Windows***

- install aws CLI 2 

https://docs.aws.amazon.com/zh_cn/cli/latest/userguide/install-cliv2.html

- aws configure

```bash
aws configure
```

remove `.docker/config.json`  line if have  `"credsStore": "wincred"`

- use aws password to login docker

```bash
aws ecr get-login-password --region region | docker login --username AWS --password-stdin accountid.dkr.ecr.region.amazonaws.com
```

```bash
aws ecr create-repository --repository-name name
```

```bash
docker push aws_account_id.dkr.ecr.region.amazonaws.com/imagename
```