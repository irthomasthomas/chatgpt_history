## USER
Using temperature=0, Convert this command to a VALID ffplay command. Remove any options that are not available in ffplay:
mpv --hwdec=auto-copy --video-unscaled=yes --script-opts=osc-timems=yes --script-opts=osc-visibility=always "$FILEPATH"

## ASSISTANT


ffplay -hwaccel auto -video_size 0x0 -vf "scale=trunc(iw/2)*2:trunc(ih/2)*2" -fs -noborder -osd_bar -x osc=on:bar_visible=1:bar_w=1:bar_h=0.05:bar_x=10:bar_y=h-h*2/3 -i "$FILEPATH"