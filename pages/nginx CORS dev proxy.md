- default nginx config is `/etc/nginx/nginx.conf`
- ```conf
  http {
      include       mime.types;
      default_type  application/octet-stream;
  
      sendfile        on;
  
      keepalive_timeout  65;
  
      server {
          listen       8000;
          server_name  localhost;
  
          location / {
              proxy_pass http://127.0.0.1:4000;
              proxy_set_header Host $host;
              proxy_set_header X-Real-IP $remote_addr;
              proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
              proxy_set_header X-Forwarded-Proto $scheme;
  
              # CORS headers
              add_header 'Access-Control-Allow-Origin' '*' always;  # Allow all origins
              add_header 'Access-Control-Allow-Methods' 'GET, POST, OPTIONS' always;  # Allowed methods
              add_header 'Access-Control-Allow-Headers' 'Content-Type, Authorization' always;  # Allowed headers
  
          	# Handle preflight requests
              if ($request_method = 'OPTIONS') {
              add_header 'Access-Control-Allow-Origin' '*';
                  add_header 'Access-Control-Allow-Methods' 'GET, POST, OPTIONS, DELETE, PUT';
                  add_header 'Access-Control-Allow-Headers' 'Content-Type, Authorization, X-Requested-With, access-control-allow-headers,access-control-allow-methods,access-control-allow-origin,content-type';
                  add_header 'Access-Control-Max-Age' 86400;  # Cache preflight response for 1 day
                  add_header 'Content-Length' 0;
                  return 204;  # No content response
              }
          }
      }
  }
  ```