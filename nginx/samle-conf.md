# Sample Config

> Simple Config
```nginx
server {
    listen 80;
    location / {
        root /var/www/html;
    }

}

```
### Mount file from Another Address

```nginx
location /robots.txt { alias /mnt/robots/robots.txt; }
```

```nginx
location = /ir/yalda-1400/robots.txt { return 200 "User-agent: *\nDisallow: /\n"; }
```

