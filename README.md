# h5ai
树莓派(arm架构）中运行h5ai,基于corfr / h5ai修改


# Pi-DOCKER-H5AI

## 使用基本的Nginx配置文件运行



```
$ sudo docker run -d \
  -p 80:80 \
  -v $PWD:/var/www \
  -v $PWD/nginx_config_examples/basic_h5ai.nginx.conf:/etc/nginx/sites-enabled/h5.conf \
  stivw/armv7-h5ai
```

## HTTPS and PASSWORD

1.创建一个密码文件。 [使用nginx设置http身份验证](https://www.digitalocean.com/community/tutorials/how-to-set-up-http-authentication-with-nginx-on-ubuntu-12-10)
2.创建nginx conf文件或查看`nginx_config_examples /`中的文件。
3.生成或使用证书和密钥文件。 [如何在Nginx上创建ssl证书](https://www.digitalocean.com/community/tutorials/how-to-create-an-ssl-certificate-on-nginx-for-ubuntu-14-04)

```
$ sudo docker run -d \
  -p 80:80 \
  -p 443:443 \
  -v $PWD/nginx_config_examples/h5ai.nginx.conf:/etc/nginx/sites-enabled/h5.conf \
  -v $PWD/htpasswd:/mnt/config/htpasswd:ro \
  -v $PWD/ssl:/etc/nginx/ssl:ro \
  -v /home/marcel/media:/var/www \
  stivw/armv7-h5ai
```

参考：
CoRfr/docker-h5ai
https://github.com/CoRfr/docker-h5ai

（个人使用）
