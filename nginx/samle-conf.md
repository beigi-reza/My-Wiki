# Sample Config

### Mount file to Another Address or flile

```nginx
location /robots.txt { alias /mnt/robots/robots.txt; }
```

```nginx
location = /ir/yalda-1400/robots.txt { return 200 "User-agent: *\nDisallow: /\n"; }
```
