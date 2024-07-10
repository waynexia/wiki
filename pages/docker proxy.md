- config the docker daemon `dockerd` to use proxy (for operations like `docker pull`)
	- edit `daemon.json` (default path is `/etc/docker/daemon.json`)
	- ```json
	  {
	      "proxies": {
	        "http-proxy": "http://127.0.0.1:7890",
	        "https-proxy": "http://127.0.0.1:7890",
	        "no-proxy": "*.test.example.com,.example.org,127.0.0.0/8"
	      }
	  }
	  ```
	- restart daemon
	- ```shell
	  sudo systemctl restart docker
	  ```
- use host proxy inside docker
	- ```shell
	  export https_proxy=http://172.17.0.1:7890 http_proxy=http://172.17.0.1:7890
	  ```
	- `172.17.0.1` is the special addr for host
	-