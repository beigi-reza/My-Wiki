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
 
 
 > برای دیگر کدها می توان یک متن در نظر گرفت. این متن به عنوان body صفحه نمایش داده خواهد شد.
   ```nginx
   return (1xx | 2xx | 4xx | 5xx) ["text"];
   return 401 "Access denied because token is expired or invalid";
   ```

## Redirect A File

```nginx
if ($request_filename ~ oldfile.html){
rewrite ^ http://example.com/newfile.html? permanent;
}
```
## Redirect Site

```nginx
if ($request_filename ~ /*){
rewrite ^ http://example.com? permanent;
}
```
> Example :
> 
>   176.9.162.107 --> http://example.com
>   
>   176.9.162.107/test.html --> http://example.com

```ngin
if ($request_filename ~ /*){
rewrite ^ http://example.com$request_uri permanent;
}
```
> Example :
> 
>   176.9.162.107 --> http://example.com
>   
>   176.9.162.107/test.html --> http://example.com/test.html




rewrite ^/(.*)$ https://ronixtools.com/ir/ permanent;
