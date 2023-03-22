## USER
ffmpeg -i INPUT.mkv -codec copy -bsf:v hevc_metadata=colour_primaries=1:transfer_characteristics=1:matrix_coefficients=1 OUTPUT.mkv

## ASSISTANT
The command you provided is an FFmpeg command that can be used to copy the video and audio streams from an input file, while also modifying the color space metadata of the video stream, and saving the result to an output file.

Here is what each of the parts of the command do:

- `ffmpeg`: This is the command to invoke the FFmpeg tool.
- `-i INPUT.mkv`: This specifies the input file for FFmpeg to read from.
- `-codec copy`: This tells FFmpeg to copy the video and audio streams from the input file, without re-encoding them.
- `-bsf:v hevc_metadata=colour_primaries=1:transfer_characteristics=1:matrix_coefficients=1`: This is a bitstream filter (bsf) that modifies the color space metadata of the video stream. In this case, it sets the color primaries, transfer characteristics, and matrix coefficients to values that correspond to the BT.601 color space, which is commonly used for standard definition (SD) content. The values used are 1, which corresponds to the BT.601 specification.
- `OUTPUT.mkv`: This specifies the output file to write the modified streams to.

So overall, this command is useful when you have a video file that uses a different color space from what you want, and you want to modify the color space metadata without re-encoding the video.

## USER
Change it to bt2020nc

## ASSISTANT
To change the color space metadata to BT.2020 non-constant luminance (BT.2020nc) instead of BT.601, you can modify the `colour_primaries`, `transfer_characteristics`, and `matrix_coefficients` values in the `hevc_metadata` bitstream filter to the following:

```
ffmpeg -i INPUT.mkv -codec copy -bsf:v hevc_metadata=colour_primaries=9:transfer_characteristics=16:matrix_coefficients=9 OUTPUT.mkv
```

Here's what the new values mean:

- `colour_primaries=9`: This sets the color primaries to BT.2020.
- `transfer_characteristics=16`: This sets the transfer characteristics to BT.2020 non-constant luminance (BT.2020nc).
- `matrix_coefficients=9`: This sets the matrix coefficients to BT.2020.

By using these values, FFmpeg will modify the color space metadata of the video stream to BT.2020nc while keeping the video and audio streams intact.