- for video
	- ```shell
	  ffmpeg -i INPUT.mp4 -vcodec libx265 -crf 23 -b:v 1000k -vf scale=1920:1080 -b:a 128k -acodec aac OUTPUT.mp4
	  ```
	- `-crf 23`: compression (work with `-vcodec libx265` and similar soft encoder)
	- `-b:a 128k`: audio sampling
	- `-r 30` frame rate
	-
- hardware accelerate
	- macOS
		- `-hwaccel videotoolbox` before `-i` to accelerate decoder
		- `-c:v hevc_videotoolbox -q:v 65` (0~100 for worse ~ best) to use hardware encoder (with worse quality than libx265)
	-