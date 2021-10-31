# nginx: display active connection per user / concurrent users

add this code in /etc/nginx/conf.d/default
```
location /nginx_concurrent {
   stub_status on;
   access_log   off;
   # only allow access from 127.0.0.1
   allow 127.0.0.1;
   deny all;
}
```

restart nginx
```
sudo systemctl restart nginx
```

get info concurrent users 
```
curl 127.0.0.1/nginx_concurrent
```

output like this
```
Active connections: 93 
server accepts handled requests
 12827 12828 265482 
Reading: 0 Writing: 131 Waiting: 88 
```

Note:
1. 93 = number of all open connections
2. 12827 = accepted connections
3. 12828 = handled connections
4. 265482 = handles requests
