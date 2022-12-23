- set http proxy
	- ```shell
	  git config --global http.proxy "http://127.0.0.1:7890"
	  git config --global https.proxy "http://127.0.0.1:7890"
	  ```
- unset http proxy
	- ```shell
	  git config --global --unset http.proxy
	  git config --global --unset https.proxy
	  ```
- set ssh proxy
	- ```shell
	  vim ~/.ssh/config
	  ```
	- ```ssh-config
	  Host github.com
	     HostName github.com
	     User git
	     ProxyCommand /usr/bin/nc -v -x 127.0.0.1:7890 %h %p
	  ```
	- Notice the `nc` here is not `GNU netcat`, its manual looks like this
		- ```
		  usage: nc [-46AacCDdEFhklMnOortUuvz] [-K tc] [-b boundif] [-i interval] [-p source_port]
		  	  [--apple-recv-anyif] [--apple-awdl-unres]
		  	  [--apple-boundif ifbound]
		  	  [--apple-no-cellular] [--apple-no-expensive]
		  	  [--apple-no-flowadv] [--apple-tcp-timeout conntimo]
		  	  [--apple-tcp-keepalive keepidle] [--apple-tcp-keepintvl keepintvl]
		  	  [--apple-tcp-keepcnt keepcnt] [--apple-tclass tclass]
		  	  [--tcp-adp-rtimo num_probes] [--apple-initcoproc-allow]
		  	  [--apple-tcp-adp-wtimo num_probes]
		  	  [--setsockopt-later] [--apple-no-connectx]
		  	  [--apple-delegate-pid pid] [--apple-delegate-uuid uuid]
		  	  [--apple-kao] [--apple-ext-bk-idle]
		  	  [--apple-netsvctype svc] [---apple-nowakefromsleep]
		  	  [--apple-notify-ack] [--apple-sockev]
		  	  [--apple-tos tos] [--apple-tos-cmsg]
		  	  [-s source_ip_address] [-w timeout] [-X proxy_version]
		  	  [-x proxy_address[:port]] [hostname] [port[s]]
		  ```