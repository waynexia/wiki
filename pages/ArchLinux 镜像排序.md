- 需要`pacman-contrib`包里面的`rankmirrors`
- 命令
  ```bash
  sudo bash -c "rankmirrors -n 6 /etc/pacman.d/mirrorlist.backup > /etc/pacman.d/mirrorlist"
  ```
- 源文件在 https://gitlab.archlinux.org/pacman/pacman-contrib/-/blob/master/src/rankmirrors.sh.in
- 跑之前最好删掉一些地球对面的肯定用不上的镜像源，不然脚本要跑很久
- 一些参数
	- `-n NUM` 输出结果个数，感觉没什么意义，不过上面的命令里面设到了6
	- `--max-time`每个镜像源的超时时间，默认是10,可能配了之后跑奇怪的源会快一点
-