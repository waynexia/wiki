- for video
	- ```shell
	  ffmpeg -i INPUT.mp4 -vcodec libx265 -crf 23 -b:v 1000k -vf scale=1920:1080 -b:a 128k -acodec aac OUTPUT.mp4
	  ```
	- `-crf 23`: compression
	- `-b:a 128k`: audio sampling
-