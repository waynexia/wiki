- with `tcpdump`
	- ```shell
	  sudo tcpdump -n -s 0 -A -i eth0 'tcp dst port 80 and (((ip[2:2] - ((ip[0]&0xf)<<2)) - ((tcp[12]&0xf0)>>2)) != 0)'
	  ```
		- `-n` 表示不尝试查找主机，端口号等名称。
		- `-s 0` 表示拍摄整个包-没有任何长度限制。
		- `-A` 表示将包内容以ASCII格式输出，包括请求头和正文数据。
		- `-i eth0` 表示你正在监听的网络接口。请注意，这取决于你的系统配置，你的网络接口名称可能不同，使用 `ifconfig` 可以查看具体的网络接口名称。
		- `tcp dst port 80 and (((ip[2:2] - ((ip[0]&0xf)<<2)) - ((tcp[12]&0xf0)>>2)) != 0)` 是一个过滤条件，寻找目标端口（dst port）是80的 TCP 包，并且包中的数据部分不为空。
- with `tshark`
	- ```shell
	  sudo tshark -V -i eth0 tcp port 80
	  ```
-