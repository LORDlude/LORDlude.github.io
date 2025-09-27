## ffmpeg拼接视频

**key1：**

```bash
setp1：编辑一个1.txt内容为（注意必须是单引号）：
		file '1.mp4'
		file '2.mp4'
		file '3.mp4'
```

```bash
setp2：ffmpeg -f concat -safe 0 -i 1.txt -c copy -y output.mp4
```

**key2：**

```bash
ffmpeg -i concat:"1.mpg|2.mpg|3.mpg" -c copy output.mp4
```

对于 MPEG 格式的视频，可以直接连接，尺寸要一致

## ffmpeg合并音视频

```bash
ffmpeg -i video.mp4 -i audio.mp3 -c:v copy -c:a aac -strict experimental output.mp4

-i video.mp4：指定视频文件路径。
-i audio.mp3：指定音频文件路径。
-c:v copy：将视频流复制到输出文件中，不进行重新编码。
-c:a aac：使用AAC编码音频流。
-strict experimental：启用实验性AAC编码器。
output.mp4：指定输出文件路径和名称。
```

## ffmpeg提取视频流

提取H265

```bash
-x265-params "bframes=0" 不带B帧，比如在不支持解码B帧的时候
ffmpeg -i input.mp4 -vcodec libx265 output.265
ffmpeg -i test.mp4  -vcodec copy -f hevc test.h265
```

提取H264

```bash
ffmpeg -i video.mp4 video.264
ffmpeg -i input.mp4 -vcodec h264 output.264
ffmpeg -i input.mp4 -vcodec libx264 output.264
ffmpeg -i file.mp4 -an -vcodec copy -bsf:v h264_mp4toannexb output.264
ffmpeg -i input.mp4 -codec copy -bsf: h264_mp4toannexb -f h264 output.264
ffmpeg -i video.mp4 -codec copy -f h264 video.h264
```

## 环境变量去重清理工具

**key1：**

`EnvMan.exe`

**key2：**

`WindowsPathEditor`
