- Install in docker （好像没生效，后来从 AUR 装了）
	- ```shell
	  docker run -d \
	  --name homeassistant \
	  --privileged \
	  --restart=unless-stopped \
	  -e TZ="Asia/Shanghai" \
	  -v ~/.dotfiles/homeassistant:/config \
	  --network=host \
	  ghcr.io/home-assistant/home-assistant:stable
	  ```
- AUR 安装 [`homeassistant-supervised`](https://aur.archlinux.org/packages/homeassistant-supervised/)
- 初始化的时候下 Python 依赖很慢，可以给 PIP 加上镜像源参数 `--index-url https://mirrors.sustech.edu.cn/pypi/web/simple`
- 安装 HACS https://hacs.xyz/docs/setup/download/ ，默认 config 目录是 `/usr/share/hassio/homeassistant`
- 安装米家的集成插件 https://github.com/al-one/hass-xiaomi-miot/tree/master
- 网络问题可以用 https://github.com/ryanh7/hacs-proxy （HACS 右上角添加 custom repo，下载完之后在添加 integration 的地方写配置）
-
- 配置 Dashboard
	- 参考 https://github.com/matt8707/hass-config/blob/master/INSTALL.md
	- Awesome List https://github.com/frenck/awesome-home-assistant#dashboards
	- Mushroom Card https://github.com/piitaya/lovelace-mushroom （开关类的卡片比较好）
	- https://github.com/kalkih/mini-graph-card
-
	- Prometheus integration https://www.home-assistant.io/integrations/prometheus/
		- 要直接改配置文件，然后重启就行了
		-