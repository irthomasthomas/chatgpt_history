## USER
How to get the run time of a video using bash?

## ASSISTANT
You can use the `ffmpeg` command to get the runtime of a video.

The command is:
```
ffmpeg -i [video file name] 2>&1 | grep "Duration" | awk '{print $2}' | tr -d ,
```

This command first uses `ffmpeg` to get information about the video file, then `grep` filters the output to show only the line that contains the "Duration" information, `awk` is used to extract the duration time, and finally `tr` is used to remove the comma from the output.

You can also use the `mediainfo` tool :
```
mediainfo --Inform='General;%Duration%' [video file name]
```

This will give you the duration of the video in milliseconds.


## USER
Force MPV to use GPU

## ASSISTANT
To force MPV to use the GPU for video playback, you can use the `--hwdec` option with the value `auto-copy`. This tells MPV to use the GPU for decoding and copy the video frame to system memory for display.

The command to use is:
```
mpv --hwdec=auto-copy [video file name]
```

You can also use `--hwdec=auto`, this option will try to use the GPU if it's available, otherwise it will fall back to using software decoding.

```
mpv --hwdec=auto [video file name]
```

It's also important to note that, in some cases, you may also need to configure your GPU drivers, and your system settings to allow MPV to access the GPU,  so depending on your configuration some troubleshooting may be needed.
