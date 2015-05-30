## Nginx Optimization.

1. Worker Processes.
2. Worker Connections.
3. Timeouts.
4. Buffer Size.
5. Caching Static Contents.
6. Disable Access Logs.


##### 1. Worker Processes.

> This depends on number of cores of the server. Use grep command to cpuinfo to get the number of cores.

```
grep processor /proc/cpuinfo | wc -l

```

> Set the value of worker_processes to the value of the cores.


##### 2. Worker Connections.

> Number of simultaneous conncetions a worker handles. check our core's limitations by issuing a ulimit command.

```
ulimit -n
```

> Update the following values in the nginx.conf

```
sudo nano /etc/nginx/nginx.conf
```

```
worker_processes 1;
worker_connections 1024;
```

##### 3. Timeouts.

> **client_body_timeout** and **client_header_timeout** directives are responsible for the time a server will wait for a client body or client header to be sent after request. If neither a body or header is sent, the server will issue a 408 error or Request time out.

> The **keepalive_timeout** assigns the timeout for keep-alive connections with the client. Nginx will close connections with the client after this period of time.

> **send_timeout** if client stop responding, free up memory, shut down the connection.

```
client_body_timeout 15;
client_header_timeout 15;
keepalive_timeout 60;
send_timeout 20;
```

##### 4. Buffer Size.

> **client_body_buffer_size** This handles the client buffer size, meaning any POST actions sent to Nginx. POST actions are typically form submissions.

> **client_header_buffer_size** it handles the client header size. For all intents and purposes, 1K is usually a decent size for this directive.

> **client_max_body_size** The maximum allowed size for a client request. If the maximum size is exceeded, then Nginx will spit out a 413 error or Request Entity Too Large.

> **large_client_header_buffers** The maximum number and size of buffers for large client headers.

```
client_body_buffer_size 10K;
client_header_buffer_size 1k;
client_max_body_size 10m;
large_client_header_buffers 2 1k;
```

##### 5. Caching Static Contents.

```
location ~* .(jpg|jpeg|png|gif|ico|css|js)$ {
expires 7d;
}
```


##### 6. Disable Access Logs.

```
access_log off;
```

#### For Security Reasons 

> Disable server tokens.

```
server_tokens off;
```
