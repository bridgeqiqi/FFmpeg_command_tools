# FFmpeg_command_tools
Frequently-used commands of ffmpeg


### Export the audio from the video
```bash
ffmpeg -i <video_path.mp4> <output_audio_path.wav>
```

### Concatenate two videos in the spatial level
```bash
ffmpeg -i <video_path1.mp4> -i <video_path2.mp4> -filter_complex "[0:v]pad=iw*2:ih*1[a];[a][1:v]overlay=w" <output_video_path.mp4>
```

### Concatenate multiple videos in spatial level
- concatenate in vertical level
```bash
ffmpeg -i <video1.mp4> -i <video2.mp4> ... -i <videoN.mp4> -filter_complex vstack=inputs=<N> <output.mp4>
```
- concatenate in horizontal level
```bash
ffmpeg -i <video1.mp4> -i <video2.mp4> ... -i <videoN.mp4> -filter_complex hstack=inputs=<N> <output.mp4>
```

### Crop the video with customized size
```bash
ffmpeg -i <input_video.mp4> -filter:v "crop=out_w:out_h:x:y" <output_video.mp4>
```
- **out_w** is the desired **width** of the output video
- **out_h** is the desired **height** of the output video
- **x** is the **horizontal** position in the input video
- **y** is the **vertical** position in the input video

