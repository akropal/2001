# AKROPAL - Фабрика мягких игрушек (2001)

#### 👉 &nbsp; Album Info: [(metadata)](https://akropal.github.io/2001/album/)

```cookie
ffmpeg -i input.mp4 -b:v 1M -b:a 192k output.avi
ffmpeg -i input.aiff -b:a 192k output.mp3
ffmpeg -i input.aiff -b:a 192k output.flac
```

# How to Slice an Audio/Video into Two Parts Using FFmpeg

## Step 1: Check the Duration of the File
Run the following command to determine the total duration of the MKV file:
```bash
ffmpeg -i input.mkv
```
Look for the Duration: field in the output. For example, if the video is 1 hour long (00:60:00), you can use this information to decide the split point.

## Step 2: Slice the Video into Two Parts
Let’s assume you want to split the video at 00:30:00.
Slice Part 1 (Start to 00:30:00)
```
ffmpeg -i input.mkv -t 00:30:00 -c copy part1.mkv
```
Slice Part 2 (00:30:00 to the End)
```
ffmpeg -i input.mkv -ss 00:30:00 -c copy part2.mkv
```
## Explanation of Flags
```
-i input.mkv: Specifies the input MKV file.
-t 00:30:00: Specifies the duration of the first part.
-ss 00:30:00: Specifies the starting time for the second part.
-c copy: Copies the codec stream without re-encoding (faster and avoids quality loss).
```
