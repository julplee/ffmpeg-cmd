# ffmpeg commands

## convert video to mp4

`./ffmpeg -i a.ts -preset slow -c:a aac -codec:v libx264 -profile:v main out.mp4`

## convert sliced video to mp4

-ss indicates hh:mm:ss of start
-to indicates hh:mm:ss of end 

`./ffmpeg -i a.ts -ss 00:05:03 -to 01:45:00 -preset slow -crf 18 -profile:a aac_low -b:a 384k -codec:v libx264 -pix_fmt yuv420p -b:v 2500k -minrate 1500k -maxrate 4000k -bufsize 5000k out.mp4`

## convert DVD to mp4

`./ffmpeg -i concat:VIDEO_TS/VTS_01_1.VOB|VIDEO_TS/VTS_01_2.VOB -preset slow -c:a aac -codec:v libx264 -profile:v main out.mp4`
