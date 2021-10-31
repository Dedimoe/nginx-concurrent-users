# nginx: display active connection per user / concurrent users

1. add this code in /etc/nginx/conf.d/default
```
location /nginx_concurrent {
   stub_status on;
   access_log   off;
   # only allow access from 127.0.0.1
   allow 127.0.0.1;
   deny all;
}
```

2. restart nginx
```
sudo systemctl restart nginx
```

3. get info concurrent users 
```
curl 127.0.0.1/nginx_concurrent
```

4. output like this
```
Active connections: 93 
server accepts handled requests
 12827 12828 265482 
Reading: 0 Writing: 131 Waiting: 88 
```

Note:
a. 93 = number of all open connections<br>
b. 12827 = accepted connections<br>
c. 12828 = handled connections<br>
d. 265482 = handles requests
