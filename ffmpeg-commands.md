# ffmpeg commands

## convert video to mp4

`./ffmpeg -i a.ts -preset slow -c:a aac -codec:v libx264 -profile:v main out.mp4`  

## convert sliced video to mp4

-ss indicates hh:mm:ss of start  
-to indicates hh:mm:ss of end  

`./ffmpeg -i a.ts -ss 00:05:03 -to 01:45:00 -preset slow -crf 18 -profile:a aac_low -b:a 384k -codec:v libx264 -pix_fmt yuv420p -b:v 2500k -minrate 1500k -maxrate 4000k -bufsize 5000k out.mp4`  

## convert DVD to mp4

`./ffmpeg -i concat:VIDEO_TS/VTS_01_1.VOB|VIDEO_TS/VTS_01_2.VOB -preset slow -c:a aac -codec:v libx264 -profile:v main out.mp4`  

## replace audio in a video

`.\ffmpeg.exe -i .\MoP.mp4 -itsoffset 0.7 -i .\MoP.wav -c:v copy -map 0:v:0 -map 1:a:0 new.mp4`  

* -i – stands for input. It’s used to pass an input file to FFmpeg. In our case, we have two files audio.mp3 and file.mkv, so we use two -i.
* -itsoffset – this is an important parameter in this command because it instructs FFmpeg to add a delay of 0.7 seconds to the input streams. 0.7 literally means start the second input after 0.7 seconds of when the first input started.
* -c:a copy – tells FFmpeg for audio codec just copy it. If we want to can specify other codes like -c:a libmp3lame.
* -c:v copy – the same as the last, except for the video codec.
* -map 0:v:0 – instructs FFmpeg to copy/map the video of the first input to the output file.
* -map 1:a:0 – same as above, except it copies the audio of the second input to the output file
