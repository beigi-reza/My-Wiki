# NGINX Rewrite Rules


```nginx
server {
    listen 80;
    listen 443 ssl;
    server_name www.old-name.com;
    return 301 $scheme://www.new-name.com$request_uri;
}
```
**$scheme** : return is the protocol (http or https)

**$request_uri** : return is the full URI including arguments

> در کدهای سری 3xx آدرس url به صورت کامل بازنویسی می شود
 ```nginx
 return (301 | 302 | 303 | 307) url;
 ```
 
 
 > برای دیگر کدها می توان یک متن در نظر گرفت.
   ```nginx
   return (1xx | 2xx | 4xx | 5xx) ["text"];
   ```
